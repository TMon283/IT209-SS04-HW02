# BÁO CÁO THỰC HÀNH QUẢN LÝ NHÁNH VÀ GIẢI QUYẾT XUNG ĐỘT

## 1. Mục tiêu

Thực hiện tạo và quản lý các nhánh Git, cố ý tạo Merge Conflict trên file `README.md`, xử lý xung đột thủ công và hoàn thành Merge Commit.

## 2. Các bước thực hiện

### Bước 1: Khởi tạo repository

Tạo Git repository và tạo commit ban đầu cho file `README.md`.

```bash
git init
git add README.md
git commit -m "Initial commit"
```

### Bước 2: Tạo nhánh feature

Tạo nhánh `feature-update` và chuyển sang nhánh này.

```bash
git switch -c feature-update
```

Sau đó chỉnh sửa file `README.md` và commit:

```bash
git add README.md
git commit -m "Update README on feature branch"
```

### Bước 3: Cập nhật nhánh main

Chuyển về nhánh `main`:

```bash
git switch main
```

Tiếp tục chỉnh sửa cùng phần nội dung trong `README.md` và commit:

```bash
git add README.md
git commit -m "Update README on main branch"
```

Lúc này hai nhánh đã có các thay đổi khác nhau trên cùng file.

### Bước 4: Tạo Merge Conflict

Chuyển lại sang `feature-update`:

```bash
git switch feature-update
```

Thực hiện merge:

```bash
git merge main
```

Git phát hiện hai nhánh cùng thay đổi nội dung trong `README.md` nên xảy ra Merge Conflict.

### Bước 5: Giải quyết xung đột thủ công

Mở file `README.md` và tìm các ký hiệu:

```text
<<<<<<< HEAD
=======
>>>>>>> main
```

Các ký hiệu này xác định phần nội dung của hai nhánh đang xung đột.

Tiến hành lựa chọn và kết hợp nội dung phù hợp, đồng thời xóa thủ công toàn bộ các ký hiệu đánh dấu conflict.

Sau khi chỉnh sửa xong, kiểm tra trạng thái:

```bash
git status
```

Đánh dấu conflict đã được giải quyết:

```bash
git add README.md
```

### Bước 6: Tạo Merge Commit

Hoàn thành quá trình merge bằng:

```bash
git commit -m "Merge main into feature-update and resolve conflict"
```

Commit này là Merge Commit và có hai commit cha, tương ứng với hai nhánh được hợp nhất.

### Bước 7: Kiểm tra lịch sử

Sử dụng:

```bash
git log --graph --oneline --all
```

Kết quả hiển thị lịch sử phân nhánh và Merge Commit, qua đó có thể quan sát trực quan quá trình tách nhánh và hợp nhất hai nhánh.

## 3. Kết quả

Đã hoàn thành việc:

- Tạo nhánh `feature-update`.
- Thực hiện các thay đổi riêng trên `feature-update` và `main`.
- Cố ý tạo Merge Conflict trên `README.md`.
- Xử lý Merge Conflict thủ công.
- Xóa các ký hiệu `<<<<<<<`, `=======`, `>>>>>>>`.
- Tạo Merge Commit.
- Kiểm tra lịch sử commit bằng `git log --graph --oneline --all`.

## 4. Ảnh minh chứng

image/Screenshot.png

```bash
git log --graph --oneline --all
```

Ảnh cần thể hiện được nhánh `feature-update`, nhánh `main` và Merge Commit.