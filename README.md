# Make your own portfolio!
This challenge assume that there is a server hosted by [Heroku](https://heroku.com).
Please [make a new application](https://dashboard.heroku.com/new) for this challenge in Heroku.

## Database
Information for this challenge is specified in below.
It is also provided in [database.sql](./specifications/database.sql) file.

```sql
-- This file is formatted based on SQLite3's syntax
-- Some small fixes might be needed to use in other database.
create table projects (
    id integer PRIMARY KEY AUTOINCREMENT,
    url varchar(255) NULL,
    title varchar(255) NOT NULL,
    description text NOT NULL,
    created_at datetime NOT NULL DEFAULT CURRENT_TIMESTAMP
  );
```

## Step 1: Edit account.json
Open [account.json](./account.json) and edit the value for `heroku_appname` to the application that you have hosted.

```json
{
  "heroku_appname": "<App Name>"
}
```
Replace `<App Name>`, including `<` and `>`, to your application name.

## Step 2: Implement your server and check with Test!
We require to implement 4 endpoints. All details of specifications are written in files with format of [api-first-spec](https://github.com/shunjikonishi/api-first-spec).

- GET /api/projects
  - Return `200 OK` status code when server succeed to get data
  - [GET /api/projects spec](./specifications/localhost/GET-api-projects.spec.js)
- POST /api/projects
  - Return `400 BadRequest` when either of title or description was empty
  - Return `200 OK` when server succeed to create new data
  - [POST /api/projects spec](./specifications/localhost/POST-api-projects.spec.js)
- GET /api/projects/:id
  - Return `200 OK` when found data
  - Return `404 NotFound` when data didn't exists
  - [GET /api/projects/:id spec](./specifications/localhost/GET-api-projects_id.spec.js)
- DELETE /api/projects/:id
  - Return `200 OK` when data was successfully deleted
  - Return `404 NofFound` when data didn't exists
  - [GET /api/projects/:id spec](./specifications/localhost/DELETE-api-projects_id.spec.js)

### Run Test
To test your API server in local environment, run commands in below.

```bash
$ npm install                               # Install modules (You need run this at first time)
$ $(npm bin)/mocha specifications/localhost # Run Test in local
```

Make all test status as `passing`; there are several failing tests at beginning.

```
42 passing (16s)
6 failing
```

## Step 3: Hack as you want!
As long as our tests pass, it is free to hack in your own way! Please write features that you add and your thoughts about why / how you add that features to [answer.md](./answer.md).

If you are back-end developer, adding validation, new parameter, or implement new endpoints would be a good option to show your skills.
For front-end developer, implement front page using the API that you have implemented.
