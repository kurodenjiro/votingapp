# Vote App

![Build Passed](https://img.shields.io/badge/build-passed-lightgrey.svg)
![Status Beta](https://img.shields.io/badge/status-beta-blue.svg)

## Free Code Camp Challenge

[**HEROKU APP**](https://neckers-voteapp.herokuapp.com) - https://neckers-voteapp.herokuapp.com

This app was built in MERN stack. It uses: MongoDB, Node, Express, React, React Router, Redux, Socket.IO, Material-UI and Google Charts.
The UI can be used on mobile, tablet and desktop.

_Note_:
- Server and client components are _isomorphic_.
- Authentication doesn't use cookie but a mix in client ( in localStorage/Redux store ) and server, by Socket.IO, check.
- Already voted polls are saved in localStorage

### User Stories
- As an authenticated user, I can keep my polls and come back later to access them.
- As an authenticated user, I can share my polls with my friends.
- As an authenticated user, I can see the aggregate results of my polls.
- As an authenticated user, I can delete polls that I decide I don't want anymore.
- As an authenticated user, I can create a poll with any number of possible items.
- As an unauthenticated or authenticated user, I can see and vote on everyone's polls.
- As an unauthenticated or authenticated user, I can see the results of polls in chart form. (This could be implemented using Chart.js or Google Charts.)
- As an authenticated user, if I don't like the options on a poll, I can create a new option.

### It's a bug? No, it's a feature!
Ok, they aren't really features, but there are some actions _not really good_ but ,for this challenge, I don't mind.

- I can vote multiple times if I clear my local storage or I do an access from another device ( or I go in incognito mode, etc.. ).
 - Yeah, because to get track of the votes I have to save some informations in server side and, with users without login, I've to do a really hard work to check them. So.. the DB is in a sandbox powered by mlab and I don't want to stress it more.
- I can't edit or remove options after the poll publish.
 - No, you can't. These actions weren't in the user stories.
- I can't have multiple logins.
  - Yep, everytime you do a login you get a different `session_id` in both side: client and server.
- I can't edit my personal data, like e-mail, nick or password
  - No, you can't. These actions weren't in the user stories.
- I can't change my preferences
  - Yes, I don't like this _feature_ in special way but I've decided to not implement an _UNDO_ action for some security reasons.  

### `process.env`
* __MONGOURI__: your query to authenticate in mongodb server `mongodb://<dbuser>:<dbpassword>@ds119508.mlab.com:19508/neckersbox`
* __NODE_ENV__: for example `production`. _Note_: this must be the same between server and client.

### Scripts
To compile or run this app use gulp and/or npm.
* __Build__: `gulp build`
* __Watch__: `gulp watch` or `npm run watch`
* __Clean__: `gulp clean`
* __Start Server__: `gulp start` or `npm run start-server`
_Note_: normally `start-server` hide console messages, to show them you should exec `npm run start-server-debug`

### MongoDB configuration
To properly works this application need a MongoDB database with two collections:
* **vote_users** To save signed users
* **vote_polls** To save users polls
