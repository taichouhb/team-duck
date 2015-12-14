# Zembo

## Overview
The idea for this web-based software application is to assist college students in getting together to collaborate on group-based assignments and engage in study sessions, allowing for better learning techniques. This web application will utilize location-based services to determine where you are located on campus, and it will give you notifications of anyone nearby looking to meet up and form a study group.

## How To Run
Make sure you have Node.js installed on your system.

You can download it [here](https://nodejs.org/en/download/)
(required for Windows) or follow these commands in the terminal:

On Linux:
```bash
$ sudo apt-get update
$ sudo apt-get install nodejs
$ sudo apt-get install npm
```
On Mac OS:
```bash
$ brew install node
```

After you have Node.js installed,
```bash
$ git clone https://github.com/AnthLi/team-duck
$ cd path/to/repository
$ npm install
```

#### Usage
```bash
$ cd path/to/repository
$ nodemon app.js
```
The application is now running on localhost:3000.

If ```nodemon app.js``` isn't working, try ```npm install -g nodemon```, then re-run ```nodemon app.js```.

## Libraries
- [body-parser](https://github.com/expressjs/body-parser) to retrieve submitted form data
- [connect-flash](https://github.com/jaredhanson/connect-flash) to flash messages to certain pages
- [express](http://expressjs.com/) to provide the main web framework
- [express-handlebars](https://github.com/ericf/express-handlebars) to provide templating and styling via injection
- [express-session](https://www.npmjs.com/package/express-session) to support session states
- [multer](https://github.com/expressjs/multer) to upload files to the file system
- [nodemon](https://github.com/remy/nodemon) to automatically reload the server on any changes
- [pg](https://github.com/brianc/node-postgres) to access the PostgreSQL database

## Views
- ```/index```: the home page
- ```/about```: what we're about
- ```/team```: the devs and who we are
- ```/class```: individual class pages
- ```/class/content```: events and posts for each individual class page
- ```/class/students```: a list of all students in the class
- ```/group/createEvent```: event creation page for an individual class
- ```/group/createPost```: post submission for an individual class
- ```/user/login```: logging into the application
- ```/user/registration```: registering for an account
- ```/user/profile```: the user profile
- ```/admin/online```: a list of all online users
- ```/admin/users```: a list of every user and all of their attributes
- ```/admin/controls```: various admin controls

## Statefulness
Statefulness is maintained by using the [express-session](https://www.npmjs.com/package/express-session) library. In ```app.js```, ```/routes/user-routes.js```, and ```/routes/admin-routes.js```, there are various GET requests that check both the user session state through ```req.session.user``` and if the user is online through ```/lib/online.js```.

If the user session state exists, then that means they are currently logged in. Otherwise, it would be ```undefined```. Therefore, no user session exists. The library ```/lib/online.js``` simply stores a list of every user logged in. If a user isn't in the list, then either they are not logged in, or the server restarted and ended their session.

## Persistence
This application uses a PostgreSQL database. The database stores tables, one of which consists of every single user registered for the app. Each user in the table has a UID, first name, last name, email, date of birth, admin status, and number of flags for inappropriate behavior for their attributes. There is also a table consists of every single class and their class ID that goes along with it. For example, class COMPSCI 326 and class ID 34166. Another table contains blacklisted users that were banned from the app, which contains the banned user's email address. One last table contains the id, first and last names, description, and role of each developer, which gets queried into the the ```/team``` view.

The library ```/lib/database.js``` contains the connection to the database and various functions such as adding and deleting users from the database. A file containing the password to the database is stored locally and ignored by bit on each developer's computer and parsed in order to create a successful connection to the database. (Hint: the password in old commits is not the same, so don't try to be clever!)

## The Team
- Anthony Li
- Harsh Keswani
- Ben Cheung
- Zachary Milrod
- Jonathan Gatley

## Final Project Document
https://docs.google.com/document/d/1QAY0uNoGbssk_nWpT-EiKctfoWRgb0gmmcVC5dHICgY/edit?usp=sharing
