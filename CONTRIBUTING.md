
# Contributing to Real Dev Squad API

- [Getting Started](#getting-started)
- [NPM Command Reference](#npm-command-reference)
- [Project Structure](#project-structure)
- [Generating Authentication Token](#generating-authentication-token)
- [Pull request guidelines](#pull-request-guidelines)

## Getting Started

Instructions for initial setup can be found in the [README](README.md).

## NPM Command Reference

##### `npm install`

Installs all `dependencies` listed in the root `package.json`.

##### `npm run test`

The script associated with `npm run test` will run all tests that ensures that your commit does not break anything in the
repository. This will run the lint, integration and unit tests.

##### `npm run lint`
Runs the lint checks in the project.

##### `npm run generate-api-schema`
Generates the API schema in the file `public/apiSchema.json`.


## Project Structure
The following project structure should be followed:

``` shell script
|-- website-backend
    |-- config
    |   |-- custom-environment-variables.js
    |   |-- default.js
    |   |-- development.js
    |   |-- production.js
    |   |-- staging.js
    |   |-- test.js
    |-- controllers
    |   |-- healthController.js
    |   |-- // Controller files concerning function on a similar entity
    |-- logs
    |   |-- // log files
    |-- middlewares
    |   |-- // individual middleware files to be required on server start or in the route middleware
    |-- models
    |   |-- // Files consisting of the individual table/collection config and wrapper interaction functions
    |-- routes
    |   |-- index.js // routes files separated by their first path string
    |   |-- auth.js // the individual routes files should contain the OPEN API JSDOC reference
    |-- services
    |   |-- authService.js // Files using any 3rd party library/service or providing any secific service in the project
    |-- test
    |   |-- fixtures
    |   |   |-- auth
    |   |       |-- githubUserInfo.js
    |   |-- integration // Integration tests
    |   |   |-- authController.test.js
    |   |-- unit // Unit tests
    |-- utils // Files containing utility functions
    |    |-- logger.js
    |-- .github
    |   |-- workflows
    |       |-- // Github actions files
    |-- .gitignore
    |-- .*rc, .*js, .*json, .*yml // config files for dependencies 
    |-- CONTRIBUTING.md
    |-- README.md
    |-- app.js
    |-- firestore-private-key.json // Firestore key file
    |-- package-lock.json
    |-- package.json
    |-- server.js // Contains server start logic

```

## Generating Authentication Token
- Navigate to `https://github.com/login/oauth/authorize?client_id=<GITHUB_CLIENT_ID>`
- Authorize the application.
- Copy the response cookie named `rds-session` from the redirected request from the API.
- Use the cookie for authenticated routes in the API.
- For non-production environments, authentication is also supported with the `Authorization` header.
- Authorization header: `Authorization: Bearer <token>`

## Pull request guidelines
- Ensure that the tests pass locally before raising a PR.
- All pull requests should be to the develop branch. 
- Every pull request should have associated issue(s) on our [issue tracker](https://github.com/Real-Dev-Squad/website-backend/issues).
- For any non-trivial fixes and features, unit and integration tests must be added. The PR reviewer should not approve/merge PR(s) that lack these.
- The PR(s) should be merged only after the CI passes.

