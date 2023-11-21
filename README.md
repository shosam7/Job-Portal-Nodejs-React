# Getting Started with Create React App

This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

## Available Scripts

In the project directory, you can run:

### `npm start`

Runs the app in the development mode.\
Open [http://localhost:3000](http://localhost:3000) to view it in your browser.

--server.js--
For server side of the application I have used REST API structure starting from server.js file
In this file I have used express and mongodb to connect to local database
Installed cors to avoid cors errors
from here I am configuring router class and will listen through port 8080

--Router.js--
Here with help of express router function, I am assigning different path to different calls (login, get, create, update and delete users)
And calling corresponding functions from controller class

--UserController.js--
This controller class provides five methods to handle the CRUD (Create, Read, Update, Delete) operations for the User model:
-createUser: creates a new user and saves it to the database.
-getUsers: retrieves all users from the database.
-updateUser: updates a user by its emailID.
-deleteUser: deletes a user by its emailID.
-Each method uses the try/catch block to catch any errors that might occur during the database operations
Added functionality is login feature that verifies if the email and password matches our data in database and returns message accordingly

--UserService.js--
Here I have written the logic behind every CRUD operations in the controller class.
Depending on the logic, I am either throwing an error or returning a message.
Based on this message controller function operates
While creating or updating user details, I am checking for both email and password if it is macthing the genric format.
Using bcrypt to encrypt password before storing in database
In delete function works only if the email is present in the database
For login, I am first checking if the user exists in the system and later verifyig if the email and password matches. If not throwing an error 

--User.js--
This is a model class that has schema.
Here I am initializing required paramaters(fullname, email, password)
Each has its own requirements such as matching a regex, minimum and maximum length etc.