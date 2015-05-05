---
title: Voxelus API Reference

language_tabs:
  - shell

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='http://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction
```
  _          _ _
 | |__   ___| | | ___
 | '_ \ / _ \ | |/ _ \
 | | | |  __/ | | (_) |
 |_| |_|\___|_|_|\___/     _
 __      _____  _ __| | __| |
 \ \ /\ / / _ \| '__| |/ _` |
  \ V  V / (_) | |  | | (_| |
   \_/\_/ \___/|_|  |_|\__,_|

```

Welcome to the Voxelus API! You can use our API to access Voxelus API endpoints, which can get information from our database.

We have language bindings in Shell! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This example API documentation page was created with [Slate](http://github.com/tripit/slate). Feel free to edit it and use it as a base for your own API's documentation.

# Authentication

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "X-Access-Token: foobar"
```

> Make sure to replace `foobar` with your API key.

Voxelus uses API keys to allow access to the API. You can register a new Voxelus API key at our [website](http://www.voxelus.com/).

Voxelus expects for the API key to be included in all API requests to the server in a header that looks like the following:

`X-Access-Token: 76740eeda4a55ec9632ae73429fd545f`

<aside class="notice">
You must replace <code>foobar</code> with your personal API key.
</aside>

# Auth
```
                  ._,.
            ."..-..pf
            -L   ..#'
          .+_L  ."]#
          ,'j' .+.j`                 -'.__..,.,p.
         _~ #..<..0.                 .J-.``..._f.
        .7..#_.. _f.                .....-..,`4'
        ;` ,#j.  T'      ..         ..J....,'.j`
       .` .."^.,-0.,,,,yMMMMM,.    ,-.J...+`.j@
      .'.`...' .yMMMMM0M@^=`""g.. .'..J..".'.jH
      j' .'1`  q'^)@@#"^".`"='BNg_...,]_)'...0-
     .T ...I. j"    .'..+,_.'3#MMM0MggCBf....F.
     j/.+'.{..+       `^~'-^~~""""'"""?'"``'1`
     .... .y.}                  `.._-:`_...jf
     g-.  .Lg'                 ..,..'-....,'.
    .'.   .Y^                  .....',].._f
    ......-f.                 .-,,.,.-:--&`
                              .`...'..`_J`
                              .~......'#'  May the Force be with you.
                              '..,,.,_]`
                              .L..`..``.
```

## Signup

```shell
curl -X POST --include "https://voxelus.herokuapp.com/v1/auth/signup" \
-H "Content-Type: application/json" \
-d '{"username":"foobar","password":"leave_britney_alone","email":"foo@bar.com"}'
```

> The above command returns JSON structured like this:

```json
{
  "token":"3858f62230ac3c915f300c664312c63f"
}
```

This endpoint registers a new user

### HTTP REQUEST

`POST /v1/auth/signup`

### Default Parameters

Name | Type | Description
---- | ---- | -----------
username|String|The user’s username; it must be unique.
email|String|The user’s email; it must be unique.
password|String|The user’s password; it’s encrypted and never returned within the API response.

## Login

```shell
curl -X POST --include "https://voxelus.herokuapp.com/v1/auth/login" \
-H "Content-Type: application/json" \
-d '{"username":"foobar","password":"leave_britney_alone"}'
```

> The above command returns JSON structured like this:

```json
{
  "token":"3858f62230ac3c915f300c664312c63f"
}
```

This endpoint logins an user

### HTTP REQUEST

`POST /v1/auth/login`

### Default Parameters

Name | Type | Description
---- | ---- | -----------
username|String|The user’s username.
password|String|The user’s password.

# Users
```
∩( ・ω・)∩
```

## Me

```shell
curl -X GET --include "https://voxelus.herokuapp.com/v1/users/me" \
-H "X-Access-Token: 76740eeda4a55ec9632ae73429fd545f"
```

> The above command returns JSON structured like this:

```json
{
  "username": "foobar",
  "created_at": "2015-05-04T22:55:14.659Z",
  "gravatar":"f3ada405ce890b6f8204094deb12d8a8"
}
```

Returns personal data.

### HTTP REQUEST

`GET /v1/users/me`

# Worlds
```
            _____
        ,-:` \;',`'-,
      .'-;_,;  ':-;_,'.
     /;   '/    ,  _`.-\
    | '`. (`     /` ` \`|
    |:.  `\`-.   \_   / |
    |     (   `,  .`\ ;'|
     \     | .'     `-'/
      `.   ;/        .'
    jgs `'-._____.-'`
```

## List all worlds

```shell
curl -X GET --include "https://voxelus.herokuapp.com/v1/worlds"
```

> The above command returns JSON structured like this:

```json
[
  {
    "title": "foo",
    "description": "bar",
    "created_at": "2015-05-04T20:00:02Z",
    "updated_at": "2015-05-04T20:00:02Z"
  },
  {
    "title": "foo",
    "description": "bar",
    "created_at": "2015-05-04T20:00:02Z",
    "updated_at": "2015-05-04T20:00:02Z"
  },
  {
    "title": "foo",
    "description": "bar",
    "created_at": "2015-05-04T20:00:01Z",
    "updated_at":"2015-05-04T20:00:01Z"
  }
]
```

Returns a list of worlds.

### HTTP REQUEST

`GET /v1/worlds`

## Creating a world

```shell
curl -X POST --include "https://voxelus.herokuapp.com/v1/worlds" \
-H "Content-Type: application/json" \
-H "X-Access-Token: 76740eeda4a55ec9632ae73429fd545f" \
-d '{"title":"foo","description":"bar"}'

```

> The above command returns JSON structured like this:

```json
{"title":"foo"}
```

This endpoint creates a new world.

### HTTP REQUEST

`POST /v1/worlds`

### Default Parameters

Name | Type | Description
---- | ---- | -----------
title|String|The world’s title.
description|String|The world’s descriptionl.

## Retrieving an existing

```shell
curl -X GET --include "https://voxelus.herokuapp.com/v1/worlds/1"
```

> The above command returns JSON structured like this:

```json
{"title":"foo"}
```

Retrieves the details of an existing world.

### HTTP REQUEST

`GET /v1/worlds/:world_id`

### Default Parameters
Name | Type | Description
---- | ---- | -----------
world_id|Int|The identifier of the user to be retrieved.

## Deleting a world

```shell
curl -X DELETE --include "https://voxelus.herokuapp.com/v1/worlds/1" \
-H "X-Access-Token: 76740eeda4a55ec9632ae73429fd545f"
```
> The above command returns JSON structured like this:

```json
{
  "destroy": "1"
}
```

# Uploads

# Kittens

## Get All Kittens

```shell
curl "http://example.com/api/kittens"
  -H "X-Access-Token: foobar"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Isis",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```shell
curl "http://example.com/api/kittens/3"
  -H "X-Access-Token: foobar"
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Isis",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">If you're not using an administrator API key, note that some kittens will return 403 Forbidden if they are hidden for admins only.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the cat to retrieve

