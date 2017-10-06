# Nativescript Sqlcipher  

A sqlcipher module for nativescript application.   
Inspired by [NathanaelA/Nativescript-Sqlite](https://github.com/NathanaelA/nativescript-sqlite)

### Create/Open Database
Before creating database, nativescript-sqlcipher module must be imported.  
```var Database = require('nativescript-sqlcipher');```  
Then create a new database:  
```var sqlcipher = new Database(dbname, options, callbackFn)```  
where in nativescript-sqlite module, ```options``` only support readOnly property where now options can read key property as PRAGMA Key for database encryption.
```javascript
  var options = {
    readOnly: false,
    key: 'Password'   // key must be a string
  }
```  
If property key is missing, or in a wrong format. Database would not be encrypted.

### Example
```javascript
  var Database = require('nativescript-sqlcipher');

  var options = {
    key: 'Password'
  }
  var sqlcipher = new Database('myDatabase', options);  //sqlcipher is a Promise type
  sqlcipher
    .then( (db)=>{
      db.execSQL('CREATE TABLE my_first_table (name TEXT, age INTEGER);');
    }) 
    .catch( (err)=>{
      alert('Database creation failed.');
    })
```

### Update Log
Added all updates to sqlcipher.ios.js from [NathanaelA/Nativescript-Sqlite](https://github.com/NathanaelA/nativescript-sqlite/blob/master/sqlite.ios.js).  