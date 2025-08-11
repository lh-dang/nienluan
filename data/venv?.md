### venv là viết tắt của Virtual Environment – tức là một môi trường Python riêng biệt cho dự án, tách biệt hoàn toàn với Python hệ thống.

### Cách tạo và dùng venv trong Python

- Bước 1 – Cài gói tạo venv
- Trên Kali:
```
sudo apt install python3-venv
```
- Bước 2 – Tạo môi trường ảo
- Giả sử dự án ở thư mục ~/sqli:

```
cd ~/sqli
python3 -m venv venv
```
> Lệnh này tạo thư mục venv/ chứa Python và pip riêng.

> Có thể đổi tên venv thành gì cũng được, nhưng thường giữ tên venv hoặc .venv.

- Bước 3 – Kích hoạt môi trường ảo
```
source venv/bin/activate
```

- Khi kích hoạt, đầu dòng lệnh sẽ hiện:
```
(venv) ┌──(kali㉿kali)-[~/sqli]
```
> → Nghĩa là mọi pip install giờ đây chỉ cài vào venv này.
Bước 4 – Cài gói trong venv
```
pip install scikit-learn flask
```

> Không cần sudo và không bị ảnh hưởng bởi PEP 668.
- Bước 5 – Chạy dự án trong venv
```
python <app.py>
```
- Python này sẽ dùng các thư viện trong venv.

- Bước 6 – Thoát venv
```
deactivate
```
- Trở về Python hệ thống.
- 3. Mẹo quản lý venv
- Để lưu danh sách thư viện đã cài:

> pip freeze > requirements.txt

Khi cài trên máy khác:
```
pip install -r requirements.txt
```
Không commit thư mục venv/ lên Git (thêm vào .gitignore).
