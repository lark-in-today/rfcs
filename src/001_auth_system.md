# 01_auth_system

## Request Table

| Type    | Code | Message                          |
|---------|------|----------------------------------|
| OK      | 000  | Created Token.                   |
| ERROR   | 000  | No Public Key in Request Header. |
| WARNING | 000  | Generating Token...              |

## Auth System

```sequence
title: Auth System
Client -->> Server: public-key-header: pk
Server -->> Client: token
Client -->  Server: headers: signed-token-header, public-key-header
Server -->  Client: saved {public_key: signed_token}
Client ->   Server: normal request
```

## 摘要

1. 客户端的请求头中必须存在 __公钥__(ed25519)
   1. `public-key-header: your_public_key`
   2. 若没有公钥，则会 __请求失败__。
2. 首次求请求后，服务器返回一个 token
3. 客户端使用 __私钥__ 对 token 进行签名，将 `token` 与 签名后的 `signed_token` 加入请求头。
   1. `token-header: your_token`
   2. `signed-token-header: your_signed_token`
4. 以上流程(2 次请求)完成后，则可根据记录的身份任意请求。

标准的 headers 如下：

```json
headers: { 
	"Accept": "application/json, text/plain, */*",
	"public-key-header": "py+qzXgPUdfNipn2QF+yGBDvRsMeLOeG95+K6zMIL/E=",
    "token-header": "",
    "signed-token-header": "",
    "User-Agent": "axios/0.19.0" 
}
```
