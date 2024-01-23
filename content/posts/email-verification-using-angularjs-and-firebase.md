---
title: "Email verification using AngularJS and Firebase"
date: 2014-05-31T22:23:00Z
subtitle: ""
slug: ""
tags:
  [
    "account activation",
    "featured",
    "english",
    "email verification",
    "cloud",
    "angularjs",
    "web",
  ]
aliases: ["/2014/05/email-verification-using-angularjs-firebase.html"]
type: post
---

![firebase logo](/img/83576v9-max-450x450.png)

I believe many of us who only using Firebase as data backend and its hosting for serving client code would eventually find out that it lacks email verification feature upon account registration or account activation. Actually we can use server code to provide email verification and account activation using firebase token.We can store a token in the database, send the same token via e-mail to the client, and ask them to click a link in the e-mail that passes the token back to a page which then marks their e-mail as verified. And for account activation, we can define user data with a property “active” (initially set to false), send token to their email, and ask them to click a link with token appended that passes the token back to a page, and finally compare the tokens, if they’re same, set active to true.

But there is an alternative that does not require server code. We can use a sendPasswordResetEmail() method of FirebaseSimpleLogin of Firebase Javascript SDK or $sendPasswordResetEmail method of $firebaseSimpleLogin service of Angularfire library.

I have developed a method for email verification and integrated into Angularfire seed of Firebase team. You can find my seed at [angularjsfire-with-reg-confirmation](https://github.com/ciptohadi79/angularjsfire-with-reg-confirmation). It is AngularJS seed with Firebase backend and a feature for account registration confirmation via email. It is a clone of [AngularFire Seed](https://github.com/firebase/angularFire-seed) with additional feature above and also login feature vial social login ie login with Facebook, Twitter, and Google.

The account registration differs significantly from the original seed. We can register for an account just by supplying an email and then we’ll get a confirmation email about our temporary random password. The password is recommended to be changed to a memorable one and at the same time it must also be strong and secure.

How do I approach email verification? Here what I do:

1. First, on account registration, user is asked to provide his/her email address
2. Create an account for that user
3. If account creation is success, I create profile for him/her and send a confirmation email about temporary password. And user is asked update his/her account detail, especially the password.

Files that I have modified are:

1. index.html: upgrade firebase-simple-login.js and angularfire.js
2. router.js: change login to auth
3. controllers.js: change loginCtrl to authCtrl, and change the logic of createAccount method
4. service.login.js: add sendPasswordResetEmail method using $sendPasswordResetEmail method of $firebaseSimpleLogin service of Angularfire library

Hopefully it help others

Cheers
