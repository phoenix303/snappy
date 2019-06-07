# Topcoder Submission API Wrapper

Wrapper library for Topcoder Submission API endpoint 

(Currently only `ReviewTypes` and `Reviews` are implemented)

## How to use this Wrapper

1. Include the wrapper in package.json as follows

    ```bash
    "topcoder-submission-api-wrapper": "topcoder-platform/topcoder-submission-api-wrapper.git"
    # If you want to use the local version
    "topcoder-submission-api-wrapper": "PATH_TO_DIRECTORY"
    ```

2. Create an instance of this wrapper with the configuration variables listed below

    ```bash
    const submissionApi = require('topcoder-submission-api-wrapper')
    const submissionApiClient = submissionApi(_.pick(config,
          ['AUTH0_URL', 'AUTH0_AUDIENCE', 'TOKEN_CACHE_TIME',
            'AUTH0_CLIENT_ID', 'AUTH0_CLIENT_SECRET', 'SUBMISSION_API_URL',
            'AUTH0_PROXY_SERVER_URL']))
    ```

    **Configuration / Environment variables:**

    - AUTH0_URL - the auth0 url
    - AUTH0_AUDIENCE - the auth0 audience
    - TOKEN_CACHE_TIME - (optional) the token cache time
    - AUTH0_CLIENT_ID - the auth0 client id, used as credential
    - AUTH0_CLIENT_SECRET - the auth0 client secret, used as credential
    - AUTH0_PROXY_SERVER_URL - (optional) the auth0 proxy server url
    - SUBMISSION_API_URL - Topcoder V5 Submission API URL. E.g. `https://api.topcoder-dev.com/v5`

3. Every function in this wrapper will return a promise, Handling promises is at the caller end. Call the functions with appropriate arguments

E.g.

```bash
let reviewTypeId = '8f4e8b6a-0ad2-4ff6-ab19-afeb102ff3b4'

submissionApiClient
  .createReviewType({ name: 'test-for-create', isActive: true })
  .then(result => console.log(result.body, result.status))
  .catch(err => console.log(err))

await submissionApiClient.deleteReviewType(reviewTypeId)
```

Refer `index.js` for the list of available wrapper functions

## Documentation wrapper methods

All URIs are relative to **SUBMISSION_API_URL** configuration variable.

### Review Types

Method | HTTP request | Description
------------- | ------------- | -------------
[**searchReviewTypes**](docs/ReviewTypesApi.md#searchReviewTypes) | **GET** /reviewTypes | Search review types.
[**headReviewTypes**](docs/ReviewTypesApi.md#headReviewTypes) | **HEAD** /reviewTypes | Same to search review types, but only response status and headers information return.
[**createReviewType**](docs/ReviewTypesApi.md#createReviewType) | **POST** /reviewTypes | Create a review type.
[**getReviewType**](docs/ReviewTypesApi.md#getReviewType) | **GET** /reviewTypes/{reviewTypeId} | Get the review type.
[**headReviewType**](docs/ReviewTypesApi.md#headReviewType) | **HEAD** /reviewTypes/{reviewTypeId} | Same to get review type, but only response status and headers information return.
[**updateReviewType**](docs/ReviewTypesApi.md#updateReviewType) | **PUT** /reviewTypes/{reviewTypeId} | Fully update review type.
[**patchReviewType**](docs/ReviewTypesApi.md#patchReviewType) | **PATCH** /reviewTypes/{reviewTypeId} | Partially update review type.
[**deleteReviewType**](docs/ReviewTypesApi.md#deleteReviewType) | **DELETE** /reviewTypes/{reviewTypeId} | Delete the review type.

### Reviews

| Method                                         | HTTP request                   | Description                                                  |
| ---------------------------------------------- | ------------------------------ | ------------------------------------------------------------ |
| [**getReviews**](ReviewsApi.md#getReviews)     | **GET** /reviews               | Get all reviews.                                             |
| [**headReviews**](ReviewsApi.md#headReviews)   | **HEAD** /reviews              | Get only response status and headers information but no response body for the endpoint. |
| [**createReview**](ReviewsApi.md#createReview) | **POST** /reviews              | Create a review.                                             |
| [**getReview**](ReviewsApi.md#getReview)       | **GET** /reviews/{reviewId}    | Get the review.                                              |
| [**headReview**](ReviewsApi.md#headReview)     | **HEAD** /reviews/{reviewId}   | Get only response status and headers information but no response body for the endpoint. |
| [**updateReview**](ReviewsApi.md#updateReview) | **PUT** /reviews/{reviewId}    | Fully update the review.                                     |
| [**patchReview**](ReviewsApi.md#patchReview)   | **PATCH** /reviews/{reviewId}  | Partially update the review.                                 |
| [**deleteReview**](ReviewsApi.md#deleteReview) | **DELETE** /reviews/{reviewId} | Delete the review.                                           |

## Authorization

Review Types wrapper internally generates a **JWT token using Auth0 credentials** and pass it in the `Authorization` header.

## Running tests

Following environment variables need to be set up before running the tests

```bash
- TEST_AUTH0_URL
- TEST_AUTH0_AUDIENCE
- TEST_AUTH0_CLIENT_ID
- TEST_AUTH0_CLIENT_SECRET
- TEST_SUBMISSION_API_URL
```

Refer to Step # 2 in [this section](#how-to-use-this-wrapper) to learn more about the configuration variables.

To run the tests alone, execute the command

```bash
npm run test
```

To run tests with coverage report, execute the command

```bash
npm run cov
```
