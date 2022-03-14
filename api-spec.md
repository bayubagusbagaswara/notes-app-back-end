# API Specification

## Data yang disimpan

```json
{
  "id": "string",
  "title": "string",
  "createdAt": "string",
  "updatedAt": "string",
  "tags": "array of string",
  "body": "string"
}
```

## Contoh Data yang tersimpan

```json
{
  "id": "notes-V1StGXR8_Z5jdHi6B-myT",
  "title": "Sejarah JavaScript",
  "createdAt": "2020-12-23T23:00:09.686Z",
  "updatedAt": "2020-12-23T23:00:09.686Z",
  "tags": ["NodeJS", "JavaScript"],
  "body": "JavaScript pertama kali dikembangkan oleh Brendan Eich dari Netscape di bawah nama Mocha, yang nantinya namanya diganti menjadi LiveScript, dan akhirnya menjadi JavaScript. Navigator sebelumnya telah mendukung Java untuk lebih bisa dimanfaatkan para pemrogram yang non-Java."
}
```

# Create New Note

- Method : `POST`
- URL : `/notes`

### Request Body :

```json
{
  "title": "Judul Catatan",
  "tags": ["Tag 1", "Tag 2"],
  "body": "Konten catatan"
}
```

### Response Success :

- Status Code : `201`

```json
{
  "status": "success",
  "message": "Catatan berhasil ditambahkan",
  "data": {
    "noteId": "V09YExygSUYogwWJ"
  }
}
```

### Response Failed :

- Status Code : `500`

```json
{
  "status": "error",
  "message": "Catatan gagal untuk ditambahkan"
}
```

# Get Note by ID

- Method : `GET`
- URL : `/notes/{id}`

### Response Success

- Status Code : `200`

```json
{
  "status": "success",
  "data": {
    "note": {
      "id": "notes-V1StGXR8_Z5jdHi6B-myT",
      "title": "Catatan 1",
      "createdAt": "2020-12-23T23:00:09.686Z",
      "updatedAt": "2020-12-23T23:00:09.686Z",
      "tags": ["Tag 1", "Tag 2"],
      "body": "Isi dari catatan 1"
    }
  }
}
```

### Response Failed (ID not found)

- Status Code : `404`

```json
{
  "status": "fail",
  "message": "Catatan tidak ditemukan"
}
```

# Get All Note

- Method : `GET`
- URL : `/notes`

### Response Success (ada datanya)

- Status Code : `200`

```json
{
  "status": "success",
  "data": {
    "notes": [
      {
        "id": "notes-V1StGXR8_Z5jdHi6B-myT",
        "title": "Catatan 1",
        "createdAt": "2020-12-23T23:00:09.686Z",
        "updatedAt": "2020-12-23T23:00:09.686Z",
        "tags": ["Tag 1", "Tag 2"],
        "body": "Isi dari catatan 1"
      },
      {
        "id": "notes-V1StGXR8_98apmLk3mm1",
        "title": "Catatan 2",
        "createdAt": "2020-12-23T23:00:09.686Z",
        "updatedAt": "2020-12-23T23:00:09.686Z",
        "tags": ["Tag 1", "Tag 2"],
        "body": "Isi dari catatan 2"
      }
    ]
  }
}
```

### Response Success (data )

- Status Code : `200`

```json
{
  "status": "success",
  "data": {
    "notes": []
  }
}
```

# Update Note

- Method : `PUT`
- URL : `/notes/{id}`

### Reqeust Body

```json
{
  "title": "Judul Catatan Revisi",
  "tags": ["Tag 1", "Tag 2"],
  "body": "Konten catatan"
}
```

### Response Success

- Status Code : `200`

```json
{
  "status": "success",
  "message": "Catatan berhasil diperbaharui"
}
```

### Response Failed (ID Not Found)

- Status Code : `404`

```json
{
  "status": "fail",
  "message": "Gagal memperbarui catatan. Id catatan tidak ditemukan"
}
```

# Delete Note

- Method : `DELETE`
- URL : `/notes/{id}`

### Response Success

- Status Code : `200`

```json
{
  "status": "success",
  "message": "Catatan berhasil dihapus"
}
```

### Response Failed (ID Not Found)

- Status Code : `404`

```json
{
  "status": "fail",
  "message": "Catatan gagal dihapus. Id catatan tidak ditemukan"
}
```
