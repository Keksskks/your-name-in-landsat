# 🚀 NASA Landsat Name Generator

Tạo chữ cái bằng ảnh vệ tinh từ NASA Landsat 🛰️

---

## 👨‍💻 Creator
- Xellox

---

## 📌 Giới thiệu

Tool Python sử dụng ảnh từ chương trình NASA Landsat để tạo tên bằng ảnh vệ tinh.

Ví dụ:

```bash
python landsat.py NASA
```

Kết quả sẽ tự động tải ảnh cho từng ký tự:
- N.jpg
- A.jpg
- S.jpg
- A.jpg

---

## 🛰️ NASA Source

Nguồn chính thức:

https://science.nasa.gov/specials/your-name-in-landsat/

---

## ⚙️ Cài đặt

### 1. Clone repository

```bash
git clone https://github.com/Keksskks/your-name-in-landsat.git
cd your-name-in-landsat
```

### 2. Cài thư viện

```bash
pip install -r requirements.txt
```

Hoặc:

```bash
pip install requests
```

---

## ▶️ Sử dụng

### Chạy cơ bản

```bash
python landsat.py NASA
```

### Chỉ định thư mục output

```bash
python landsat.py NASA --out output_folder
```

---

## 📂 Kết quả

```bash
landsat_output/
├── 1_N.jpg
├── 2_A.jpg
├── 3_S.jpg
└── 4_A.jpg
```

---

## ⭐ Features

- Tải ảnh NASA theo tên
- Random ảnh cho từng ký tự
- Hỗ trợ mọi chữ cái tiếng Anh
- Open Source
- Dễ chỉnh sửa

---

## 📜 License

MIT License

---

## ❤️ Credits

- NASA Landsat
- Creator: Xellox
