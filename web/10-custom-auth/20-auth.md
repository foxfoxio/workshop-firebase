
### Hello cloud function
```shell
firebase init functions
```
### Add the Firebase Admin SDK to Your Server
> https://firebase.google.com/docs/admin/setup?authuser=0
```shell
npm install firebase-admin --save
```
### Use SDK
```js
const admin = require("firebase-admin");
const serviceAccount = require("../serviceAccountKey.json");

admin.initializeApp({
  credential: admin.credential.cert(serviceAccount),
  databaseURL: "https://foxfox-dev.firebaseio.com"
});

```

### Create custom tokens using the Firebase Admin SDK
> https://firebase.google.com/docs/auth/admin/create-custom-tokens#create_custom_tokens_using_the_firebase_admin_sdk
```js
let uid = 'some-uid';

admin.auth().createCustomToken(uid)
  .then(function(customToken) {
    // Send token back to client
    response.send(customToken)
  })
  .catch(function(error) {
    console.log('Error creating custom token:', error);
  });
```

### Sign in using custom tokens on clients
> https://firebase.google.com/docs/auth/admin/create-custom-tokens#sign_in_using_custom_tokens_on_clients