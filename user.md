# User - API Documentation

---

Base URL: `http://localhost:8080`

| Method | Endpoint       | Description                  |
|--------|----------------|------------------------------|
| GET    | /users/{id}    | Get a specific user          |
| PATCH  | /users/{id}    | Update user by id            |
| DELETE | /users/{id}    | Remove a user                |
| GET    | /users         | Get all users                |

---

## 1. Get User

Method: `GET`
Endpoint: `/users/{id}`
Authorization: `Bearer <token>`

Response Body - Success:
```json
{
    "data": {
        "name": "Syuhada Rantisi",
        "email": "oda@mail.com",
        "nim": "122140092",
        "position": "Staff",
        "attendance": 100
    },
    "message": "Success get user!"
}
```

Response Body - Error:
```json
// user unauthorized
{
    "data": [],
    "message": "Failed get user! User unauthorized."
}
```

---

## 2. Update User

Method: `PATCH`
Endpoint: `/users/{id}`
Authorization: `Bearer <token>`

Request Body:
```json
{
  "email": "oda@mail.com",
  "name": "Muhammad Rayhan",
  "nim": "123456789"
}
```

Response Body - Success:
```json
{
    "data": {
        "email": "oda@mail.com",
        "name": "Muhammad Rayhan",
        "nim": "123456789"
    },
    "message": "Success update user!"
}
```

Response Body - Error:
```json
// user unauthorized
{
    "data": [],
    "message": "Failed update user! User unauthorized."
}
```

---

## 3. Delete User

Method: `DELETE`
Endpoint: `/users/{id}`
Authorization: `Bearer <token>`


Response Body - Success:
```json
{
    "data": [],
    "message": "Success delete user!"
}
```

Response Body - Error:
```json
// user unauthorized
{
    "data": [],
    "message": "Failed delete user! User unauthorized."
}
```

---

## 4. Get All User (For Admin)

Method: `GET`
Endpoint: `/users`
Authorization: `Bearer <token>`

Response Body - Success:
```json
{
    "data": [
        {
            "name": "Syuhada Rantisi",
            "email": "oda@mail.com",
            "nim": "122140092",
            "position": "Staff",
            "attendance": 100
        },
        {
            "name": "M Rayhan",
            "email": "ray@mail.com",
            "nim": "122140093",
            "position": "Staff",
            "attendance": 100
        },
    ],
    "message": "Success get all user!"
}
```

Response Body - Error:
```json
// user unauthorized
{
    "data": [],
    "message": "Failed get user! User unauthorized."
}
```

