# Capstone Project - DevCTraining with Andela - Teamwork

This is our high-quality team API. You can use this API to request edit and delete articles and gifs for the teamwork app

<hr />

## Auth API

### POST /auth/signin

```endpoint
POST /api/v1/auth/signin
```

Employee/ Admin can signin and get back token

#### Example request

```javascript
require('axios');
const postData = {
  email: 'email216.43518328052647@gmail.com',
  password: 'password',
};
axios
  .post('https://capstone-project-teamwork.herokuapp.com/api/v1/auth/signin')
  .then(response => {
    // Action on success
  })
  .catch(error => {
    // Action on error
  });
```

#### Example response

```javascript
{
    "status": "success",
    "data": {
        "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjUwLCJpYXQiOjE1NzM1MjQwNTIwMjV9.wTMED93IC8jtm3NHJEJ1bPDUcIBjoVS3UTXiOFrT670",
        "userId": 50
    }
}
```

<hr />

### POST /auth/create-user

```endpoint
POST /api/v1/auth/create-user
```

**admin** can create a user

> _This api requires an authorization token_

#### Example request

```javascript
require('axios');

const config = {
  Authorization:
    'Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjUwLCJpYXQiOjE1NzM1MjQwNTIwMjV9.wTMED93IC8jtm3NHJEJ1bPDUcIBjoVS3UTXiOFrT670',
};
const postData = {
  email: 'newemail232@gmail.com', // required
  password: 'password', // optional
  jobRole: 'employee', // required; valid options: admin | employee,
  address: 'Thika Road 484 Plaza', // optional
  gender: 'M', // optional; valid options: M | F
};

axios
  .post(
    'https://capstone-project-teamwork.herokuapp.com/api/v1/auth/create-user',
    postData,
    config,
  )
  .then(response => {
    // Action on success
  })
  .catch(error => {
    // Action on error
  });
```

#### Example response

```javascript
{
    "status": "success",
    "message": "User successfully created",
    "data": {
        "userId": 204,
        "email": 'newemail232@gmail.com',
        "jobRole": 'employee',
        "address": 'Thika Road 484 Plaza',
        "gender": 'M'
    }
}
```

<hr />

## Feeds Api

### POST /feed

```endpoint
POST /api/v1/feed
```

Employee/ Admin can get back a articles/gifs starting from the most recent

> _This api requires an authorization token_

#### Example request

```javascript
require('axios');
const config = {
  Authorization:
    'Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjUwLCJpYXQiOjE1NzM1MjQwNTIwMjV9.wTMED93IC8jtm3NHJEJ1bPDUcIBjoVS3UTXiOFrT670',
};

axios
  .post('https://capstone-project-teamwork.herokuapp.com/api/v1/feed', config)
  .then(response => {
    // Action on success
  })
  .catch(error => {
    // Action on error
  });
```

#### Example response

```javascript
{
    "status": "success",
    "message": "Feed successfully rethrieved",
    "data": [
        {
            "articleId": 608,
            "gifid": null,
            "title": "Some Title",
            "article": "article",
            "url": null,
            "createdOn": "2019-11-11T09:55:25.499Z"
        },
        {
            "articleId": 607,
            "gifid": null,
            "title": "tile",
            "article": "article",
            "url": null,
            "createdOn": "2019-11-11T09:55:23.465Z"
        },
        {
            "articleId": null,
            "gifid": 316,
            "title": "Some gif title",
            "article": null,
            "url": "http://res.cloudinary.com/owenkelvin/image/upload/v1573321232/teamwork/",
            "createdOn": "2019-11-10T20:42:03.953Z"
        },
    ]
}
```

<hr />

## Articles API

### POST /articles

```endpoint
POST /api/v1/articles
```

Employee/ Admin can post articles

> _This api requires an authorization token_

#### Example request

```javascript
require('axios');
const config = {
  Authorization:
    'Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjUwLCJpYXQiOjE1NzM1MjQwNTIwMjV9.wTMED93IC8jtm3NHJEJ1bPDUcIBjoVS3UTXiOFrT670',
};
const postData = {
    title: 'Some Title',
    article: 'another short article'
};

axios
  .post(
    'https://capstone-project-teamwork.herokuapp.com/api/v1/articles', postData,
    config,
  )
  .then(response => {
    // Action on success
  })
  .catch(error => {
    // Action on error
  });
```

#### Example response

```javascript
{
    "status": "success",
    "message": "Artical successfully posted",
    "data": {
        "articleId": 629,
        "title": "Some Title",
        "article": "another short article",
        "createdOn": "2019-11-11T09:55:25.499Z"
    }
}
```

### PATCH /articles/:articleId

```endpoint
PATCH /api/v1/articles/:articleId
```

Employee/ Admin can edit articles

> _This api requires an authorization token_

#### Example request

```javascript
require('axios');
const config = {
  Authorization:
    'Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjUwLCJpYXQiOjE1NzM1MjQwNTIwMjV9.wTMED93IC8jtm3NHJEJ1bPDUcIBjoVS3UTXiOFrT670',
};
const postData = {
    title: 'Some Title',
    article: 'another short article'
};

axios
  .patch(
    'https://capstone-project-teamwork.herokuapp.com/api/v1/articles/625', postData,
    config,
  )
  .then(response => {
    // Action on success
  })
  .catch(error => {
    // Action on error
  });
```

#### Example response

```javascript
{
    "status": "success",
    "message": "Artical successfully updated",
    "data": {
        "articleId": 625,
        "title": "Some Title",
        "article": "another short article",
        "createdOn": "2019-11-11T09:55:25.499Z"
    }
}
```

<hr />
