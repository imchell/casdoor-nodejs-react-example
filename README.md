<h1 align="center" style="border-bottom: none;">Casdoor NodeJS React Example</h1>

## Demo

*Password input is clipped out of the recording.*

![react-express-illustration.gif](public/react-express-illustration.gif)

## Architecture

This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app) and [Express](https://expressjs.com/).

The example includes two parts:

| Name     | SDK                | Language             | Source code                                                                 |
|----------|--------------------|----------------------|-----------------------------------------------------------------------------|
| Frontend | casdoor-js-sdk     | Javascript + React   | https://github.com/casdoor/casdoor-nodejs-react-example/tree/master/src     | 
| Backend  | casdoor-nodejs-sdk | JavaScript + Express | https://github.com/casdoor/casdoor-nodejs-react-example/tree/master/backend | 

## Installation

The example uses Casdoor to manage members, so you need to create an organization and an application in a Casdoor instance in advance.

### Necessary Configurations

#### Get the Code

```shell
git clone https://github.com/casdoor/casdoor
git clone https://github.com/casdoor/casdoor-nodejs-react-example
```

#### Run Example

1. Run Casdoor
2. Configure
   - Backend
   - Frontend

#### Backend Configs

Initialization requires 6 (or 5) parameters, all in string type. Please refer to the official doc on [backend SDK configuration](https://casdoor.org/docs/how-to-connect/sdk#1-backend-sdk-configuration) for the latest change.

| Parameter        | Must | Description                                                                   |
|------------------|------|-------------------------------------------------------------------------------|
| endpoint         | Yes  | Casdoor Server URL, like `https://door.casdoor.com` or `http://localhost:8000` |
| clientId         | Yes  | Client ID for the Casdoor application                                         |
| clientSecret     | Yes  | Client secret for the Casdoor application                                     |
| jwtPublicKey     | Yes  | The public key for the Casdoor application's cert                             |
| organizationName | Yes  | The name for the Casdoor organization                                         |
| applicationName  | No   | The name for the Casdoor application                                          |

```js
// in ./backend/server.js
const authCfg = {
  endpoint: 'https://door.casdoor.com',
  clientId: '0ba528121ea87b3eb54d',
  clientSecret: '04f4ca22101529a3503d5a653a877b4e8403edf0',
  certificate: cert,
  orgName: 'casbin',
}
```

#### Frontend Configs

The first 4 parameters should use the same value as the Casdoor backend SDK. The last parameter redirectPath is relative path for the redirected URL, returned from Casdoor's login page. For the latest change, please refer to the official doc on [frontend SDK configuration](https://casdoor.org/docs/how-to-connect/sdk#2-frontend-configuration).

```js
// in ./src/Setting.js
const config = {
  serverUrl: "http://localhost:8000", //casdoor server url
  clientId: "4262bea2b293539fe45e",
  organizationName: "casbin",
  appName: "app-casnode",
  redirectPath: "/callback",
};
```

After setting configurations up, install all dependencies by running `yarn install`. Then, while Casdoor is operating, run the following scripts.

### Available Scripts

Launch the backend powered by Express at [http://localhost:8080](http://localhost:8080):

```shell
node backend/server.js
```

Launch the frontend app in the development mode:

```shell
yarn start
```

Note that the port running frontend is set in `package.json`:

`"start": "PORT=9000 react-scripts start"`

Open [http://localhost:9000](http://localhost:9000) in your browser to view it.
