# Reviews Api

All URIs are relative to **SUBMISSION_API_URL** configuration variable.

Method | HTTP request | Description
------------- | ------------- | -------------
[**getReviews**](ReviewsApi.md#getReviews) | **GET** /reviews | Get all reviews. 
[**headReviews**](ReviewsApi.md#headReviews) | **HEAD** /reviews | Get only response status and headers information but no response body for the endpoint. 
[**createReview**](ReviewsApi.md#createReview) | **POST** /reviews | Create a review. 
[**getReview**](ReviewsApi.md#getReview) | **GET** /reviews/{reviewId} | Get the review. 
[**headReview**](ReviewsApi.md#headReview) | **HEAD** /reviews/{reviewId} | Get only response status and headers information but no response body for the endpoint. 
[**updateReview**](ReviewsApi.md#updateReview) | **PUT** /reviews/{reviewId} | Fully update the review. 
[**patchReview**](ReviewsApi.md#patchReview) | **PATCH** /reviews/{reviewId} | Partially update the review. 
[**deleteReview**](ReviewsApi.md#deleteReview) | **DELETE** /reviews/{reviewId} | Delete the review. 

<a name="getReviews"></a>

# **getReviews**
> getReviews(reqQuery)

Get reviews. Link headers are sent back and they have rel set to prev, next, first, last and contain the relevant URL.

### Example
```javascript
const submissionApi = require('topcoder-submission-api-wrapper')
const submissionApiClient = submissionApi(_.pick(config,
      ['AUTH0_URL', 'AUTH0_AUDIENCE', 'TOKEN_CACHE_TIME',
        'AUTH0_CLIENT_ID', 'AUTH0_CLIENT_SECRET', 'SUBMISSION_API_URL',
        'AUTH0_PROXY_SERVER_URL']))

const reqQuery = {
  page: 1,
  perPage: 3,
  score: 95.5,
  typeId: 'a12bc180-65ab-42ec-a945-5fd21dec1567',
  reviewerId: 'a12bc280-65ab-42ec-a945-5fd21dec1567',
  scoreCardId: 'a12bd180-65ab-42ec-a945-5fd21dec1567',
  submissionId: '48555121-73ba-416d-b139-ee3646aef988'
}

// Promise model
submissionApiClient
  .getReviews(reqQuery)
  .then(result => console.log(result.body, result.status))
  .catch(err => console.log(err))

// Async / await model
await submissionApiClient.getReviews(reqQuery)
```

### Parameters

Name | Type | Description
------------- | ------------- | -------------
 **reqQuery** | [**ReviewCriteria**](ReviewCriteria.md) | the criteria for reviews 

### Return type

Array of [**ReviewType**](ReviewType.md)

### Authorization

[Bearer](../README.md#authorization)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

<a name="headReviews"></a>

# **headReviews**
> headReviews(reqQuery)

Get only response status and headers information but no response body for the endpoint.

### Example
```javascript
const submissionApi = require('topcoder-submission-api-wrapper')
const submissionApiClient = submissionApi(_.pick(config,
      ['AUTH0_URL', 'AUTH0_AUDIENCE', 'TOKEN_CACHE_TIME',
        'AUTH0_CLIENT_ID', 'AUTH0_CLIENT_SECRET', 'SUBMISSION_API_URL',
        'AUTH0_PROXY_SERVER_URL']))

const reqQuery = {
  page: 1,
  perPage: 3,
  score: 95.5,
  typeId: 'a12bc180-65ab-42ec-a945-5fd21dec1567',
  reviewerId: 'a12bc280-65ab-42ec-a945-5fd21dec1567',
  scoreCardId: 'a12bd180-65ab-42ec-a945-5fd21dec1567',
  submissionId: '48555121-73ba-416d-b139-ee3646aef988'
}

// Promise model
submissionApiClient
  .headReviews(reqQuery)
  .then(result => console.log(result.status))
  .catch(err => console.log(err))

// Async / await model
await submissionApiClient.headReviews(reqQuery)
```

### Parameters

Name | Type | Description
------------- | ------------- | -------------
 **reqQuery** | [**ReviewCriteria**](ReviewCriteria.md) | the criteria for reviews 

### Return type

null (empty response body)

### Authorization

[Bearer](../README.md#authorization)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

<a name="createReview"></a>

# **createReview**
> createReview(reqBody)

Create a review.

### Example
```javascript
const submissionApi = require('topcoder-submission-api-wrapper')
const submissionApiClient = submissionApi(_.pick(config,
      ['AUTH0_URL', 'AUTH0_AUDIENCE', 'TOKEN_CACHE_TIME',
        'AUTH0_CLIENT_ID', 'AUTH0_CLIENT_SECRET', 'SUBMISSION_API_URL',
        'AUTH0_PROXY_SERVER_URL']))

const reqBody = {
  score: 95.5,
  typeId: 'a12bc180-65ab-42ec-a945-5fd21dec1567',
  reviewerId: 'a12bc280-65ab-42ec-a945-5fd21dec1567',
  scoreCardId: 'a12bd180-65ab-42ec-a945-5fd21dec1567',
  submissionId: '48555121-73ba-416d-b139-ee3646aef988'
}

// Promise model
submissionApiClient
  .createReview(reqBody)
  .then(result => console.log(result.body, result.status))
  .catch(err => console.log(err))

// Async / await model
await submissionApiClient.createReview(reqBody)
```

### Parameters

Name | Type | Description
------------- | ------------- | -------------
 **reqBody** | [**ReviewData**](ReviewData.md) | the review data 

### Return type

[**Review**](Review.md)

### Authorization

[Bearer](../README.md#authorization)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

<a name="getReview"></a>

# **getReview**
> getReview(reviewId)

Get the review by id.

### Example
```javascript
const submissionApi = require('topcoder-submission-api-wrapper')
const submissionApiClient = submissionApi(_.pick(config,
      ['AUTH0_URL', 'AUTH0_AUDIENCE', 'TOKEN_CACHE_TIME',
        'AUTH0_CLIENT_ID', 'AUTH0_CLIENT_SECRET', 'SUBMISSION_API_URL',
        'AUTH0_PROXY_SERVER_URL']))

let reviewId = '8f4e8b6a-0ad2-4ff6-ab19-afeb102ff3b4'

// Promise model
submissionApiClient
  .getReview(reviewId)
  .then(result => console.log(result.body, result.status))
  .catch(err => console.log(err))

// Async / await model
await submissionApiClient.getReview(reviewId)
```
### Parameters

Name | Type | Description
------------- | ------------- | -------------
 **reviewId** | String | the review id 

### Return type

[**Review**](Review.md)

### Authorization

[Bearer](../README.md#authorization)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

<a name="headReview"></a>

# **headReview**
> headReview(reviewId)

Get only response status and headers information but no response body for the endpoint.

### Example
```javascript
const submissionApi = require('topcoder-submission-api-wrapper')
const submissionApiClient = submissionApi(_.pick(config,
      ['AUTH0_URL', 'AUTH0_AUDIENCE', 'TOKEN_CACHE_TIME',
        'AUTH0_CLIENT_ID', 'AUTH0_CLIENT_SECRET', 'SUBMISSION_API_URL',
        'AUTH0_PROXY_SERVER_URL']))

let reviewId = '8f4e8b6a-0ad2-4ff6-ab19-afeb102ff3b4'

// Promise model
submissionApiClient
  .headReview(reviewId)
  .then(result => console.log(result.status))
  .catch(err => console.log(err))

// Async / await model
await submissionApiClient.headReview(reviewId)
```

### Parameters

Name | Type | Description
------------- | ------------- | -------------
 **reviewId** | String | the review id 

### Return type

[**Review**](Review.md)

### Authorization

[Bearer](../README.md#authorization)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

<a name="updateReview"></a>

# **updateReview**
> updateReview(reviewId, reqBody)

Fully update review.

### Example
```javascript
const submissionApi = require('topcoder-submission-api-wrapper')
const submissionApiClient = submissionApi(_.pick(config,
      ['AUTH0_URL', 'AUTH0_AUDIENCE', 'TOKEN_CACHE_TIME',
        'AUTH0_CLIENT_ID', 'AUTH0_CLIENT_SECRET', 'SUBMISSION_API_URL',
        'AUTH0_PROXY_SERVER_URL']))

let reviewId = '8f4e8b6a-0ad2-4ff6-ab19-afeb102ff3b4'
const reqBody = {
  score: 99.5,
  typeId: 'a12bc180-65ab-42ec-a945-5fd21dec1567',
  reviewerId: 'a12bc280-65ab-42ec-a945-5fd21dec1567',
  scoreCardId: 'a12bd180-65ab-42ec-a945-5fd21dec1567',
  submissionId: '48555121-73ba-416d-b139-ee3646aef988'
}

// Promise model
submissionApiClient
  .updateReview(reviewId, reqBody)
  .then(result => console.log(result.body, result.status))
  .catch(err => console.log(err))

// Async / await model
await submissionApiClient.updateReview(reviewId, reqBody)
```

### Parameters

Name | Type | Description
------------- | ------------- | -------------
 **reviewId** | String | the review id 
 **reqBody** | [**ReviewData**](ReviewData.md) | the review data 

### Return type

[**Review**](Review.md)

### Authorization

[Bearer](../README.md#authorization)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

<a name="patchReview"></a>

# **patchReview**
> patchReview(reviewId, reqBody)

Partially update review.

### Example
```javascript
const submissionApi = require('topcoder-submission-api-wrapper')
const submissionApiClient = submissionApi(_.pick(config,
      ['AUTH0_URL', 'AUTH0_AUDIENCE', 'TOKEN_CACHE_TIME',
        'AUTH0_CLIENT_ID', 'AUTH0_CLIENT_SECRET', 'SUBMISSION_API_URL',
        'AUTH0_PROXY_SERVER_URL']))

let reviewId = '8f4e8b6a-0ad2-4ff6-ab19-afeb102ff3b4'
const reqBody = {
  score: 90.5
}

// Promise model
submissionApiClient
  .patchReview(reviewId, reqBody)
  .then(result => console.log(result.body, result.status))
  .catch(err => console.log(err))

// Async / await model
await submissionApiClient.patchReview(reviewId, reqBody)
```

### Parameters

Name | Type | Description
------------- | ------------- | -------------
 **reviewId** | String | the review id 
 **reqBody** | [**ReviewData**](ReviewData.md) | the review data 

### Return type

[**Review**](Review.md)

### Authorization

[Bearer](../README.md#authorization)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

<a name="deleteReview"></a>

# **deleteReview**
> deleteReview(reviewId)

Delete review by id.

### Example
```javascript
const submissionApi = require('topcoder-submission-api-wrapper')
const submissionApiClient = submissionApi(_.pick(config,
      ['AUTH0_URL', 'AUTH0_AUDIENCE', 'TOKEN_CACHE_TIME',
        'AUTH0_CLIENT_ID', 'AUTH0_CLIENT_SECRET', 'SUBMISSION_API_URL',
        'AUTH0_PROXY_SERVER_URL']))

let reviewId = '8f4e8b6a-0ad2-4ff6-ab19-afeb102ff3b4'

// Promise model
submissionApiClient
  .deleteReview(reviewId)
  .then(result => console.log(result.status))
  .catch(err => console.log(err))

// Async / await model
await submissionApiClient.deleteReview(reviewId)
```

### Parameters

Name | Type | Description
------------- | ------------- | -------------
 **reviewId** | String | the review id 

### Return type

null (empty response body)

### Authorization

[Bearer](../README.md#authorization)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json
