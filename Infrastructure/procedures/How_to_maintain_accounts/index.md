---
title: How to maintain accounts
uri: 'WPD:Infrastructure/procedures/How to maintain accounts'

---
Here are a few commands we can do to check what’s happening in the accounts system

## Database queries

### Is a user activated?

     SELECT HEX(uid),HEX(emailCode),email,fullName FROM accounts WHERE emailVerified = 0 AND email LIKE '%@w3.org%';

### Force activation

This can be done by going to a specific link;

     SELECT CONCAT('https://accounts.webplatform.org/verify_email?uid=', HEX(uid), '&code=',HEX(emailCode)) FROM accounts WHERE  emailVerified = 0 AND email LIKE '%@w3.org%';
