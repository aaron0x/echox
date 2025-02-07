+++
title = "JWT Recipe"
description = "JWT recipe for Echo"
[menu.main]
  name = "JWT"
  identifier = "cookbook-jwt"
  parent = "cookbook"
+++

- JWT authentication using HS256 algorithm.
- JWT is retrieved from `Authorization` request header.

## Server using Map claims

`server.go`

{{< embed "jwt/map-claims/server.go" >}}

## Server using custom claims

`server.go`

{{< embed "jwt/custom-claims/server.go" >}}

## Client

`curl`

### Login

Login using username and password to retrieve a token.

```sh
curl -X POST -d 'username=jon' -d 'password=shhh!' localhost:1323/login
```

*Response*

```js
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE0NjE5NTcxMzZ9.RB3arc4-OyzASAaUhC2W3ReWaXAt_z2Fd3BN4aWTgEY"
}
```

### Request

Request a restricted resource using the token in `Authorization` request header.

```sh
curl localhost:1323/restricted -H "Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE0NjE5NTcxMzZ9.RB3arc4-OyzASAaUhC2W3ReWaXAt_z2Fd3BN4aWTgEY"
```

*Response*

```
Welcome Jon Snow!
```

## [Source Code]({{< source "jwt" >}})

