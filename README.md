# Review Summations Api

All URIs are relative to **SUBMISSION_API_URL** configuration variable.

Method | HTTP request | Description
------------- | ------------- | -------------
[**searchReviewSummations**](ReviewSummationsApi.md#searchReviewSummations) | **GET** /reviewSummations | Search review summations.
[**headReviewSummations**](ReviewSummationsApi.md#headReviews) | **HEAD** /reviewSummations | Same to search review summations, but only response status and headers information return.
[**createReviewSummation**](ReviewSummationsApi.md#createReview) | **POST** /reviewSummations | Create a review summation.
[**getReviewSummation**](ReviewSummationsApi.md#getReview) | **GET** /reviewSummations/{reviewSummationId} | Get the review summation.
[**headReviewSummation**](ReviewSummationsApi.md#headReview) | **HEAD** /reviewSummations/{reviewSummationId} | Same to get review summation, but only response status and headers information return.
[**updateReviewSummation**](ReviewSummationsApi.md#updateReview) | **PUT** /reviewSummations/{reviewSummationId} | Fully update review summation.
[**patchReviewSummation**](ReviewSummationsApi.md#patchReview) | **PATCH** /reviewSummations/{reviewSummationId} | Partially update review summation.
[**deleteReviewSummation**](ReviewSummationsApi.md#deleteReview) | **DELETE** /reviewSummations/{reviewSummationId} | Delete the review summation.

<a name="searchReviewSummations"></a>
# **searchReviewSummations**
> searchReviewSummations(reqQuery)

Search review summations. Link headers are sent back and they have rel set to prev, next, first, last and contain the relevant URL.

### Example
```javascript
const submissionApi = require('tc-submission-api-wrapper')
const submissionApiClient = submissionApi(_.pick(config,
      ['AUTH0_URL', 'AUTH0_AUDIENCE', 'TOKEN_CACHE_TIME',
        'AUTH0_CLIENT_ID', 'AUTH0_CLIENT_SECRET', 'SUBMISSION_API_URL',
        'AUTH0_PROXY_SERVER_URL']))

const reqQuery = {
  page: 1,
  perPage: 10,
  submissionId: '16883c9e-50e0-4388-b7ac-52d66aded166',
  aggregateScore: 90,
  scoreCardId: 30001101,
  isPassing: true
}

// Promise model
submissionApiClient
  .searchReviewSummations(reqQuery)
  .then(result => console.log(result.body, result.status))
  .catch(err => console.log(err))

// Async / await model
await submissionApiClient.searchReviewSummations(reqQuery)
```

### Parameters

Name | Type | Description
------------- | ------------- | -------------
 **reqQuery** | [**SearchSummationsCriteria**](SearchSummationsCriteria.md)| the search summations criteria

### Return type

Array of [**ReviewSummation**](ReviewSummation.md)

### Authorization

[Bearer](../README.md#authorization)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

<a name="headReviewSummations"></a>
# **headReviewSummations**
> headReviewSummations(reqQuery)

Same to search review summations, but only response status and headers information return.

### Example
```javascript
const submissionApi = require('tc-submission-api-wrapper')
const submissionApiClient = submissionApi(_.pick(config,
      ['AUTH0_URL', 'AUTH0_AUDIENCE', 'TOKEN_CACHE_TIME',
        'AUTH0_CLIENT_ID', 'AUTH0_CLIENT_SECRET', 'SUBMISSION_API_URL',
        'AUTH0_PROXY_SERVER_URL']))

const reqQuery = {
  page: 1,
  perPage: 10,
  submissionId: '16883c9e-50e0-4388-b7ac-52d66aded166',
  aggregateScore: 90,
  scoreCardId: 30001101,
  isPassing: true
}

// Promise model
submissionApiClient
  .headReviewSummations(reqQuery)
  .then(result => console.log(result.status))
  .catch(err => console.log(err))

// Async / await model
await submissionApiClient.headReviewSummations(reqQuery)
```

### Parameters

Name | Type | Description
------------- | ------------- | -------------
 **reqQuery** | [**SearchSummationsCriteria**](SearchSummationsCriteria.md)| the search criteria

### Return type

null (empty response body)

### Authorization

[Bearer](../README.md#authorization)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

<a name="createReviewSummation"></a>
# **createReviewSummation**
> createReviewSummation(reqBody)

Create a review summation.

### Example
```javascript
const submissionApi = require('tc-submission-api-wrapper')
const submissionApiClient = submissionApi(_.pick(config,
      ['AUTH0_URL', 'AUTH0_AUDIENCE', 'TOKEN_CACHE_TIME',
        'AUTH0_CLIENT_ID', 'AUTH0_CLIENT_SECRET', 'SUBMISSION_API_URL',
        'AUTH0_PROXY_SERVER_URL']))

const reqBody = {
  submissionId: '16883c9e-50e0-4388-b7ac-52d66aded166',
  aggregateScore: 90,
  scoreCardId: 30001101,
  isPassing: true,
  metadata: { abc: 'def' }
}

// Promise model
submissionApiClient
  .createReviewSummation(reqBody)
  .then(result => console.log(result.body, result.status))
  .catch(err => console.log(err))

// Async / await model
await submissionApiClient.createReviewSummation(reqBody)
```

### Parameters

Name | Type | Description
------------- | ------------- | -------------
 **reqBody** | [**ReviewSummationData**](ReviewSummationData.md)| the review summation data

### Return type

[**ReviewSummation**](ReviewSummation.md)

### Authorization

[Bearer](../README.md#authorization)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

<a name="getReviewSummation"></a>
# **getReviewSummation**
> getReviewSummation(reviewSummationId)

Get the review summation by id.

### Example
```javascript
const submissionApi = require('tc-submission-api-wrapper')
const submissionApiClient = submissionApi(_.pick(config,
      ['AUTH0_URL', 'AUTH0_AUDIENCE', 'TOKEN_CACHE_TIME',
        'AUTH0_CLIENT_ID', 'AUTH0_CLIENT_SECRET', 'SUBMISSION_API_URL',
        'AUTH0_PROXY_SERVER_URL']))

const reviewSummationId = '4cdce3cf-a9e9-4f29-bfe8-a0139a159fa8'

// Promise model
submissionApiClient
  .getReviewSummation(reviewSummationId)
  .then(result => console.log(result.body, result.status))
  .catch(err => console.log(err))

// Async / await model
await submissionApiClient.getReviewSummation(reviewSummationId)
```
### Parameters

Name | Type | Description
------------- | ------------- | -------------
 **reviewSummationId** | String | the review summation id

### Return type

[**ReviewSummation**](ReviewSummation.md)

### Authorization

[Bearer](../README.md#authorization)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

<a name="headReviewSummation"></a>
# **headReviewSummation**
> headReviewSummation(reviewSummationId)

Same to get review summation, but only response status and headers information return.

### Example
```javascript
const submissionApi = require('tc-submission-api-wrapper')
const submissionApiClient = submissionApi(_.pick(config,
      ['AUTH0_URL', 'AUTH0_AUDIENCE', 'TOKEN_CACHE_TIME',
        'AUTH0_CLIENT_ID', 'AUTH0_CLIENT_SECRET', 'SUBMISSION_API_URL',
        'AUTH0_PROXY_SERVER_URL']))

const reviewSummationId = '4cdce3cf-a9e9-4f29-bfe8-a0139a159fa8'

// Promise model
submissionApiClient
  .headReviewSummation(reviewSummationId)
  .then(result => console.log(result.status))
  .catch(err => console.log(err))

// Async / await model
await submissionApiClient.headReviewSummation(reviewSummationId)
```

### Parameters

Name | Type | Description
------------- | ------------- | -------------
 **reviewSummationId** | String | the review summation id

### Return type

null (empty response body)

### Authorization

[Bearer](../README.md#authorization)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

<a name="updateReviewSummation"></a>
# **updateReviewSummation**
> updateReviewSummation(reviewSummationId, reqBody)

Fully update review summation.

### Example
```javascript
const submissionApi = require('tc-submission-api-wrapper')
const submissionApiClient = submissionApi(_.pick(config,
      ['AUTH0_URL', 'AUTH0_AUDIENCE', 'TOKEN_CACHE_TIME',
        'AUTH0_CLIENT_ID', 'AUTH0_CLIENT_SECRET', 'SUBMISSION_API_URL',
        'AUTH0_PROXY_SERVER_URL']))

const reviewSummationId = '4cdce3cf-a9e9-4f29-bfe8-a0139a159fa8'
const reqBody = {
  submissionId: '16883c9e-50e0-4388-b7ac-52d66aded166',
  aggregateScore: 90,
  scoreCardId: 30001101,
  isPassing: true,
  metadata: { abc: 'def' }
}

// Promise model
submissionApiClient
  .updateReviewSummation(reviewSummationId, reqBody)
  .then(result => console.log(result.body, result.status))
  .catch(err => console.log(err))

// Async / await model
await submissionApiClient.updateReviewSummation(reviewSummationId, reqBody)
```

### Parameters

Name | Type | Description
------------- | ------------- | -------------
 **reviewSummationId** | String | the review summation id
 **reqBody** | [**ReviewSummationData**](ReviewSummationData.md)| the review summation data

### Return type

[**ReviewSummation**](ReviewSummation.md)

### Authorization

[Bearer](../README.md#authorization)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

<a name="patchReviewSummation"></a>
# **patchReviewSummation**
> patchReviewSummation(reviewSummationId, reqBody)

Partially update review summation.

### Example
```javascript
const submissionApi = require('tc-submission-api-wrapper')
const submissionApiClient = submissionApi(_.pick(config,
      ['AUTH0_URL', 'AUTH0_AUDIENCE', 'TOKEN_CACHE_TIME',
        'AUTH0_CLIENT_ID', 'AUTH0_CLIENT_SECRET', 'SUBMISSION_API_URL',
        'AUTH0_PROXY_SERVER_URL']))

const reviewSummationId = '4cdce3cf-a9e9-4f29-bfe8-a0139a159fa8'
const reqBody = {
  submissionId: '16883c9e-50e0-4388-b7ac-52d66aded166',
  aggregateScore: 90,
  scoreCardId: 30001101,
  isPassing: true,
  metadata: { abc: 'def' }
}

// Promise model
submissionApiClient
  .patchReviewSummation(reviewSummationId, reqBody)
  .then(result => console.log(result.body, result.status))
  .catch(err => console.log(err))

// Async / await model
await submissionApiClient.patchReviewSummation(reviewSummationId, reqBody)
```

### Parameters

Name | Type | Description
------------- | ------------- | -------------
 **reviewSummationId** | String | the review summation id
 **reqBody** | [**ReviewSummationData**](ReviewSummationData.md)| the review summation data

### Return type

[**ReviewSummation**](ReviewSummation.md)

### Authorization

[Bearer](../README.md#authorization)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

<a name="deleteReviewSummation"></a>
# **deleteReviewSummation**
> deleteReviewSummation(reviewSummationId)

Delete review summation by id.

### Example
```javascript
const submissionApi = require('tc-submission-api-wrapper')
const submissionApiClient = submissionApi(_.pick(config,
      ['AUTH0_URL', 'AUTH0_AUDIENCE', 'TOKEN_CACHE_TIME',
        'AUTH0_CLIENT_ID', 'AUTH0_CLIENT_SECRET', 'SUBMISSION_API_URL',
        'AUTH0_PROXY_SERVER_URL']))

const reviewSummationId = '4cdce3cf-a9e9-4f29-bfe8-a0139a159fa8'

// Promise model
submissionApiClient
  .deleteReviewSummation(reviewSummationId)
  .then(result => console.log(result.status))
  .catch(err => console.log(err))

// Async / await model
await submissionApiClient.deleteReviewSummation(reviewSummationId)
```

### Parameters

Name | Type | Description
------------- | ------------- | -------------
 **reviewSummationId** | String | the review summation id

### Return type

null (empty response body)

### Authorization

[Bearer](../README.md#authorization)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json
