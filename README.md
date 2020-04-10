# useSnapshot

## A React hook to manage onSnapshot events with Firebase Firestore

### ⚡ Installing

Install with Yarn or NPM
`npm install firebase-onsnapshot` or `yarn add firebase-onsnapshot`

Import Module
`import useSnapshot from "firebase-usesnapshot";`

### 🔧 Usage

To use pass your query to the hook.
`const { loading, data } = useSnapshot(query)`

The hook returns a loading state that is true by default until the first onSnapshot event resolves.
It also returns a data array which is created by looping through the documents the snapshot returns.
A re-render is triggered whenever an onSnapshot event occurs.

### 📦 Example

```jsx
import React from "react";
import useSnapshot from "firebase-usesnapshot";
import { db } from "../helpers/db.js"; // const db = firebase.firestore();

const FirebaseComponent = () => {
  const { loading, data } = useSnapshot(
    db.collection("collection").where("document", "==", true)
  );

  if (loading) return <Loading />;
  return (
    <div>
      {data.map((data) => (
        <DataElement key={data.id} data={data} />
      ))}
    </div>
  );
};

export default FirebaseComponent;
```

### License

MIT
