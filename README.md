# Express OpenID Connect Webapp Sample

Simple regular web app with https nodejs server and auth0 login + custom auth0 login page + custom auth0 database scripts + mongodb database connection

Based on [Express OpenID Connect Webapp Sample Repo](https://github.com/auth0-samples/auth0-express-webapp-sample) and [this video](https://www.youtube.com/watch?v=TXnDFU4sG0A). See a detailed walk-through of the original sample app on the [Express Quickstart](https://auth0.com/docs/quickstart/webapp/express).


## Prerequisites

- You need a mongoAtlas account and setup your tenant with a regular webapp with nodejs. More detailed explanations on how to setup auth0 with a custom database and connecting it with auth0 [here](https://www.youtube.com/watch?v=TXnDFU4sG0A).
I copied the scripts to the scripts/ folder but you can  use the default code for MongoDB you can select from dropdown in your tenant and update the code as you want. These options are in the Database Action Scripts section after allowing custom database in your tenant. Go to Authentication> Database> Username-Password-Authentication>Custom Database, enable 'my own database' and scroll down. Note: if you copied the scripts, change YOUR_MONGO_CONNECTION_URL_STRING for your own connection string or set it up according to the video. Same for all scripts

- [mkcert]() is required for running a self-signed ssl certificate from localhost. If not over https, the login flow could fail in some scenarios with the default auth0 login page.
Setup instructions are [here](https://github.com/thefrontside/simulacrum/blob/5bd797f68a0c33a4d8c98dc7f2b7a1d2526fa699/packages/ui/README.md#running-https-services-from-localhost). You should end up this part with a config folder with two files cert.crt and cert.key. These files will be read by the server.


- Related to the previous, notice you need to setup urls in your application configurations in the auth tenant such as callback and logout urls..Make sure to specify the protocol (https://).


- Add the login page code from pages/login.html to your custom login page in Branding>Universal Login> Advanced options>Login section in your tenant


I'm sure you can also do deployment and some configuration using the [auth0-cli](https://github.com/auth0/auth0-deploy-cli) but I have done all of this manually.


With all that in place, continue:

## Running This Sample Locally


1. Install the dependencies with npm:

```bash
npm install
```

2. Rename `.env.example` to `.env` and replace or check the following values.

- `CLIENT_ID`=from your tenant
- `ISSUER_BASE_URL`=https://your-tenant-domain.auth0.com
- `SECRET`='whatever'
- `PORT`=3000
- `CLIENT_SECRET`=from your tenant

```bash
mv .env.example .env
```

3. Run the sample app:

```bash
npm start
```

The sample app will be served at `https://localhost:3000`.



## License

This project is licensed under the MIT license.
