=webplatform.org bugs=

If you find an issue related to the content of the site (e.g. an article is incorrect or missing), you have a few choices:

* '''Fix it yourself'''. [[WPD:Getting Started|Learn how]] to contribute.
* '''Add a comment'''. To add a comment, hover your mouse over the relevant section heading and click '''Add Comment'''.
* '''Add a flag'''. Flags visually mark pages that are incomplete or incorrect. See [[WPD:Flags|Using Flags]] for details.
* '''File a bug'''. Only if it is not something that is covered by the three options above (see below for how).

If you find an issue related to the functionality of the site, file a bug (see below). The main groups of bugs we are seeing are as follows:

* '''Site functionality bugs''' (for example, browser errors or UI issues).
* '''Issues related to entire groups of pages''' not behaving or displaying correctly.

==How to file bugs==

To file a bug against WPD, or any other part of webplatform.org, you need to use the W3C's [http://www.w3.org/Bugs/ Bugzilla bug tracking system].

* First of all, you need to make sure you have an account. If not, go to the [https://www.w3.org/Bugs/Public/createaccount.cgi Create a new Bugzilla account] page, and follow the steps there.
* Next, make sure you are logged into the site.
* Make sure that this bug hasn't been filed already — go to the [https://www.w3.org/Bugs/Public/query.cgi Bugzilla search] page, set the product to '''webplatform.org''', and enter keywords to search for the bug. 
* Now go to the [https://www.w3.org/Bugs/Public/enter_bug.cgi Enter bug] page.
* Choose the [https://www.w3.org/Bugs/Public/enter_bug.cgi?product=webplatform.org webplatform.org] link.
* There are a number of options here, for example you can set a severity rating, add an attachment, or specify the hardware/OS you are using; the most important ones for you to fill in are as follows:
** '''Summary''': Enter a descriptive but short summary, to summarize what the problem is.
** '''Description''': Enter a more detailed description of exactly what the problem is. If there are multiple steps needed to reproduce the bug, say what they are, in a numbered list. It is also helpful to describe what the expected/desired behavior is, and what the actual behavior is, if appropriate.
** '''Component''': Select which component of the site this bug applies to. You can choose:
*** '''Comment Extension''' — if the problem relates specifically to the coments extension we've got installed to allow you to comment on specific parts of pages.
*** '''content''' — if the problem is specifically to do with the content of any pages, rather than it's look and implementation.
*** '''default''' — choose this if you are not sure where else to place your bug.
*** '''info architecture''' — if the problem is specific to the organization of pages on the site. Maybe some pages are placed wrongly, or you feel that it is harder to find something than it should be?
*** '''infrastructure''' — if you have a problem with some facet of how the site is implemented. Database bugs, JavaScript bugs, other development problems?
*** '''skin''' — if the problem concerns the visual design; the look and feel of the site.
* Finally, press the '''Submit bug''' button at the bottom of the page.

You should receive notifications via e-mail when your bug is actioned, commented, etc.