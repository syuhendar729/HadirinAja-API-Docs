# Absensi - API Documentation

---

Base URL: `http://localhost:8080`

| Method | Endpoint              | Description                                 |
|--------|-----------------------|---------------------------------------------|
| GET    | /attendance          | Get all data attendances from current user  |
| POST   | /attendance          | Send attendance in current time             |
| POST   | /attendance/image    | Upload attendance picture                   |

---

## 1. Get Attendance

Method: `GET`
Endpoint: `/api/attendance`
Authorization: `Bearer <token>`

Response Body - Success:
```json
// PRESENT, LATE, LEAVE, or ABSENT

{
    "data": [
        {
			"id": 1,
            "created_at": "2025-11-01",
            "status": "PRESENT",
        },
        {
			"id": 2,
            "created_at": "2025-11-02",
            "status": "LATE",
        },
        {
			"id": 3,
            "created_at": "2025-11-03",
            "status": "LEAVE",
        },
        {
			"id": 4,
            "created_at": "2025-11-04",
            "status": "ABSENT",
        }
    ],
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

## 2. Get Attendance Detail

Method: `GET`
Endpoint: `/api/attendance/<id>`
Authorization: `Bearer <token>`

Response Body - Success:

```json
{
    "data": {
        "created_at": "2025-11-01",
        "status": "PRESENT",
        "location": "Institut Teknologi Sumatera",
        "notes": "Terlambat tapi masih datenng",
        "url_image": "https://cloud.image/2025-mar-28.jpg"
    }
    "message": "Success get attendance!"
}

```


---

## 3. Create Attendance

Method: `POST`
Endpoint: `/api/attendance`

Request Body:
```json
{
    "status": "LATE",
    "location": "Institut Teknologi Sumatera",
    "notes": "Hadir tapi terlambat",
    "url_image": "https://cloud.image/2025-mar-28.jpg",
    "latitude": -5.360000,
    "longitude": 105.315000

}
```

Response Body - Success:
```json
{
	"data": {
        "id": 1,
		"status": "LATE",
		"location": "Institut Teknologi Sumatera",
		"notes": "Hadir tapi terlambat",
        "url_image": "https://cloud.image/2025-mar-28.jpg",
        "latitude": -5.360000,
        "longitude": 105.315000
	},
	"message": "Success create attendance!"
}
```

Response Body - Error:
```json
// user unauthorized
{
    "data": [],
    "message": "Failed create attendance! User unauthorized."
}
// invalid input
{
    "data": [],
    "message": "Failed create attendance! Invalid input."
}
```

---

## 3. Upload Picture

Method: `POST`
Endpoint: `/api/attendance/image`

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
