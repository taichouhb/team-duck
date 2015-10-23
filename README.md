# The Homework Project

## Installation
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

## Usage
```bash
$ cd path/to/repository
$ node app.js
```
The application is now running on localhost:3000.

## Branching
```bash
$ git checkout -b [branch name]
$ git checkout [branch name]
$ git branch
```

## Merging your branch to master
```bash
$ git checkout [your branch]
$ git push origin [your branch]
$ git checkout master
$ git merge [your branch]
```
