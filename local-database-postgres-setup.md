# Setup a Postgres database to use with strapi on development

## Requirement
- Postgresql
- Strapi v4

## Create database using psql

### Connect to postgres
`sudo -i -u postgres`

### use psql
`psql`

### Create user and login password
`CREATE USER <dbname> WITH LOGIN PASSWORD '<dbuser>';`

### Create database and attach his owner
`CREATE DATABASE <dbname> OWNER <dbuser>;`

### Show database list
> postgres=#`\l`

## Setup Strapi to use development database in `./config/database.js`

```js
module.exports = ({ env }) => ({
  connection: {
    client: 'postgres',
    connection: {
      host: env('DATABASE_HOST', 'localhost'),
      port: env.int('DATABASE_PORT', 5432),
      database: env('DATABASE_NAME', '<dbname>'),
      user: env('DATABASE_USERNAME', '<dbuser>'),
      password: env('DATABASE_PASSWORD', '<dbpass>'),
      schema: env('DATABASE_SCHEMA', 'public'), // Not required
      ssl: {
        rejectUnauthorized: env.bool('DATABASE_SSL_SELF', false),
      },
    },
    debug: false,
  },
});
```

