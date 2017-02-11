# Stormpath Notes Server

This is the server for the Stormpath Notes Tutorial for iOS and Android, where we show you how to build a note-taking app that saves to a server using Stormpath.

[Stormpath Notes (iOS) in Swift Tutorial](https://stormpath.com/blog/build-note-taking-app-swift-ios/) - [Stormpath Notes (Android) Tutorial](https://stormpath.com/blog/build-user-authentication-for-android-app/)

Stormpath Notes Server is an [express-stormpath](https://github.com/stormpath/express-stormpath) application that hosts the Stormpath default `application/json` endpoints, and additional endpoints to retrieve and save notes. 

The master branch automatically will be deployed to https://stormpathnotes.herokuapp.com/

**[Read the Tutorial for how to Build this Server in Node.js](https://stormpath.com/blog/tutorial-build-rest-api-mobile-apps-using-node-js)**

## Steps to run

1. Download and install [Node.js](https://nodejs.org/)
2. Grab your API Keys from the [Stormpath Admin Console](https://api.stormpath.com) (easiest way is to use the quickstart)

Log into the Stormpath Account you created, and click on the Node.js quickstart. In the first page, you’ll see a section showing you how to set up your API Keys by using environment variables. Environment variables allow you to configure your application without using code, which is great when you have multiple development environments or even servers. Paste the API Keys from the quickstart into your command line:

*This is an example; use the values in Stormpath instead*

```
$ export STORMPATH_CLIENT_APIKEY_ID=EXAMPLE
$ export STORMPATH_CLIENT_APIKEY_SECRET=EXAMPLE
$ export STORMPATH_APPLICATION_HREF=https://api.stormpath.com/v1/applications/EXAMPLE
```

3. Run the commands:

```bash
git clone https://github.com/stormpath/stormpath-express-mobile-notes-example.git
cd stormpath-express-mobile-notes-example
node index.js
```

## Endpoints

All endpoints require authentication with an `Authorization: Bearer ACCESSTOKEN` header.

`GET /notes`

Returns a json object like {"notes": "The notes the user saved"}

`POST /notes`

Takes a json object of` {"notes": "The new notes the user wants to save"}` and saves it to the Stormpath account's customData.

Returns a blank page with a status code of 200 OK if successful, or 400 if the request was malformed.