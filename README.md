# allisone

The purpose of this website is to help people find and connect with each other. It aims to reduce the barriers that
separate humanity; to reduce the illusion of separation, and to reduce division, while perserving diversity.

Each person has a page. It has at a minimum, their first name and a single face picture. Other information can be entered later - and has privacy settings on it - allow only friends, allow only compatible ads to see this, allow everyone.

This information includes an 'About Me' paragraph and a list of interests. People can then create ads to search for either
friends, jobs, business partners, or romantic interests.

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.

### Installing

1. Ensure node, postgresql and yarn are installed. Since lerna is built on yarn, this uses yarn as the package manager. Node must be at least version 14

2. Clone GIT repository and download

```
git clone https://github.com/tomrembrown/allisone
cd allisone
```

3. Download and install packages in various directories, and copy files to create .env

```
yarn initial
```

4. Determine port postgres runs on

```
linux:  sudo netstat -plunt |grep postgres
or in psql terminal type \conninfo
```

5. Build PostgreSQL initial database, create user, and give user permissions

```
su - postgres (enter postgres user password)
psql --port (port determined for postgresql server)
OR psql -h localhost(or other host name) -U (user able to create databases) --port (port - if not default 5432)
CREATE DATABASE allisone;
CREATE ROLE one_computer_access WITH ENCRYPTED PASSWORD (enter password here in single quotes);
GRANT ALL PRIVILEGES ON DATABASE allisone TO one_computer_access;
ALTER ROLE "one_computer_access" WITH LOGIN;
CREATE EXTENSION IF NOT EXISTS citext WITH SCHEMA public;
\c allisone
CREATE EXTENSION IF NOT EXISTS citext;
```

6. Adjust parameters in .env as necessary (note .env files exist in root directory as well as database, client, and server)

7. Create the database tables

```
yarn run createTables (from root directory)
```

8. a) Development - For development mode, start the servers (command from root directory starts both react & express servers).

```
yarn run dev
```

8. b) Production - For production mode, first build the bundles

```
yarn run build
```

Second, for production, on the server, run the server using pm2 (process manager) using:

```
yarn run server
```

## Running the tests

Tests are not currently configured

### What the tests do

These tests handle linting with jshint, link checking, and some cross-page and unit tests.

## Built With

- [Node.JS](https://nodejs.org/) - JavaScript runtime that allows server-side JavaScript
- [Express](https://expressjs.com/) - Backend framework
- [PostgreSQL](https://www.postgresql.org/) - Database
- [Vue.js](https://v3.vuejs.org/) - Frontend framework

## Contributing

Please ask Tom Brown (tom@tomrembrown.com) if you would like to contribute to this project.

## Authors

- **Tom Brown**

## License

This project is using the MIT license - see the [LICENSE](LICENSE) file for details
