# Documentation

## Users

### Get authentication token

`POST /api/authToken`

#### Request body

| Name     | Type   | Description        |
| -------- | ------ | ------------------ |
| username | String | Username           |
| password | String | Plaintext Password |

### Check if user is authenticated

`POST /api/authenticate`

#### Request body

| Name  | Type   | Description                                       |
| ----- | ------ | ------------------------------------------------- |
| token | String | JWT token that was obtained from `/api/authToken` |

### Find user by username

`GET /api/users/:username`

#### Request parameters

| Name     | Type   | Description                      |
| -------- | ------ | -------------------------------- |
| username | String | Username of the user to be found |

### Add new user

`POST /api/users`

Saves a new user in the database. All user details are to be provided in the request body. The response status is set to `409 Conflict` if the username is already taken. `201 Created` is returned if the user is saved successfully.

### Get badges of a user

`GET /api/users/:username/badges`

#### Request parameters

| Name     | Type   | Description                      |
| -------- | ------ | -------------------------------- |
| username | String | Username of the user to be found |

### Get heart rate metrics of user

`GET /api/:username/metrics/heartRate`

#### Request parameters

| Name     | Type   | Description                      |
| -------- | ------ | -------------------------------- |
| username | String | Username of the user to be found |

### Get playgrounds the user has joined

`GET /api/:username/playgrounds`

#### Request parameters

| Name     | Type   | Description          |
| -------- | ------ | -------------------- |
| username | String | Username of the user |

### Award badge to user

`POST /api/:username/badges`

#### Request parameters

| Name     | Type   | Description          |
| -------- | ------ | -------------------- |
| username | String | Username of the user |

### Request body

| Name    | Type   | Description                   |
| ------- | ------ | ----------------------------- |
| badgeId | String | ID of the badge to be awarded |

## Badges

### Add new badge

`POST /api/badges`

#### Request body

| Name | Type   | Description     |
| ---- | ------ | --------------- |
| id   | String | ID of the badge |

### Find badge

`GET /api/badges/:id`

#### Request parameters

| Name | Type   | Description     |
| ---- | ------ | --------------- |
| id   | String | ID of the badge |

## Playgrounds

### Find playground by ID

`GET /api/playgrounds/:id`

`404 Not Found` is set as the status if the playground is not found.

#### Request parameters

| Name | Type   | Description          |
| ---- | ------ | -------------------- |
| id   | String | ID of the playground |

### Add new playground

`POST /api/playgrounds`

Saves a new playground in the database. All playground details are to be provided in the request body. The response status is set to `409 Conflict` if the id is already taken. `201 Created` is returned if the playground is saved successfully.

### Add user to playground

`POST /api/playgrounds/:id/users`

`201 Created` is returned if the user is successfully added.

#### Request parameters

| Name | Type   | Description          |
| ---- | ------ | -------------------- |
| id   | String | ID of the playground |

#### Request body

| Name   | Type   | Description                |
| ------ | ------ | -------------------------- |
| userId | String | ID of the user to be added |

### Get all users in playground

`GET /api/playgrounds/:id/users`

#### Request parameters

| Name | Type   | Description          |
| ---- | ------ | -------------------- |
| id   | String | ID of the playground |

### Get invite link

`GET /api/playgrounds/:id/inviteLink`

#### Request parameters

| Name | Type   | Description          |
| ---- | ------ | -------------------- |
| id   | String | ID of the playground |

### Add a user using invite link

`GET /api/playgrounds/inviteLink/:link`

#### Request parameters

| Name | Type   | Description                                             |
| ---- | ------ | ------------------------------------------------------- |
| link | String | A random 10 character code associated with a playground |

#### Request queries

| Name     | Type   | Description                      |
| -------- | ------ | -------------------------------- |
| username | String | Username of the user to be added |
