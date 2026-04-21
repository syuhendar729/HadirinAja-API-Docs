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
        "2025-11-01": "HADIR",
        "2025-11-02": "HADIR",
        "2025-11-03": "ALPHA",
        "2025-11-04": "IZIN",
        // ...
        "2026-03-29": "HADIR",
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

## 2. Create Attendance

Method: `POST`
Endpoint: `/attendances`

Request Body:
```json
{
    "status": "HADIR",
    "location": "Institut Teknologi Sumatera",
    "notes": "Hadir tapi terlambat",
}
```

Response Body - Success:
```json
{
	"data": {
		"status": "HADIR",
		"location": "Institut Teknologi Sumatera",
		"notes": "Hadir tapi terlambat"
	},
	"message": "Success create attendance!"
}
```

Response Body - Error:
```json
// user unauthorized
{
    "data": [],
    "message": "Failed attendance user! User unauthorized."
}
// invalid input
{
    "data": [],
    "message": "Failed attendance user! Invalid input."
}
```

---

## 3. Upload Picture

Method: `POST`
Endpoint: `/attendances/image`

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
