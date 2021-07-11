---
timeToRead: 0
authors:
- Reboot-Codes
title: Make a Twitter Clone with the MERN Stack
excerpt: Basically re-make twitter using the MERN stack. The MERN stack uses MongoDB
  (as a database, of course), Express (api package for Node.js), React (as a front-end
  javascript library), and Node.js (the base runtime for the server driving the stack,
  except MongoDB, I think).
date: 2021-07-11T07:00:00+00:00
draft: false

---
Basically re-make twitter using the MERN stack. The MERN stack uses MongoDB (as a database, of course), Express (api package for Node.js), React (as a front-end javascript library), and Node.js (the base runtime for the server driving the stack, except MongoDB, I think). Using this stack, the developer only needs to know Javascript as a programing language (plus JSX and CSS) and have knowledge of how MongoDB is structured to make the REST API powered by Express and Node.js.

## The Backend

Normally people start with the frontend, however I find that making the backend first makes things easier as you have already organized the database and you don’t worry about needing a thing that you forgot to expose in the API.

The Backend uses Express (api server package, so we don’t have to do it ourselves), Mongoose (MongoDB driver that almost forces you to use a schema to keep things organized), and GraphQL (a better query language that structures the response so nothing breaks if we reorganize the organization of things). The API will use the standard HTTP request types (like `GET`, `POST`, `PUT`, and `DELETE`) while using GraphQL in the body of the requests.

### Packages

Here are all the direct dependancies for the Backend:

* express
* graphql
* graphql-express
* mongoose

### Setup

Setup the backend, we should probably have the database running in the background (or dockerized somewhere). To do this we need to install MongoDB on our local machine anyway to get access to the Mongo Shell and have a nice local database for testing. However you may not want the database installed on your main OS, so you should dockerize it; a tutorial on this can be found [here](https://coderwall.com/p/vxq6oa/setup-a-mongodb-container-with-a-docker-file). But I will set it up on my local machine for simplicity.

#### MacOS

On macOS (with Homebrew installed) you can run this one-liner to install MongoDB:

```bash
brew tap mongodb/brew && brew install mongodb-community
```

This will add the “tap” for all MongoDB packages, and install MongoDB Community. Then start up the server using:

```bash
brew services start mongodb-community
```

However if you are using MongoDB Atlas, or only use MongoDB in a docker container, then you may just want the shell. For that run:

```bash
brew tap mongodb/brew && brew install mongodb-community-shell
```

This adds the “tap” and installs the shell. This isn’t a tutorial on how to use the MDB shell and how to sign in using credentials; so please google that if you have trouble.

Or if you don’t have brew, then download MDB [here](https://www.mongodb.com/try/download/community).

#### Linux

Follow the instructions for your specific distro [here](https://docs.mongodb.com/manual/administration/install-on-linux/).

#### Windows

Download the installer [here](https://www.mongodb.com/try/download/community), run the `MSI File`, and follow the instructions to install MongoDB.

You should now have MongoDB installed now (yay!)

---

## The Frontend

The Frontend uses React (of course), Styled-Components (for templating components), and Tailwind CSS (provided utility styling classes and keeping things consistent). Other notable dependancies are Axios (a replacement for `fetch()`) and GraphQL (this needs to be in the frontend for obvious reasons).