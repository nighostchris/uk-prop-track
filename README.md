# uk-prop-track

Main goal of the project

1. Track the available amount of properties for rent in specified area

2. Track the average time for a property to change it's status from open for rent to let agreed

3. Generate report of analysis based on the point 1 and 2

4. Setup broadcasting channel in communication app, i.e. Telegram, Discord etc

## System Design

### Tools

- Database: We will start off with Postgres, then perform experiments on MongoDB, DynamoDB and ScyllaDB for educational purpose

- Cache: Redis

- Webserver: Echo

### Service Workflow

The whole service workflow will be outlined as follows

1. Upon service startup, setup connection to database, redis and initializing a web server

2. Setup cronjob to file queries to property listing sites like Rightmove periodically, retrieving the amount of properties for rent in specific area at the moment

3. Insert all properties that their ids have never existed in the database before

4. Setup cronjob to query property status on listing sites and record their let agreed time whenever there is a status change
