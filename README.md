# Topcoder - MM Final Score Processor

### Dependencies

- nodejs https://nodejs.org/en/ (v10+)
- Kafka
- Docker, Docker Compose (Only for deployment with Docker)

## Configuration

Configuration of the MM Final Score Processor is at `config/default.js`.
The following parameters can be set in config files or in env variables:

- LOG_LEVEL: the log level; default value: 'debug'
- KAFKA_URL: comma separated Kafka hosts; default value: 'localhost:9092'
- KAFKA_CLIENT_CERT: Kafka connection certificate, optional; default value is undefined;
    if not provided, then SSL connection is not used, direct insecure connection is used;
    if provided, it can be either path to certificate file or certificate content
- KAFKA_CLIENT_CERT_KEY: Kafka connection private key, optional; default value is undefined;
    if not provided, then SSL connection is not used, direct insecure connection is used;
    if provided, it can be either path to private key file or private key content
- KAFKA_GROUP_ID: Kafka group id, default value is 'mm-final-score-processor'
- KAFKA_ERROR_TOPIC: Error topic in Kafka to which error message need to be posted
- TOPIC_NAME - Topic name to post to bus API, default value is 'submission.notification.score'
- ORIGINATOR - Originator to post to bus API, default value is 'MMFinalScoreProcessor'
- BUSAPI_URL - Bus API URL, default value is 'https://api.topcoder-dev.com/v5'
- AUTOPILOT_EVENT_TOPIC: Auto Pilot event Kafka topic, default value is 'notifications.autopilot.events'
- SUBMISSION_API_URL: The Submission API URL, default value is 'https://api.topcoder-dev.com/v5/submissions'
- CHALLENGE_API_URL: The Challenge API URL, default value is 'https://api.topcoder-dev.com/v4/challenges'
- AUTH0_URL: Auth0 URL, used to get TC M2M token
- AUTH0_AUDIENCE: Auth0 audience, used to get TC M2M token
- TOKEN_CACHE_TIME: Auth0 token cache time, used to get TC M2M token
- AUTH0_CLIENT_ID: Auth0 client id, used to get TC M2M token
- AUTH0_CLIENT_SECRET: Auth0 client secret, used to get TC M2M token
- TEST_TYPE: Test type, default value is 'system'
- CHALLENGE_SUBTRACK: Challenge subtrack, default value is 'MARATHON_MATCH, DEVELOP_MARATHON_MATCH'
- SCORER_REVIEW_TYPE_ID: The scorer review type ID

In order to properly get TC M2M token, the AUTH0_URL, AUTH0_CLIENT_ID and AUTH0_CLIENT_SECRET must be set properly, e.g.
export AUTH0_URL="<Auth0 URL>"
export AUTH0_CLIENT_ID="<Auth0 Client ID>"
export AUTH0_CLIENT_SECRET="<Auth0 Client Secret>"

## Local Kafka setup

- `http://kafka.apache.org/quickstart` contains details to setup and manage Kafka server,
  below provides details to setup Kafka server in Mac, Windows will use bat commands in bin/windows instead
- download kafka at `https://www.apache.org/dyn/closer.cgi?path=/kafka/1.1.0/kafka_2.11-1.1.0.tgz`
- extract out the downloaded tgz file
- go to the extracted directory kafka_2.11-0.11.0.1
- start ZooKeeper server:
  `bin/zookeeper-server-start.sh config/zookeeper.properties`
- use another terminal, go to same directory, start the Kafka server:
  `bin/kafka-server-start.sh config/server.properties`
- note that the zookeeper server is at localhost:2181, and Kafka server is at localhost:9092
- use another terminal, go to same directory, create topic:
```  
  bin/kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic notifications.autopilot.events
```
- verify that the topic is created:
  `bin/kafka-topics.sh --list --zookeeper localhost:2181`,
  it should list out the created topics
- run the producer and then write some message into the console to send to the topic `notifications.autopilot.events`:
  `bin/kafka-console-producer.sh --broker-list localhost:9092 --topic notifications.autopilot.events`
- In the console, write some message, one message per line:
E.g.
```
  { "topic": "notifications.autopilot.events", "payload": { "projectId": 30054682, "phaseTypeName": "Review", "state": "START" } }
```
- optionally, use another terminal, go to same directory, start a consumer to view the messages:
```
  bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic notifications.autopilot.events --from-beginning
```

## Local deployment

1. From the project root directory, run the following command to install the dependencies

```
npm i
```

2. To run linters if required

```
npm run lint

npm run lint:fix # To fix possible lint errors
```

3. Start the processor

```
npm start
```

## Local Deployment with Docker

To run the MM Final Score Processor using docker, follow the below steps

1. Navigate to the directory `docker`

2. Once that is done, run the following command

```
docker-compose up
```

3. When you are running the application for the first time, It will take some time initially to download the image and install the dependencies

## Unit and E2E tests

Variables related to tests is present in `config/test.js`

1. TEST_KAFKA_URL - Kafka URL to be used for tests, this could be different from the Kafka instance used for development
2. TEST_SCORER_REVIEW_TYPE_ID - Scorer review type ID, default is 1
3. WAIT_TIME - wait time used in test, default is 1500 or 1.5 second

#### Running unit tests and coverage

To run unit tests alone

```
npm run test
```

To run unit tests with coverage report

```
npm run cov
```

#### Running E2E tests and coverage

To run e2e tests alone

```
npm run e2e
```

To run e2e tests with coverage report

```
npm run cov-e2e
```

## Verification

1. Ensure that Kafka is up and running and the topic `notifications.autopilot.events` are created in Kafka

2. Attach to the topic `notifications.autopilot.events` using Kafka console producer

```
bin/kafka-console-producer.sh --broker-list localhost:9092 --topic notifications.autopilot.events
```

3. Write the following message to the Console

```
{ "topic": "notifications.autopilot.events", "payload": { "projectId": 30054682, "phaseTypeName": "Review", "state": "START" } }
```

4. Some other payload for testing

```
## For the below challenge, scorecardId will be fetched from Challenge API

{ "topic": "notifications.autopilot.events", "payload": { "projectId": 30054682, "phaseTypeName": "Review", "state": "START" } }


## Below payloads will be ignored because only Appeals Response end will be processed

{ "topic": "notifications.autopilot.events", "payload": { "projectId": 30054682, "phaseTypeName": "Appeals Response", "state": "START" } }

{ "topic": "notifications.autopilot.events", "payload": { "projectId": 30054682, "phaseTypeName": "Review", "state": "END" } }
```
