# Genrationing Password Hash in [nodejs](https://nodejs.org/en/)



**Password encryption** is a major thing as we need it sometimes while working with authentication.
It might be possible that your database may get hacked but what if when the passwords are not.
Simply you have stored them in different format instead of storing them as plain text which quite
risky.

So while working with [nodejs](https://nodejs.org/en/) you can do such a thing using bcryptjs. It is easy to use it. In order to
use it simply generate a password salt first and generate the hash using the salt you have created.
Refer below code for more explanation.

### Install the [bcryptjs](https://www.npmjs.com/package/bcryptjs) package
```sh
$ npm install --save bcryptjs
```

Import this package into your file where you want to use it.
```js
var bcrypt = require('bcryptjs')
```

 First, generate the salt
```js
bcrypt.genSalt(12, function(err, salt) {
	//salt goes here.
})
```
 Add the salt to your password
```js
//Number 12 is number of iteration to genrate salt.(default it is 10)
bcrypt.genSalt(12, function(err, salt) {
  bcrypt.hash(password, salt, function(err, hash) {
	  // Now the hash is available to store.
	  console.log("hash is -   " + hash);
  });
```


Final working code is below.

```js
	var password = 'MyUserPassword';
	var number = 12 // Number of iteration to genrate salt.
	bcrypt.genSalt(number , function(err, salt) {
	  bcrypt.hash(password, salt, function(err, hash) {
		  // Store hash in your password DB.
		  console.log("hash is -   " + hash);
	  });
	});
```
