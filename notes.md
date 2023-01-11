# MERN - Stack

M - Mongo
E - Express
R - React
N - Node

### Traditional Databases

Databases - collection of tables (user, products, movies, blog)
Tables - Primary Key (ID) columns inside the table(ie: username, first name, last name, dob)
Records - Rows of values that are stored in the table

### Mongo Database

Database = Database
Collections = Tables
Documents = Records

## Getting Started Server

- Need a package.json file ('npm init -y (in the terminal))
- Install Express ('npm i express' (in the terminal))
- Install Mongoose ('npm i mongoose' (in the terminal))
- Install dotenv ('npm i dotenv' (in the terminal))
- Update package.json from index.js to app.js

## .gitignore

Git Ignore - tells your git repo to ingnore certain files and folders from being tracked.
- Create a .gitignore
- '/node_modules'

## app.js file

- Add boiler plate code and have the app listen on 4000.

```
require("dotenv").config();
const express = require('express');
const app = express();


app.listen(process.env.PORT, function(){
    console.log(`movie app is listening on port ${process.env.PORT}`)
}) 
```

## .env file

- Contains constants that are specific for our environment
- Store items in there that you do not want published publically
- Add .env to the gitignore file
- Set the 'PORT = "4000"'
- Change the PORT in the app.js as shown above

## Creating Models

- Models help define what your database collection will look like
- Boiler Plate

```
const mongoose = require("mongoose");

const UserSchema = new mongoose.Schema({
// Create the Columns Here for the Collection
})


module.exports = mongoose.model("User", UserSchema)
```

## Controllers

- They will take in user requests and send back information
- Controllers will do the work and will Create, Read, Update, or Delete (CRUD) from the Database.

## Bcrypt - Hashing Passwords

- This will encrypt our password
- 'npm i bcrypt' in order to use it in your files.
- To hash the password you can use this example

 ```js
bcrypt.hashSync(req.body.password, 10);
```
- you will need to use 'bcrypt.compare()' to compare the passwords: this will return true or false

```js
const isPasswordMatch = await bcrypt.compare(req.body.password, user.password);
```

## JWT - JSON Web Token

- used to help identify and authenticate a user
- should be given in user login and signup
- jw.sign has 3 arguements: Payload, encrypt and decrypt message, option sets
- Example code:

```js
const token = jwt.sign({ id: newUser._id }, "secret_message_here", {
  expiresIn: 60 * 60 * 24,
});
```
