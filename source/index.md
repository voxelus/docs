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

## Forgot password

```shell
curl -X POST --include "https://voxelus.herokuapp.com/v1/auth/forgotpw" \
-H "Content-Type: application/json" \
-d '{"email":"foo@bar.com"}'
```

> The above command returns JSON structured like this:

```json
{
  "token":"ok"
}
```

This endpoint send an email with a temporay key for later use on resetpw endpoint

### HTTP REQUEST

`POST /v1/auth/forgotpw`

### Default Parameters

Name | Type | Description
---- | ---- | -----------
email|String|The user’s email.

## Reset password

```shell
curl -X POST --include "https://voxelus.herokuapp.com/v1/auth/resetpw" \
-H "Content-Type: application/json" \
-d '{"otp":"2.CSONNW.cpQWERTYAZERTWERPO_iFE44","password":"L3av3_britn3y_al0n3"}'
```

> The above command returns JSON structured like this:

```json
{
  "token":"ok"
}
```

Resets user's password

### HTTP REQUEST

`POST /v1/auth/resetpw`

### Default Parameters

Name | Type | Description
---- | ---- | -----------
otp|String|OTP.
password|String|The new password, optional.

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
-d '{"title":"foo","description":"bar","images":["043111ad-0994-4d05-a3b0-c4273f7a3e5f","c7c83710-b4aa-4a70-953f-9debf229e794"],"atmos":["e94f6924-5d94-4fbd-88a0-cc681bc7917d"]}'

```

> The above command returns JSON structured like this:

```json
[
  {
    "id":47
    "title":"foo",
    "description":"bar",
    "owner":[
      {
      "username":"foobar"
      }
    ],
    "images":[
      {
      "sid":"043111ad-0994-4d05-a3b0-c4273f7a3e5f",
      "image":{"url":"http://assets.voxelus.com/images/7/9454862341-dcefa385-0124-41d2-8d12-2a2572e2adc1.png"},
      "mime":"image/png",
      "size":8018
      },
      {
      "sid":"c7c83710-b4aa-4a70-953f-9debf229e794",
      "image":{"url":"http://assets.voxelus.com/images/11/0543862341-2eccf2ab-2f5d-49fb-aa63-68e3c806d2ed.png"},
      "mime":"image/png",
      "size":5243
      }
    ],
	"atmos":[
      {
      "sid":"e94f6924-5d94-4fbd-88a0-cc681bc7917d",
      "image":{"url":"http://assets.voxelus.com/atmos/434/8224862341-0cd0cab0-e217-4db5-be53-23f2df64ae4a.atmo"},
      "mime":"image/png",
      "size":34732
      }
    ]
    "created_at":"2015-05-26T23:56:12Z",
    "updated_at":"2015-05-26T23:56:12Z"
  }
]
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
```
,'";-------------------;"`.
;[]; ................. ;[];
;  ; ................. ;  ;
;  ; ................. ;  ;
;  ; ................. ;  ;
;  ; ................. ;  ;
;  ; ................. ;  ;
;  ; ................. ;  ;
;  `.                 ,'  ;
;    """""""""""""""""    ;
;    ,-------------.---.  ;
;    ;  ;"";       ;   ;  ;
;    ;  ;  ;       ;   ;  ;
;    ;  ;  ;       ;   ;  ;
;//||;  ;  ;       ;   ;||;
;\\||;  ;__;       ;   ;\/;
 `. _;          _  ;  _;  ;
   " """"""""""" """"" """
```

## Upload a new Image

```
curl -X POST --include "https://voxelus.herokuapp.com/v1/uploads/image" \
-H "X-Access-Token: 76740eeda4a55ec9632ae73429fd545f" \
-F 'image=@voxelus.png'
```

> The above command returns JSON structured like this:

```json
[
  {
    "id":"0e9d9b51-58e8-4430-8db9-b6ac741734d1",
    "image":"http://assets.voxelus.com/images/9/5475862341-7460e52e-9be1-45f6-badc-234ddd693d0f.png",
    "size":8018
  }
]
```

Upload a new image

### HTTP REQUEST

`POST /v1/uploads/image`

## Upload a new Atmo

```
curl -X POST --include "https://voxelus.herokuapp.com/v1/uploads/atmo" \
-H "X-Access-Token: 76740eeda4a55ec9632ae73429fd545f" \
-F 'atmo=@voxelus.atmo'
```

> The above command returns JSON structured like this:

```json
[
  {
    "id":"0e9d9b51-58e8-4430-8db9-b6ac741734d1",
    "atmo":"http://assets.voxelus.com/images/9/5475862341-7460e52e-9be1-45f6-badc-234ddd693d0f.png",
    "size":8018
  }
]
```

Upload a new atmo

### HTTP REQUEST

`POST /v1/uploads/atmo`


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

