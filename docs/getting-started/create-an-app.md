---
id: create-an-app
title: Create an App
---

To get set up quickly with your own Backstage project you can create a Backstage
App.

A Backstage App is a monorepo setup with `lerna` that includes everything you
need to run Backstage in your own environment.

## Create an app

To create a Backstage app, you will need to have
[NodeJS](https://nodejs.org/en/download/) Active LTS Release installed
(currently v12).

Backstage provides a utility for creating new apps. It guides you through the
initial setup of selecting the name of the app and a database for the backend.
The database options are either SQLite or PostgreSQL, where the latter requires
you to set up a separate database instance. If in doubt, choose SQLite, but
don't worry about the choice, it's easy to change later!

The easiest way to run the create app package is with `npx`:

```bash
npx @backstage/create-app
```

This will create a new Backstage App inside the current folder. The name of the
app-folder is the name that was provided when prompted.

<p align='center'>
  <img src='../assets/getting-started/create-app_output.png' width='600' alt='create app'>
</p>

Inside that directory, it will generate all the files and folder structure
needed for you to run your app.

### Folder structure

```
app
├── README.md
├── lerna.json
├── package.json
├── prettier.config.js
├── tsconfig.json
├── packages
│   └── app
│       ├── package.json
│       ├── tsconfig.json
│       ├── public
│       │   └──  ...
│       └── src
│           ├── App.test.tsx
│           ├── App.tsx
│           ├── index.tsx
│           ├── plugins.ts
│           └── setupTests.ts
└── plugins
    └── welcome
        ├── README.md
        ├── package.json
        ├── tsconfig.json
        └── src
            ├── index.ts
            ├── plugin.test.ts
            ├── plugin.ts
            ├── setupTests.ts
            └── components
                ├── Timer
                │   └──  ...
                └── WelcomePage
                    └──  ...
```

## Run the app

When the installation is complete you can open the app folder and start the app.

```bash
cd my-backstage-app
yarn start
```

_When `yarn start` is ready it should open up a browser window displaying your
app, if not you can navigate to `http://localhost:3000`._

In most cases you will want to start the backend as well, as it is required for
the catalog to work, along with many other plugins.

To start the backend, open a separate terminal session and run the following:

```bash
yarn --cwd packages/backend start
```