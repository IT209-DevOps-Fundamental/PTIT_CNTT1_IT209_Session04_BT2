# Báo cáo Bài 2: Quản lý nhánh và Giải quyết xung đột (Merge Conflict)

## 1. Trạng thái sau khi giải quyết xung đột
Nội dung file sau khi đã xử lý các dấu `<<<<<<<`, `=======`, `>>>>>>>`:

```text
# System Configuration

Status: Active on main and feature merged
```

## 2. Các bước giải quyết xung đột thủ công
- **Bước 1:** Cố ý tạo conflict bằng cách sửa cùng một dòng trong `README.md` ở hai nhánh `main` và `feature-update`.
- **Bước 2:** Chạy lệnh `git merge feature-update` khi đang đứng ở nhánh `main`. Git báo lỗi CONFLICT.
- **Bước 3:** Mở file `README.md` lên, tìm đến phần code bị đánh dấu:
  ```text
  <<<<<<< HEAD
  Status: Active on main
  =======
  Status: Updating feature
  >>>>>>> feature-update
  ```
- **Bước 4:** Xóa bỏ các dòng đánh dấu (`<<<<<<< HEAD`, `=======`, `>>>>>>> feature-update`) và hợp nhất thành nội dung mong muốn: `Status: Active on main and feature merged`.
- **Bước 5:** Lưu file, sau đó đưa file vào vùng chuẩn bị với lệnh `git add README.md`.
- **Bước 6:** Hoàn tất việc gộp nhánh với lệnh `git commit -m "Merge branch 'feature-update' into main"`.

## 3. Lịch sử commit và Đồ thị nhánh
Kết quả lệnh `git log --graph --oneline`:

```text
*   37e62e9 Merge branch 'feature-update' into main
|\  
| * d3948df Update status on feature-update branch
* | 892a51b Update status on main branch
|/  
* 249510a Initial commit on main
```
