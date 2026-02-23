# 🎓 Student API with Gin Framework

REST API สำหรับจัดการข้อมูลนักศึกษา  
พัฒนาด้วย **Go (Golang)**, **Gin Framework** และ **SQLite**

รองรับการทำงานแบบ CRUD (Create, Read, Update, Delete)  
พร้อมระบบตรวจสอบข้อมูล (Input Validation) และการจัดการ Error ตามมาตรฐาน HTTP

---

## ✨ Features

- ✅ Get all students (GET)
- ✅ Get student by ID (GET)
- ✅ Create new student (POST)
- ✅ Update student (PUT)
- ✅ Delete student (DELETE)
- ✅ Input Validation (ID, Name, GPA)
- ✅ Proper HTTP Status Codes

---

## 📁 Project Structure

```

go-api-gin-lab/
├── main.go                    # Entry point & Routes
├── config/
│   └── database.go            # Database configuration
├── models/
│   └── student.go             # Student data model
├── repositories/
│   └── student_repository.go  # Database operations
├── services/
│   └── student_service.go     # Business logic & validation
├── handlers/
│   └── student_handler.go     # HTTP handlers
├── go.mod                     # Go modules
├── go.sum                     # Dependencies checksum
└── students.db                # SQLite database (auto-generated)

```

โปรเจคใช้ **Layered Architecture** แบ่งออกเป็น 4 ชั้น

- **Handler** → จัดการ HTTP Request และ Response
- **Service** → ประมวลผล Business Logic และ Validation
- **Repository** → ติดต่อและจัดการฐานข้อมูล
- **Model** → โครงสร้างข้อมูล (Data Structure)

---

## 🚀 How to Run

### 📌 Prerequisites

1️⃣ Go
```bash
go version
```
ควรเป็น Go 1.20+

2️⃣ Git

### 🔧 Installation

1️⃣ Clone repository

```bash
git clone https://github.com/Chonr/go-api-gin-lab.git
cd go-api-gin-lab
````

2️⃣ Install dependencies

```bash
go mod tidy
```

3️⃣ Run server

```bash
go run main.go
```

Server will start at:

```
http://localhost:8080
```

---

## 📡 Testing API with Postman

### 🔹 Base URL

```
http://localhost:8080
```

### 🔹 Required Headers (POST / PUT)

| Key          | Value            |
| ------------ | ---------------- |
| Content-Type | application/json |

---

## 🧪 API Endpoints

### 1️⃣ GET /students

ดึงข้อมูลนักศึกษาทั้งหมด

**Response (200 OK)**

```json
[
  {
    "id": "6609650269",
    "name": "Chonr",
    "major": "Computer Science",
    "gpa": 3.8
  }
]
```

**Internal Error (500)**

```json
{
  "error": "failed to fetch students"
}
```

---

### 2️⃣ GET /students/:id

ดึงข้อมูลนักศึกษาตาม ID

**Success (200 OK)**

```json
{
  "id": "6609650269",
  "name": "Chonr",
  "major": "Computer Science",
  "gpa": 3.8
}
```

**Error (404 Not Found)**

```json
{
  "error": "Student not found"
}
```

---

### 3️⃣ POST /students

เพิ่มข้อมูลนักศึกษาใหม่

**Request Body**

```json
{
  "id": "6609650269",
  "name": "Chonr",
  "major": "Computer Science",
  "gpa": 3.8
}
```

**Success (201 Created)**

```json
{
  "id": "6609650269",
  "name": "Chonr",
  "major": "Computer Science",
  "gpa": 3.8
}
```

#### ❌ Validation Errors (400 Bad Request)

```json
{ "error": "id must not be empty" }
```

```json
{ "error": "name must not be empty" }
```

```json
{ "error": "gpa must be between 0.00 and 4.00" }
```

**Invalid JSON (400)**

```json
{
  "error": "invalid request body"
}
```

**Internal Server Error (500)**

```json
{
  "error": "failed to create student"
}
```

---

### 4️⃣ PUT /students/:id

แก้ไขข้อมูลนักศึกษา

**Success (200 OK)**

```json
{
  "id": "6609650269",
  "name": "Chonr Updated",
  "major": "Software Engineering",
  "gpa": 3.9
}
```

**Validation Error (400)**

```json
{
  "error": "gpa must be between 0.00 and 4.00"
}
```

**Error (404 Not Found)**

```json
{
  "error": "Student not found"
}
```

---

### 5️⃣ DELETE /students/:id

ลบข้อมูลนักศึกษา

**Success (204 No Content)**
ไม่มี Response Body

**Error (404 Not Found)**

```json
{
  "error": "Student not found"
}
```

---

## ✅ Validation Rules

| Field | Rule                        |
| ----- | --------------------------- |
| id    | ต้องไม่ว่าง (เฉพาะตอน POST) |
| name  | ต้องไม่ว่าง                 |
| gpa   | ต้องอยู่ระหว่าง 0.00 – 4.00 |

---

## 🎯 HTTP Status Codes

| Code | Meaning               |
| ---- | --------------------- |
| 200  | Success               |
| 201  | Created               |
| 204  | No Content            |
| 400  | Bad Request           |
| 404  | Not Found             |
| 500  | Internal Server Error |

---

## 💡 What I Learned

* การออกแบบ RESTful API ตามมาตรฐาน
* การใช้ Layered Architecture แยกความรับผิดชอบ
* การทำ Input Validation
* การจัดการ HTTP Status Codes อย่างถูกต้อง
* การทำ CRUD กับ SQLite

---

## 👨‍💻 Author

**Student ID:** 6609650269

**Student Name:** Chonrathan S.

**Course:** CS367 WEB SERVICE DEVELOPMENT CONCEPTS

---

Last Updated: February 2026
