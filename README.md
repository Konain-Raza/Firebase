# Firebase 🚀

Firebase is a suite of backend cloud services and application development platforms offered by Google Cloud. It provides databases, authentication, hosting, and integration solutions for various applications, spanning Android, iOS, JavaScript, Node.js, Java, Unity, PHP, and C++.

## Introduction

Firebase offers a comprehensive suite of products and services that cover various aspects of app development, including authentication, database management, cloud storage, hosting, analytics, and more. Whether you're a solo developer working on a personal project or part of a large team building a complex application, Firebase has something for everyone.

## Getting Started

To start using Firebase in your project, follow these steps:

1. **Create a Firebase project:** Go to the [Firebase Console](https://console.firebase.google.com/) and create a new project.
2. **Set up your app:** Add your app to the Firebase project and follow the instructions to configure Firebase for your platform (iOS, Android, web, etc.).
3. **Add Firebase SDK:** Install the Firebase SDK in your app by following the platform-specific instructions provided in the Firebase Console.
4. **Start using Firebase:** Once the SDK is installed, you can start integrating Firebase services into your app.

## Services

### Authentication 🔐

Firebase Authentication provides a secure and easy-to-use authentication system for your app. It supports various authentication methods, including email/password, phone number, social authentication (Google, Facebook, etc.), and more.

#### Functions:

- `createUserWithEmailAndPassword`: Creates a new user account with the specified email address and password.
- `signInWithEmailAndPassword`: Signs in an existing user with the specified email address and password.
- `signInWithGoogle`: Signs in a user using Google authentication.
- `signInWithRedirect`: Signs in using a third-party provider via a redirect.
- `signOut`: Signs out the currently authenticated user.
- `updateProfile`: Updates the user's profile information.
- `updateEmail`: Updates the user's email address.
- `updatePassword`: Updates the user's password.
- `sendPasswordResetEmail`: Sends a password reset email to the specified email address.
- `confirmPasswordReset`: Completes the password reset process.
- `verifyPasswordResetCode`: Verifies the password reset code.
- `sendEmailVerification`: Sends an email verification to the currently authenticated user.
- `applyActionCode`: Applies a verification code sent to the user.
- `onAuthStateChanged`: Sets an observer on the Auth object to listen for changes in the user's sign-in state.

For detailed usage and code examples, refer to the [Firebase Authentication Documentation](https://firebase.google.com/docs/auth).

### Firestore 📄🔥

Firestore is a flexible, scalable database for mobile, web, and server development. It allows you to store and sync data in real-time between your users' devices and the Cloud. Firestore offers powerful querying, offline support, and automatic scaling, making it ideal for building responsive and feature-rich apps.

#### Functions:

- `set`: Creates or overwrites a single document.
- `get`: Retrieves a single document.
- `update`: Updates fields in a single document.
- `delete`: Deletes a single document.
- `query`: Creates and returns a new query object.
- `where`: Creates a new QueryConstraint that filters documents based on the provided condition.
- `orderBy`: Creates a new QueryConstraint that orders the query result by the specified field.
- `limit`: Creates a new QueryConstraint that limits the number of results returned by the query.
- `onSnapshot`: Attaches a listener for QuerySnapshot events.
- `docChanges`: Returns an array of the changes since the last snapshot.

For detailed usage and code examples, refer to the [Firestore Documentation](https://firebase.google.com/docs/firestore).

## Using Firebase in React

To use Firebase in a React project, you can install the Firebase npm package and import the necessary modules into your components.

Here's how you can include Firebase in your React project:

```javascript
// Install Firebase SDK using npm or yarn
npm install firebase
// Import Firebase modules in your React component
import firebase from "firebase/app";
import "firebase/auth";
import "firebase/firestore";

// Configure Firebase with your credentials
const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_AUTH_DOMAIN",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_STORAGE_BUCKET",
  messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
  appId: "YOUR_APP_ID"
};

// Initialize Firebase
firebase.initializeApp(firebaseConfig);

// Now you can use Firebase services in your React components
```
# Using Firebase in Vanilla JavaScript 🛠️

To use Firebase in your JavaScript project, you need to set up your Firebase configuration and initialize the Firebase app. Follow these steps to configure Firebase in your project:

## Step 1: Create firebase-config.js

Create a file named `firebase-config.js` in your project directory and add the following code:

```javascript
// Firebase configuration
const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_AUTH_DOMAIN",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_STORAGE_BUCKET",
  messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
  appId: "YOUR_APP_ID"
};

// Initialize Firebase
const firebaseApp = firebase.initializeApp(firebaseConfig);

// Export the Firebase app instance and configuration
export { firebaseApp, firebaseConfig };
```
Replace `"YOUR_API_KEY"`, `"YOUR_AUTH_DOMAIN"`, `"YOUR_PROJECT_ID"`, `"YOUR_STORAGE_BUCKET"`, `"YOUR_MESSAGING_SENDER_ID"`, and `"YOUR_APP_ID"` with your actual Firebase project credentials.

## Step 2: Use `firebase-config.js` in Your JavaScript Code

In your JavaScript code (e.g., `script.js`), import the variables from `firebase-config.js` and use them as needed:

```javascript
// Import all variables from firebase-config.js
import { firebaseApp, firebaseConfig } from "./firebase-config.js";

// Now you can use firebaseApp and firebaseConfig in your JavaScript code
console.log(firebaseApp);
console.log(firebaseConfig);
