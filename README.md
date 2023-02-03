# Read and Write with SQLite in React Native

- The application offers several customer management features, such as editing a customer's name or deleting the customer profile.  
- SQLite is the storage solution currently in use. The code to persist the list of customers is in place. 

## Table of contents

- [Overview](#overview)
  - [Screenshot](#screenshot)
  - [Links](#links)
- [My process](#my-process)
  - [Built with](#built-with)
  - [What I learned](#what-i-learned)
  - [Useful resources](#useful-resources)
- [Author](#author)

## Overview

### Screenshot
![image](https://user-images.githubusercontent.com/108392678/216527420-0d4796e7-8bdc-43f1-bd43-8cb2ec03f7c6.png)
![image](https://user-images.githubusercontent.com/108392678/216527449-ce0aac31-b9ea-4fb5-970d-8a282e9a3e4e.png)
![image](https://user-images.githubusercontent.com/108392678/216527485-89dc7d84-ba1f-4675-8e53-f6e6a7b09087.png)



### Links

- Github: [Code](https://github.com/marvedventures/read-and-write-with-sql)

## My process

### Built with

- [React Native](https://reactnative.dev/docs/environment-setup) - React Native app built with expo
- [SQLite](https://docs.expo.dev/versions/latest/sdk/sqlite/) - For storing restaurant's customers.
- [StyleSheet](https://reactnative.dev/docs/stylesheet) - For styles

### What I learned

- Create a React Native App using Expo
- Using SQLite to store customers.
- Using SQL CRUD operations in React Native
- Connecting SQLite to a state
- Handling side-effects using useEffect Hook
- Use View, View, Text Components 
- Extract all styles to StyleSheet API

Here is a code snippet:

```jsx
   const [customers, setCustomers] = useState([]);

  useEffect(() => {
    db.transaction(tx => {
      tx.executeSql(
        'create table if not exists customers (id integer primary key not null, uid text, name text);'
      );
      tx.executeSql('select * from customers', [], (_, { rows }) => {
        const customers = rows._array.map(item => ({
          uid: item.uid,
          name: item.name,
        }));
        setCustomers(customers);
      });
    });
  }, []);
```

### Useful resources

- [React Native Docs (StyleSheet) ](https://reactnative.dev/docs/stylesheet) - This helped me for all the neccessary React Native styles. I really liked their documentation and will use it going forward.
- [SQLite](https://docs.expo.dev/versions/latest/sdk/sqlite/) - This helped me for saving customers.

## Author

- Website - [Marvin Morales Pacis](https://marvin-morales-pacis.vercel.app/)
- LinkedIn - [@marvedventures](https://www.linkedin.com/in/marvedventures/)
- Twitter - [@marvedventures](https://www.twitter.com/marvedventures)
