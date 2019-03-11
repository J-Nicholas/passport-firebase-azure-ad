
# Microsoft Azure Active Directory Passport.js Plug-In

---
    
![npm version](https://img.shields.io/npm/v/passport-firebase-azure-ad.svg?style=for-the-badge&logo=appveyor&color=green)


_passport-azure-ad_ is a collection of [Passport](http://passportjs.org/) Strategies 
to help you integrate with Azure Active Directory. It includes OpenID Connect, 
WS-Federation, and SAML-P authentication and authorization. These providers let you 
integrate your Node app with Microsoft Azure AD so you can use its many features, 
including web single sign-on (WebSSO), Endpoint Protection with OAuth, and JWT token 
issuance and validation.

## 1. Installation

    $ npm install passport-firebase-azure-ad

## 2. Usage

This package is intended to allow users to authenticate and authorise Microsoft home, school and work accounts while working in a firebase environment. This is achieved by altering Microsoft's original passport-azure-ad npm package to store the time and encrypted cookie in the "\__session" cookie with the "azure" prefix, current time and date + encrypted cookie as the value. In firebase, cookies can only be titled "\__session" and anything else is removed.  Authenticating and authorising should be unchanged but if you are using firebase, you __must__ have useCookieInsteadOFSession and cookie encrypted keys set in your OIDCStrategy.

```javascript 
passport.use(new OIDCStrategy({
...
...
    useCookieInsteadOfSession: true,
    cookieEncryptionKeys: [
            {key: "12345678901234567890123456789012", iv: "012345678901"}
        ]
...
});
```
Note: __key__ must be a string of length 32 (32 bytes) and __iv__ must be a string of length 12 (12 bytes).

## 3. Full Documentation
Original passport-azure-ad module can be found on github: [Here](https://github.com/AzureAD/passport-azure-ad).
Please refer to this for full documentation on how to utilise passport-azure-ad. Almost everything should apply to this module as I have only made a small modification. 

## 4. Note
I am stil a student and don't have a lot of experience yet and there may be a better way to authorise/authenticate microsoft azure users using vanilla passport-azure-ad and firebase but I struggled to find a solution until I made this. Feel free to contact me about any tips you might have for me or any problems you face using this package. Thank you.
