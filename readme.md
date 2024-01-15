# Backend 101
## How to setup a simple Express server with Prisma and PostgreSQL

# 1.0 - Introduction
This tutorial aims to give a quick introduction into how backend development works. You will learn how to setup an Express server running in the Node runtime, initializing a Prisma schema and Prisma Client, and connect to a PostgreSQL database.

This tutorial was prompted by the need to learn the basics of backend development, and by following along with this tutorial you should have the functioning barebones of a server connected to a database.

## 1.1 - How to Use This Tutorial

## 1.2 - What to Use

## 1.3 - Disclaimer

1) I am NOT a backend developer - I am a beginner when it comes to backend development. This tutorial is a structured "note-to-self" based on my experiences from setting up my first backend. My hope is that someone in a similiar situation might find it useful in order to gain a basic understanding of how backend development works.

2) Mention Mac? Differences with Windows?


# 2.0 - Getting Started
// List going through the steps to get the project running.

## 2.1 - Creating Project Folder & Setting up File Structure
### Working directory: "demo"
Create a new folder with a name of your choosing; I've named mine "demo". Inside this folder create 2 new folders called "client" and "server". Your project directory should now look like this:
```
demo
    |
    client
    server
```
All your code related to the server will be located in "server" folder, while we will create a basic website in our "client" folder.
Open the your project in a code editor and let's start setting up Express.

## 3.0 - Installing Express
### Working directory: "server"
Navigate into your "server" folder and run ```npm init```. This command will walk you through a number of project settings, but the only one we will worry about is "entry point: (index.js)". You could just hit enter and move on with the setup, but I decided to call my entry point "app.js". For avoiding confusion, you should too.

We will use this file to configure a script and install some dependencies. The first dependency is Express itself.

Run ```npm install express``` to install Express in your project. Look in the package.json file to see that Express was installed correctly. We will be using ES modules import / export syntax for this project, so make sure to add "type": "module" to your package.json as well.

## 3.1 - Setting up Your First Express Server
### Working directory: "server"
Now that we have Express installed, let's setup a simple server. First, create a new javascript file and name it the same as the entry point - for us that should be "app.js". Open the "app.js" file and import express from 'express'. We can now run a function called "express", so let's do that and store its return value inside a variable we name "app". Your code should look like this:

``` 
import express from "express"
const app = express()

```
This is basically our server, and it has a lot of different methods that we can make use of.
First, in order for our server to actually run, we need for it to listen for incoming requests. We can do this by making our server listen to a port. In our case, port 3000.
```
app.listen(3000)
```
Now, we must start our server. Go to your terminal and type in ```node app.js  ``` to start your server.

If we open our browser and type "localhost:3000" we get an HTML file that says "Cannot GET/". This basically means that our server is running, but it's not returning anything. So let's fix that. Let's pass a callback function as an argument to the listen method. This function will run when the server starts up. Let's make our server log out a "Hello, World" to our console.
```
app.listen(3000, ()=>{
    console.log("Hello, World")
})
```
Restart your server (```ctrl+c``` to stop the script and run ```node app.js``` again) and you will see that the server is outputting "Hello, World". Nice...

Now, before we continue, let's install a package called "nodemon". "nodemon" will automatically rerun our server everytime we save our file, so that we don't have to stop and run our server manually everytime we make any changes in our code. 

Run ```npm install nodemon``` to install "nodemon". Go to the package.json to see "nodemon" added to our dependecies. While we're here, let's add a script: "server": "nodemon app.js" to our config. Run ```npm run server``` in your terminal, and our server will automatically restart everytime we save our changes in our editor.

That's it, you have now completed the setup of our server. Let's get our database up and running.

## 4.0 Installing PostgreSQL

