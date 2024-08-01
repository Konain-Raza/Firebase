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

uploadBytes(storageRef, data).then((snapshot) => {
  console.log('Uploaded a blob or file!');
});
```

### `uploadString`
Uploads a string to the specified storage path.

```javascript
import { getStorage, ref, uploadString } from "firebase/storage";

const storage = getStorage();
const storageRef = ref(storage, 'path/to/file');
const stringData = 'Hello, World!';

uploadString(storageRef, stringData).then((snapshot) => {
  console.log('Uploaded a raw string!');
});
```

### `uploadBytesResumable`
Uploads data to the specified storage path with resumable upload.

```javascript
import { getStorage, ref, uploadBytesResumable } from "firebase/storage";

const storage = getStorage();
const storageRef = ref(storage, 'path/to/file');
const data = ... // File or Blob

const uploadTask = uploadBytesResumable(storageRef, data);

// Listen for state changes, errors, and completion
uploadTask.on('state_changed', 
  (snapshot) => {
    // Observe state change events such as progress, pause, and resume
    const progress = (snapshot.bytesTransferred / snapshot.totalBytes) * 100;
    console.log('Upload is ' + progress + '% done');
  }, 
  (error) => {
    // Handle errors
    console.error(error);
  }, 
  () => {
    // Handle successful uploads
    uploadTask.snapshot.ref.getDownloadURL().then((downloadURL) => {
      console.log('File available at', downloadURL);
    });
  }
);
```

## Downloads 📥

### `getDownloadURL`
Gets the download URL for the specified storage path.

```javascript
import { getStorage, ref, getDownloadURL } from "firebase/storage";

const storage = getStorage();
const storageRef = ref(storage, 'path/to/file');

getDownloadURL(storageRef).then((url) => {
  console.log('File available at', url);
}).catch((error) => {
  console.error(error);
});
```

## Deletions 🗑️

### `deleteObject`
Deletes the object at the specified storage path.

```javascript
import { getStorage, ref, deleteObject } from "firebase/storage";

const storage = getStorage();
const storageRef = ref(storage, 'path/to/file');

deleteObject(storageRef).then(() => {
  console.log('File deleted successfully');
}).catch((error) => {
  console.error(error);
});
```

## Metadata 📝

### `getMetadata`
Gets the metadata for the specified storage path.

```javascript
import { getStorage, ref, getMetadata } from "firebase/storage";

const storage = getStorage();
const storageRef = ref(storage, 'path/to/file');

getMetadata(storageRef).then((metadata) => {
  console.log('Metadata retrieved:', metadata);
}).catch((error) => {
  console.error(error);
});
```

### `updateMetadata`
Updates the metadata for the specified storage path.

```javascript
import { getStorage, ref, updateMetadata } from "firebase/storage";

const storage = getStorage();
const storageRef = ref(storage, 'path/to/file');

const newMetadata = {
  cacheControl: 'public,max-age=300',
  contentType: 'image/jpeg',
};

updateMetadata(storageRef, newMetadata).then((metadata) => {
  console.log('Metadata updated:', metadata);
}).catch((error) => {
  console.error(error);
});
```

These functions cover the basics of interacting with Firebase Storage.
