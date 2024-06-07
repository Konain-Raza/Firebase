# Firestore 📄🔥

Firebase is a toolbox full of tools to help build apps, and one of its best tools is Firestore. 🔧 Think of Firestore like a magical bookshelf where you can store all your app's information. 📚 It's super flexible, meaning you can organize your data however you like, without needing to follow strict rules.

Here's how it works:
- **Database**: Picture it as your magical bookshelf where you keep all your stuff. 📂
- **Collections**: These are like different bookshelves on your bookshelf. Each collection holds a specific type of information. 📚
- **Documents**: Inside each collection, you have different books, or documents, containing specific details. 📄
- **Subcollections**: Sometimes, you might want to organize your books even further, so you can have mini-books, or subcollections, inside your main books. 📗

With Firestore, you're the boss of how you want to organize your app's info. It's like having a super-flexible bookshelf that adapts to your needs, making it easy to manage all your app's data in one place. 🎉

## Document Operations ✍️

### `set` ✨
Creates or overwrites a single document.

```javascript
import { doc, setDoc } from "firebase/firestore"; 

const docRef = doc(db, "cities", "LA");
const data = {
  name: "Los Angeles",
  state: "CA",
  country: "USA"
};

setDoc(docRef, data)
  .then(() => {
    console.log("Document successfully written!");
  })
  .catch((error) => {
    console.error("Error writing document: ", error);
  });
```

  ### `get` 📝
Retrieves a single document.

```javascript
import { doc, getDoc } from "firebase/firestore"; 

const docRef = doc(db, "cities", "LA");

getDoc(docRef)
  .then((doc) => {
    if (doc.exists()) {
      console.log("Document data:", doc.data());
    } else {
      console.log("No such document!");
    }
  })
  .catch((error) => {
    console.error("Error getting document:", error);
  });
```

### `update` 🔄
```javascript
import { doc, updateDoc } from "firebase/firestore"; 

const docRef = doc(db, "cities", "LA");
const data = { population: 4000000 };

updateDoc(docRef, data)
  .then(() => {
    console.log("Document successfully updated!");
  })
  .catch((error) => {
    console.error("Error updating document: ", error);
  });
```

### `delete` 🗑️
Deletes a single document.

```javascript
import { doc, deleteDoc } from "firebase/firestore"; 

const docRef = doc(db, "cities", "LA");

deleteDoc(docRef)
  .then(() => {
    console.log("Document successfully deleted!");
  })
  .catch((error) => {
    console.error("Error removing document: ", error);
  });

```
## Query Operations 📊

### `query` 📝

Creates and returns a new query object.

```javascript
import { collection, query, where, getDocs } from "firebase/firestore"; 

const citiesRef = collection(db, 'cities');
const queryRef = query(citiesRef, where('state', '==', 'CA'));

getDocs(queryRef)
  .then((querySnapshot) => {
    querySnapshot.forEach((doc) => {
      console.log(doc.id, " => ", doc.data());
    });
  })
  .catch((error) => {
    console.error("Error getting documents: ", error);
  });
```

### `where` 🎯

Creates a new QueryConstraint that filters documents based on the provided condition.

```javascript
import { collection, query, where, getDocs } from "firebase/firestore"; 

const citiesRef = collection(db, 'cities');
const queryRef = query(citiesRef, where('population', '>', 1000000));

getDocs(queryRef)
  .then((querySnapshot) => {
    querySnapshot.forEach((doc) => {
      console.log(doc.id, " => ", doc.data());
    });
  })
  .catch((error) => {
    console.error("Error getting documents: ", error);
  });
```
### `orderBy` 🔝

Creates a new QueryConstraint that orders the query result by the specified field.

```javascript
import { collection, query, orderBy, getDocs } from "firebase/firestore"; 

const citiesRef = collection(db, 'cities');
const queryRef = query(citiesRef, orderBy('population', 'desc'));

getDocs(queryRef)
  .then((querySnapshot) => {
    querySnapshot.forEach((doc) => {
      console.log(doc.id, " => ", doc.data());
    });
  })
  .catch((error) => {
    console.error("Error getting documents: ", error);
  });
```
### `limit` 🔍

Creates a new QueryConstraint that limits the number of results returned by the query.

```javascript
import { collection, query, limit, getDocs } from "firebase/firestore"; 

const citiesRef = collection(db, 'cities');
const queryRef = query(citiesRef, limit(5));

getDocs(queryRef)
  .then((querySnapshot) => {
    querySnapshot.forEach((doc) => {
      console.log(doc.id, " => ", doc.data());
    });
  })
  .catch((error) => {
    console.error("Error getting documents: ", error);
  });
```

## Real-time Updates 🔄
### `onSnapshot` 📡

Attaches a listener for QuerySnapshot events.

```javascript
import { collection, onSnapshot } from "firebase/firestore"; 

const citiesRef = collection(db, 'cities');

const unsubscribe = onSnapshot(citiesRef, (querySnapshot) => {
  querySnapshot.forEach((doc) => {
    console.log(doc.id, " => ", doc.data());
  });
});
```

### `docChanges` 🔄

Returns an array of the changes since the last snapshot.

```javascript
Copy code
import { collection, onSnapshot } from "firebase/firestore"; 

const citiesRef = collection(db, 'cities');

const unsubscribe = onSnapshot(citiesRef, (querySnapshot) => {
  querySnapshot.docChanges().forEach((change) => {
    if (change.type === "added") {
      console.log("New city: ", change.doc.data());
    }
    if (change.type === "modified") {
      console.log("Modified city: ", change.doc.data());
    }
    if (change.type === "removed") {
      console.log("Removed city: ", change.doc.data());
    }
  });
});
```
