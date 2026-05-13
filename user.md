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
Endpoint: `/api/user`
Authorization: `Bearer <token>`

Response Body - Success:
```json
{
    "data": {
        "id": 4,
		"role_id": 2
        "name": "Test User",
        "email": "test@mail.com",
        "email_verified_at": null,
		"created_at": "2026-04-27T18:13:06.000000Z",
		"updated_at": "2026-04-27T18:13:06.000000Z",
        "profile_picture": "http://localhost/storage/user1.png",
        "nik": "122140092",
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
Endpoint: `/api/user`
Authorization: `Bearer <token>`

Request Body:
```json
{
  "email": "testupdate@mail.com",
  "name": "Test Update",
  "nik": "123456789",
}
```

Response Body - Success:
```json
{
    "data": {
		"id": 5,
		"name": "Test Update",
		"email": "testupdate@mail.com",
		"email_verified_at": null,
		"created_at": "2026-04-29T05:56:28.000000Z",
		"updated_at": "2026-04-29T05:57:07.000000Z",
		"profile_picture": null,
		"nik": "123456789",
		"role_id": 2
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
Endpoint: `/api/user`
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
Endpoint: `/api/users`
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

