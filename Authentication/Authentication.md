# Firebase Authentication 🛡️🔐

Firebase Authentication provides a secure and easy-to-use authentication system for your app. Here are some of the key functions it offers:

## User Registration and Sign-In 🔑

### `createUserWithEmailAndPassword` 📧🔒
Creates a new user account with the specified email address and password.

```javascript
import { createUserWithEmailAndPassword } from "firebase/auth";

const email = "example@example.com";
const password = "password123";

createUserWithEmailAndPassword(auth, email, password)
  .then((userCredential) => {
    const user = userCredential.user;
    console.log("User created:", user.uid);
  })
  .catch((error) => {
    console.error("Error creating user:", error);
  });
```
## Sign In 🔓

### signInWithEmailAndPassword 📧🔑

Signs in an existing user with the specified email address and password.

```javascript
import { signInWithEmailAndPassword } from "firebase/auth";

const email = "example@example.com";
const password = "password123";

signInWithEmailAndPassword(auth, email, password)
  .then((userCredential) => {
    const user = userCredential.user;
    console.log("User signed in:", user.uid);
  })
  .catch((error) => {
    console.error("Error signing in:", error);
  });
```

### signInWithGoogle 🟠🔑

Signs in a user using Google authentication.

```javascript
import { signInWithPopup, GoogleAuthProvider } from "firebase/auth";

const provider = new GoogleAuthProvider();

signInWithPopup(auth, provider)
  .then((userCredential) => {
    const user = userCredential.user;
    console.log("User signed in with Google:", user.uid);
  })
  .catch((error) => {
    console.error("Error signing in with Google:", error);
  });
```

### signInWithRedirect 🔀

Signs in using a third-party provider via a redirect.

```javascript
import { getAuth, signInWithRedirect, GoogleAuthProvider } from "firebase/auth";

const auth = getAuth();
const provider = new GoogleAuthProvider();
signInWithRedirect(auth, provider);
```
## User Management 👤🔧

### signOut 🚪

Signs out the currently authenticated user.

```javascript
import { signOut } from "firebase/auth";

signOut(auth)
  .then(() => {
    console.log("User signed out");
  })
  .catch((error) => {
    console.error("Error signing out:", error);
  });
```

### updateProfile 🔄

Updates the user's profile information.

```javascript
import { getAuth, updateProfile } from "firebase/auth";

const auth = getAuth();
const user = auth.currentUser;
updateProfile(user, {
  displayName: "New Name",
  photoURL: "https://example.com/profile.jpg"
}).then(() => {
  // Profile updated
}).catch((error) => {
  // Error
  console.error(error);
});
```
### updateEmail 📧

Updates the user's email address.

```javascript
import { getAuth, updateEmail } from "firebase/auth";

const auth = getAuth();
const user = auth.currentUser;
updateEmail(user, "newemail@example.com")
  .then(() => {
    // Email updated
  })
  .catch((error) => {
    // Error
    console.error(error);
  });
```
### updatePassword 🔑

Updates the user's password.

```javascript
import { getAuth, updatePassword } from "firebase/auth";

const auth = getAuth();
const user = auth.currentUser;
updatePassword(user, "newPassword")
  .then(() => {
    // Password updated
  })
  .catch((error) => {
    // Error
    console.error(error);
  });
```

## Password Reset 🔄🔑

### sendPasswordResetEmail 📧🔑

Sends a password reset email to the specified email address.

```javascript
import { sendPasswordResetEmail } from "firebase/auth";

const email = "example@example.com";

sendPasswordResetEmail(auth, email)
  .then(() => {
    console.log("Password reset email sent");
  })
  .catch((error) => {
    console.error("Error sending password reset email:", error);
  });

```

### confirmPasswordReset 🔑

Completes the password reset process.

```javascript
import { getAuth, confirmPasswordReset } from "firebase/auth";

const auth = getAuth();
confirmPasswordReset(auth, oobCode, newPassword)
  .then(() => {
    // Password has been reset
  })
  .catch((error) => {
    // Error
    console.error(error);
  });
```
### verifyPasswordResetCode 🔄

Verifies the password reset code.

```javascript
import { getAuth, verifyPasswordResetCode } from "firebase/auth";

const auth = getAuth();
verifyPasswordResetCode(auth, code)
  .then((email) => {
    // Code is valid; email is returned
  })
  .catch((error) => {
    // Error
    console.error(error);
  });
```

## Email Verification ✉️🔍

### sendEmailVerification ✉️🔍

Sends an email verification to the currently authenticated user.

```javascript
import { sendEmailVerification } from "firebase/auth";

sendEmailVerification(auth.currentUser)
  .then(() => {
    console.log("Email verification sent");
  })
  .catch((error) => {
    console.error("Error sending email verification:", error);
  });
```
### applyActionCode 🔄

Applies a verification code sent to the user.

```javascript
import { getAuth, applyActionCode } from "firebase/auth";

const auth = getAuth();
applyActionCode(auth, code)
  .then(() => {
    // Action code applied
  })
  .catch((error) => {
    // Error
    console.error(error);
  });
```

## Authentication State 🔒

### onAuthStateChanged 🔄

Sets an observer on the Auth object to listen for changes in the user's sign-in state.

```javascript
import { getAuth, onAuthStateChanged } from "firebase/auth";

const auth = getAuth();
onAuthStateChanged(auth, (user) => {
  if (user) {
    // User is signed in
  } else {
    // User is signed out
  }
});
