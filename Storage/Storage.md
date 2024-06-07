# Firebase Storage 🗄️

Firebase Storage provides functions for managing and interacting with cloud storage buckets. Below is a list of commonly used Firebase Storage functions:

## Uploads 📤

### `uploadBytes`
Uploads data to the specified storage path.

```javascript
import { getStorage, ref, uploadBytes } from "firebase/storage";

const storage = getStorage();
const storageRef = ref(storage, 'path/to/file');
const data = ... // File or Blob
const uploadTask = uploadBytes(storageRef, data);

// Listen for state changes, handle progress, errors, and completion
uploadTask.on('state_changed', 
  (snapshot) => {
    // Track progress and update UI
  }, 
  (error) => {
    // Handle errors
  }, 
  () => {
    // Handle successful completion
    uploadTask.snapshot.ref.getDownloadURL().then((downloadURL) => {
      // Do something with the download URL
    });
  }
);
```
## `uploadFile` 📤

Uploads a file to the specified storage path.

```javascript
import { getStorage, ref, uploadFile } from "firebase/storage";

const storage = getStorage();
const storageRef = ref(storage, 'path/to/file');
const file = ... // File object
const uploadTask = uploadFile(storageRef, file);

// Listen for state changes, handle progress, errors, and completion
```
## Tracking Upload Progress 📊

To track the progress of an upload task, you can define a function that calculates the progress percentage and updates the user interface accordingly.

Here's a function to track upload progress:

```javascript
// Function to track upload progress
function trackUploadProgress(snapshot) {
  // Calculate the progress percentage
  const progress = (snapshot.bytesTransferred / snapshot.totalBytes) * 100;
  console.log('Upload is ' + progress + '% done');

  // Update UI with the progress
  // For example, update a progress bar element
}

// Example usage:
uploadTask.on('state_changed', trackUploadProgress);
```
## Downloads 📥

### `getDownloadURL`
Retrieves the download URL for a file in storage.

```javascript
import { getStorage, ref, getDownloadURL } from "firebase/storage";

const storage = getStorage();
const fileRef = ref(storage, 'path/to/file');
getDownloadURL(fileRef)
  .then((url) => {
    // Do something with the download URL
  })
  .catch((error) => {
    // Handle errors
  })
```
## Deletions ❌

### `deleteObject`
Deletes an object (file or folder) from storage.

```javascript
import { getStorage, ref, deleteObject } from "firebase/storage";

const storage = getStorage();
const fileRef = ref(storage, 'path/to/file');
deleteObject(fileRef)
  .then(() => {
    // File deleted successfully
  })
  .catch((error) => {
    // Handle errors
  });

```
## Metadata ℹ️

### `getMetadata`
Retrieves metadata for a file or folder in storage.

```javascript
import { getStorage, ref, getMetadata } from "firebase/storage";

const storage = getStorage();
const fileRef = ref(storage, 'path/to/file');
getMetadata(fileRef)
  .then((metadata) => {
    // Do something with metadata
  })
  .catch((error) => {
    // Handle errors
  });
```
## Update Metadata 🔄

Updates metadata for a file or folder in storage.

```javascript
import { getStorage, ref, updateMetadata } from "firebase/storage";

const storage = getStorage();
const fileRef = ref(storage, 'path/to/file');
const newMetadata = {...}; // Updated metadata
updateMetadata(fileRef, newMetadata)
  .then(() => {
    // Metadata updated successfully
  })
  .catch((error) => {
    // Handle errors
  });
```
These are some of the commonly used Firebase Storage functions for managing cloud storage buckets. For more details and advanced functionalities, refer to the Firebase documentation.
