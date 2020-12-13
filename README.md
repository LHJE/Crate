#### LABHAT presents:
# Crate

Crate, by LABHAT, is an updated version of an existing repo created by Turing School of Software and Design].  You can find the original repo [here](https://github.com/atulmy/crate), with a more robust description as to what the core repo is.

Our additions lay the groundwork to helping the user understand their personal style, and start receiving more personalized creates.

## Setup and Running
- Node installation:
  - Open the Terminal app and type brew update. This updates Homebrew with a list of the latest version of Node.
  - **Type `brew install node`.
  - **Type `brew update`.
  - **Type `brew update node`.

- Postgres installation:
  - Follow the instructions here: [https://postgresapp.com/](https://postgresapp.com/)
  - Add the following to your .bash_profile or (.zshrc if using zsh):
    ```
    export PATH="/Applications/Postgres.app/Contents/Versions/<your postgresql verson i.e. 12.3>/bin:$PATH"
    ```
  - Close or reload your terminal window
  - Type `which psql` in your terminal you should see the following output:
  ```
    /Applications/Postgres.app/Contents/Versions/latest/bin/psql
  ```
  - Type `psql` in your terminal to verify that your postgres CLI is working.
  - Clone repo `git clone git@github.com:atulmy/crate.git crate`

- Crate installation:
  - Switch to `code` directory `cd code`
  - Configurations
    - Type `psql` in your terminal to access the postgres command line interface (CLI)
    - Check your available postgres users by running `\du` in the postgres CLI.
    - Modify `/api/src/config/database.json` for database credentials.
      - Choose one of the names (“postgres” should be fine) to put as your username in the database.json.
      - If you followed the default installation instructions when install postgres you do not need a password. If you have a password created, add that to the database.json file.
    - Create your database locally by running `CREATE DATABASE crate;` in the postgres CLI;
  - Setup
    - API: Install packages and database setup (migrations and seed) `cd api` and `npm run setup`
    - Webapp: Install packages `cd web` and `npm install`
  - Development
    - Run API `cd api` and `npm start`, browse GraphiQL at http://localhost:8000/
    - Run Webapp `cd web` and `npm start`, browse webapp at http://localhost:3000/
  - Production
    - Run API `cd api` and `npm run start:prod`, creates an optimized build in `build` directory and runs the server
    - Run Webapp `cd web` and `npm run start:prod`, creates an optimized build in `build` directory and runs the server

- Database installation
  - Install Sequelize by running these on the command line
    - `npm install --save sequelize`
    - `npm install --save pg pg-hstore`
    - `yarn add sequelize`
  - Run on the command line, white in the `/api` folder, the following code to setup the database:
    - `sequelize init`
    - `sequelize db:create`
    - `sequelize db:migrate`
    - `sequelize db:seed:all`

### Common errors

When running `npm run setup` in the api directory:
```
ERROR:root:code for hash md5 was not found.
Traceback (most recent call last):
  File "/usr/local/Cellar/python@2/2.7.15/Frameworks/Python.framework/Versions/2.7/lib/python2.7/hashlib.py", line 147, in <module>
```

The cause could potentially be from switching to Catalina or bash moving to zshell.

Solution:

Run `ls /usr/local/Cellar/openssl` - This should display 1.0.2t (potentially 1.0.2r)

Based on that version run: `brew switch openssl 1.0.2t` or `brew switch openssl 1.0.2r`

Finally, run `python -c "import hashlib;m=hashlib.md5();print(m.hexdigest())"`

## Usage


## Contributing


## License
[MIT](https://choosealicense.com/licenses/mit/)
