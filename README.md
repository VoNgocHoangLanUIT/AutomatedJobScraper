
# 🕸️ Project 5 - Web Scraping Job Listings with Regular Expressions

Dự án này là một **script Python tự động** thu thập thông tin tuyển dụng từ trang [vieclam24h.vn](https://vieclam24h.vn), lọc các tin tuyển dụng dựa trên **biểu thức chính quy (Regular Expressions)** theo tiêu chí người dùng định nghĩa, lưu kết quả vào file CSV và gửi thông báo qua email.

---

## 📌 Tính năng chính

- ✅ **Thu thập dữ liệu** từ nhiều trang kết quả tìm kiếm (hỗ trợ phân trang)
- ✅ **Trích xuất thông tin** quan trọng:
  - Tiêu đề công việc
  - Tên công ty
  - Địa điểm làm việc
  - Mô tả công việc
  - Ngày đăng tuyển
  - Liên kết đến tin tuyển dụng
- ✅ **Lọc tin tuyển dụng** bằng biểu thức chính quy:
  - Bao gồm các công việc chứa từ khóa mong muốn
  - Loại trừ các công việc chứa từ khóa không mong muốn
- ✅ **Lưu kết quả** vào file CSV
- ✅ **Gửi email thông báo** với danh sách công việc phù hợp
- ✅ **Lên lịch chạy tự động hàng ngày** vào lúc 08:00 sáng

---

## ⚙️ Yêu cầu hệ thống

- Python 3.x
- Google Chrome và ChromeDriver
- Thư viện Python:
  ```bash
  pip install selenium beautifulsoup4 pandas schedule
  ```

---

## 🔍 Cách hoạt động

### 1. Cấu hình tiêu chí lọc

Trong script, bạn có thể điều chỉnh các từ khóa để lọc tin tuyển dụng:

```python
Require_Term = [r'IT Phần mềm', r'tester', r'Phân tích', r'mobile', r'web']
Exclude_Term = [r'IT Phần cứng', r'Intership', r'Thực tập sinh', r'Hà Nội']
```

- **Require_Term**: Danh sách các từ khóa mà tin tuyển dụng phải chứa ít nhất một trong số đó.
- **Exclude_Term**: Danh sách các từ khóa mà tin tuyển dụng không được chứa bất kỳ từ nào trong số đó.

### 2. Cấu hình email thông báo

Để gửi email thông báo, bạn cần:

- Tài khoản Gmail với [Mật khẩu ứng dụng](https://support.google.com/accounts/answer/185833) đã được bật.
- Thay thế `sender_email`, `receiver_email`, và `password` trong script bằng thông tin của bạn:

```python
sender_email = 'your_email@gmail.com'
receiver_email = 'receiver_email@gmail.com'
password = 'your_app_password'
```

### 3. Lưu kết quả

Kết quả được lưu vào file CSV tại đường dẫn:

```
D:/Python/job_listings.csv
```

Mỗi lần chạy script, dữ liệu mới sẽ được thêm vào file cùng với thời gian cập nhật.

### 4. Lên lịch chạy tự động

Script được lên lịch chạy tự động hàng ngày vào lúc 08:00 sáng bằng thư viện `schedule`:

```python
schedule.every().day.at("08:00").do(scrape_jobs)
```

Bạn có thể thay đổi thời gian hoặc tần suất chạy tùy ý.

---

## ✅ Cách chạy script

Chạy script bằng lệnh sau:

```bash
python job_scraper.py
```

Script sẽ thực hiện các bước sau:

1. Thu thập và lọc tin tuyển dụng
2. Lưu kết quả vào file CSV
3. Gửi email thông báo
4. Chờ và chạy lại vào ngày hôm sau

---

## 📝 Ví dụ email thông báo

```
Job Title: Tester Mobile App
Company Name: ABC Tech
Location: Hồ Chí Minh
Description: Kiểm thử ứng dụng di động cho hệ điều hành iOS/Android...
Date Posted: Hôm nay
Job Link: https://vieclam24h.vn/job/abc123
```

---

## 📄 Giấy phép

Dự án này được phát triển cho mục đích học tập và cá nhân. Vui lòng đảm bảo tuân thủ các điều khoản dịch vụ của trang web khi sử dụng script này.
