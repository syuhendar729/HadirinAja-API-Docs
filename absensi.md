# Absensi - API Documentation

---

Base URL: `http://localhost:8080`

| Method | Endpoint              | Description                                 |
|--------|-----------------------|---------------------------------------------|
| GET    | /attendances          | Get all data attendances from current user  |
| POST   | /attendances          | Send attendance in current time             |
| POST   | /attendances/image    | Upload attendance picture                   |

---

## 1. Get Attendance

Method: `GET`
Endpoint: `/attendances`
Authorization: `Bearer <token>`

Response Body - Success:
```json
// H: hadir
// I: izin
// A: tidak hadir
{
    "data": {
        "2025-nov-01": "H",
        "2025-nov-02": "H",
        "2025-nov-03": "A",
        "2025-nov-04": "I",
        // ...
        "2026-mar-29": "H",
    },
    "message": "Success get attendance!"
}
```

Response Body - Error:
```json
// user unauthorized
{
    "data": [],
    "message": "Failed get attendances! User unauthorized."
}
```

---

## 2. Present

Method: `POST`
Endpoint: `/attendances`

Request Body:
```json
{
    "date": "2025-mar-28",
    "time": "08:00 AM",
    "location": "Institut Teknologi Sumatera",
    "url_image": "https://cloud.image/2025-mar-28.jpg"
}
```

Response Body - Success:
```json
{
    "data": {
        "date": "2025-mar-28",
        "time": "08:00 AM",
        "location": "Institut Teknologi Sumatera",
        "url_image": "https://cloud.image/2025-mar-28.jpg"
    },
    "message": "Success create attendance!"
}
```

Response Body - Error:
```json
// invalid date or time
{
    "data": {
        "date": "2025-mar-28",
        "time": "08:00 AM",
    },
    "message": "Failed attendance user! Invalid date or time."
}
// user unauthorized
{
    "data": [],
    "message": "Failed attendance user! User unauthorized."
}
// invalid url image
{
    "data": {
        "url_image": "https://cloud.image/2025-mar-28.jpg"
    }],
    "message": "Failed attendance user! Invalid Date or Time."
}
```

---

## 3. Upload Picture

Method: `POST`
Endpoint: `/attendances/image`

Request Body:
```json
{
    "date": "2025-mar-28",
    "time": "08:00 AM",
    "location": "Institut Teknologi Sumatera",
    "url_image": "https://cloud.image/2025-mar-28.jpg"
}
```

Request Body  `form-data`:
| key      | type | value        |
| ---      | ---  | ---          |
| image    | file | <file_image> |


Response Body - Success:
```json
{
    "data": {
        "url_image": "https://cloud.image/2025-mar-28.jpg"
    },
    "message": "Success upload image!"
}
```

Response Body - Error:
```json
// user unauthorized
{
    "data": [],
    "message": "Failed upload image! User unauthorized."
}
// invalid image
{
    "data": [],
    "message": "Failed upload image! Invalid image type."
}
```
