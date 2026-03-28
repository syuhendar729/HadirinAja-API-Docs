# Auth - API Documentation

---

Base URL: `http://localhost:8080`

| Method | Endpoint       | Description                  |
|--------|----------------|------------------------------|
| POST   | /auth/register | Register new user            |
| POST   | /auth/login    | Login user                   |
| DELETE | /auth/logout   | Logout user                  |

---

## 1. Register

Method: `POST`
Endpoint: `/auth/register`

Request Body:
```json
{
  "email": "oda@mail.com",
  "password": "password123"
}
```

Response Body - Success:
```json
{
    "data": {
        "name": "Syuhada Rantisi",
        "email": "oda@mail.com"
    },
    "message": "Success create user!"
}
```

Response Body - Error:
```json
// invalid password
{
    "data": [],
    "message": "Failed create user! Invalid password."
}
// email already exists
{
    "data": [],
    "message": "Failed create user! Email already exists."
}
```

---

## 2. Login

Method: `POST`
Endpoint: `/auth/login`

Request Body:
```json
{
  "email": "oda@mail.com",
  "password": "password123"
}
```

Response Body - Success:
```json
{
    "data": {
        "access_token": "<access_token>",
        "data": {
            "email": "oda@mail.com",
            "id": 1,
            "profile_picture": null,
            "username": "oda"
        },
        "refresh_token": "<refresh_token>"
    },
    "message": "Success login!"
}
```

Response Body - Error:
```json
// user not registered
{
    "data": [],
    "message": "Failed login! User not registered."
}
// if wrong password
{
    "data": [],
    "message": "Failed login! Wrong password."
}
```

---

## 3. Logout

Method: `DELETE`
Endpoint: `/auth/logout`
Authorization: `Bearer <token>`

Response Body - Success:
```json
{
    "data": {},
    "message": "Success logout!"
}
```

Response Body - Error:
```json
// if user not authorized
{
    "data": [],
    "message": "Failed logout! User unauthorized."
}
```