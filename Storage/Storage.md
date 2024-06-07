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

