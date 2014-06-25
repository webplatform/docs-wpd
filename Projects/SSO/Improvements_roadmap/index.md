= Improvements roadmap =

The steps described in [[WPD:Projects/SSO/How we implemented it]] can be improved, this page describes some proposals.

== Recovering session data ==

This change proposal is about making sure the exchanged information is encoded in ways that only the intended audience can use.

=== Problem in the original steps ===

ANYBODY who got access to a sessionToken, could become that user. And that is as long as the victim keeps his session opened on the accounts server. Because there is no way to validate if the request is made from the legitimate user.

This security issue is no different than any web application that doesn’t use SSL. After all, the way a web server has to differentiate a visitor from another is basically a set of cookies, one of them serves as a session token.

One obvious solution is to have SSL across the whole site, but its not always possible. We cannot force the user to go back and forth from SSL if they are OK without it. But we cannot leave such powerful data without encoding it either.

=== Proposed solution steps ===

To solve the possible exploit, let’s revisit the original steps described in [[WPD:Projects/SSO/Login Workflows#Starting a session by communicating with accounts server]]. Differences are shown in '''bold''', removed steps has been <s>crossed out</s>.

* In the accounts server:
** '''Encode the sessionToken in some way with a shared secret key (e.g. using HMAC256)'''
** '''Save the encoded sessionToken in a new variable "<tt>encodedPacket</tt>" in SessionStorage'''
** Accept framing (i.e. accept to create iframe from other domain names that we control) through appropriate CSP policies.
** <s>Create an event handler that replies with a JSON object that reads the current sessionToken in SessionStorage (e.g. <tt>{sessionToken: "e73f75c00115f45416b121e274fd77b60376ce4084267ed76ce3ec7c0a9f4f1f"}</tt>)</s>
** '''Create an event handler that replies with a JSON object that reads the current <tt>encodedPacket</tt> value in SessionStorage (e.g. <tt>{encodedPacket: {packet: "b113a9666bc7b51625e997c3e73d4696aab7be61e0573e3041da488fad8cd2b1", digest: "hmac256"}}</tt>)''' 
* Through JavaScript, on a web application relying on the SSO (details in [[WPD:Projects/SSO/How we implemented it#JavaScript shared module: Detect and start automatically a session]]):
** Check if web application has a session locally, if not, continue
** Create a communication channel as an hidden iframe, if the accounts server doesn’t forbid due to CSP policy, continue.
** Use <tt>postMessage</tt> to communicate through the iframe opened to the accounts server
** Handle response from <tt>postMessage</tt>, use the returned data (i.e. <s><tt>sessionToken</tt></s> '''<tt>encodedPacket</tt> JSON object''' value) into a POST body member called "recoveryPayload"
** Make a <tt>POST</tt> request to the current web app callback (e.g. <tt>/wiki/Special:AccountsHandler/callback</tt>) with "recoveryPayload"
* In the backend code (detailled in (details in [[WPD:Projects/SSO/How we implemented it#Initialize local web application session]])):
** Accept <tt>POST</tt> requests with a "recoveryPayload" parameter<s>, make sure it’s 64 hexadecimal characters</s>
** <s>Rename the "recoveryPayload" as "sessionToken"</s>
** '''Unpack the "recoveryPayload" data using the shared secret key. If the payload makes any sense, has a member called "sessionToken" of 64 hexadecimal characters, continue'''
** Make an off-the-band call over SSL to the profile server
** Read a JSON object with the user data
** Create a session without further validation

'''Advantages''':
* Only the encoded packet will be communicated across frames
* If a relying party doesn’t use SSL, the data will need to be decoded to be useful
* Whether or not the session had a "man in the middle", the attacker will
** still need to get the secret key to unpack the encoded "recoveryPayload" contents.
** not get a chance to get anything useful from the JavaScript call to the call back GET parameters
* Each backend application will have to unpack the recoveryPayload, validate if it makes sense BEFORE communicating with the profile.accounts.webplatform.org endpoint.

'''What we could add on top of it''':
* Sign the response from the profile server using JWT format, see [https://github.com/mozilla/jwcrypto jwcrypto]
* Validate on the backend whether the response from the profile server is valid
* Have SSL everywhere