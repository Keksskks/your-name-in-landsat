# 🚀 NASA Landsat Name Generator

Tạo chữ cái bằng ảnh vệ tinh NASA Landsat 🛰️

## 👨‍💻 Người tạo
- Creator: Xellox

## 📌 Giới thiệu
Tool này sử dụng ảnh từ chương trình NASA Landsat để tạo ảnh theo từng ký tự trong tên của bạn.

Ví dụ:
```bash
python landsat.py NASA
```

Tool sẽ tự động tải ảnh từng chữ cái từ NASA.

---

# 📷 Demo

Tên nhập:
```bash
XELLOX
```

Kết quả:
- X.jpg
- E.jpg
- L.jpg
- L.jpg
- O.jpg
- X.jpg


---

# 🛰️ NASA Source

Nguồn ảnh chính thức:
https://science.nasa.gov/specials/your-name-in-landsat/

Image API format:
```python
https://science.nasa.gov/specials/your-name-in-landsat/images/{char}_{index}.jpg
```

---

# ⚙️ Cài đặt

## 1. Clone repository
```bash
git clone https://github.com/yourusername/nasa-landsat-generator.git
cd nasa-landsat-generator
```

## 2. Cài thư viện
```bash
pip install requests
```

---

# ▶️ Sử dụng

## Chạy cơ bản
```bash
python your name in landsat.py NASA
```

## Chỉ định thư mục output
```bash
python your name in landsat.py NASA --out output_folder
```

---

# 📂 Cấu trúc

```bash
landsat_output/
├── 1_N.jpg
├── 2_A.jpg
├── 3_S.jpg
└── 4_A.jpg
```

---

# 🧠 Source Code

```python
import requests
import os
import random
import argparse

class LandsatDownloader:
   
    BASE_URL = "https://science.nasa.gov/specials/your-name-in-landsat/images/"
    
    ALPHABET_DATA = {
        "A": ["0", "1", "2", "3", "4"],
        "B": ["0", "1"],
        "C": ["0", "1", "2"],
        "D": ["0", "1"],
        "E": ["0", "1", "2", "3"],
        "F": ["0", "1"],
        "G": ["0"],
        "H": ["0", "1"],
        "I": ["0", "1", "2", "3", "4"],
        "J": ["0", "1", "2"],
        "K": ["0", "1"],
        "L": ["0", "1", "2", "3"],
        "M": ["0", "1", "2"],
        "N": ["0", "1", "2"],
        "O": ["0", "1"],
        "P": ["0", "1"],
        "Q": ["0", "1"],
        "R": ["0", "1", "2", "3"],
        "S": ["0", "1", "2"],
        "T": ["0", "1"],
        "U": ["0", "1"],
        "V": ["0", "1", "2", "3"],
        "W": ["0", "1"],
        "X": ["0", "1", "2"],
        "Y": ["0", "1"],
        "Z": ["0"]
    }

    def __init__(self, output_dir="landsat_images"):
        self.output_dir = output_dir
        if not os.path.exists(self.output_dir):
            os.makedirs(self.output_dir)

    def get_image_url(self, char, index=None):
        char = char.lower()
        char_upper = char.upper()
        
        if char_upper not in self.ALPHABET_DATA:
            return None
        
        available_indices = self.ALPHABET_DATA[char_upper]
        
        if not available_indices:
            idx = "0"
        elif index is not None and str(index) in available_indices:
            idx = str(index)
        else:
            idx = random.choice(available_indices)
            
        return f"{self.BASE_URL}{char}_{idx}.jpg"

    def download_name(self, name):
        print(f"Đang tìm kiếm ảnh cho tên: {name}")
        downloaded_files = []
        
        for i, char in enumerate(name):
            if char.isspace():
                continue
                
            url = self.get_image_url(char)
            if not url:
                continue
                
            filename = f"{i+1}_{char.upper()}.jpg"
            filepath = os.path.join(self.output_dir, filename)
            
            try:
                response = requests.get(url, stream=True, timeout=10)
                if response.status_code == 200:
                    with open(filepath, 'wb') as f:
                        for chunk in response.iter_content(1024):
                            f.write(chunk)
                    print(f"Đã tải: {filename} từ {url}")
                    downloaded_files.append(filepath)
                    
            except Exception:
                pass
                
        return downloaded_files

if __name__ == "__main__":
    parser = argparse.ArgumentParser(description="Tải ảnh Landsat theo tên.")
    parser.add_argument("name", help="Tên muốn tìm kiếm")
    parser.add_argument("--out", default="landsat_output", help="Thư mục lưu ảnh")
    
    args = parser.parse_args()
    
    downloader = LandsatDownloader(args.out)
    files = downloader.download_name(args.name)
```

---

# ⭐ Features

- Tải ảnh NASA theo tên
- Random ảnh cho từng ký tự
- Hỗ trợ mọi tên tiếng Anh
- Dễ chỉnh sửa
- Open Source

---

# 📜 License

MIT License

---

# ❤️ Credits

- NASA Landsat
- Creator: Xellox

