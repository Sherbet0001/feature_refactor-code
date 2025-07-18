# Refactor Dự Án - Personal Task Manager

Dự án này thực hiện việc refactor code cho ứng dụng quản lý công việc cá nhân (Personal Task Manager) để cải thiện chất lượng code và tuân thủ các nguyên tắc Clean Code.

## Mục tiêu Refactor

- Áp dụng các nguyên tắc SOLID
- Loại bỏ vi phạm DRY (Don't Repeat Yourself)
- Giải quyết vấn đề YAGNI (You Aren't Gonna Need It)
- Cải thiện khả năng đọc và bảo trì code
- Tách biệt trách nhiệm của các lớp và phương thức

## Cấu trúc Dự án

```
├── CNPM.java          # Code gốc có nhiều vi phạm Clean Code
├── codeCNPM.java      # Code sau khi refactor ban đầu
└── README.md          # Tài liệu dự án
```

## Các File Chính

### [`CNPM.java`](CNPM.java)
File code gốc chứa lớp [`PersonalTaskManagerViolations`](CNPM.java) với các vấn đề:
- Vi phạm Single Responsibility Principle
- Code lặp lại (DRY violation)
- Phương thức [`addNewTaskWithViolations`](CNPM.java) quá dài và phức tạp
- Thiếu validation tốt

### [`codeCNPM.java`](codeCNPM.java)
File code đã được refactor ban đầu với:
- Thêm JavaDoc cho phương thức [`addNewTaskWithViolations`](codeCNPM.java)
- Cải thiện comments và documentation
- Khởi tạo file database tự động
- Tối ưu hóa một số logic

## Tính năng Chính

### Quản lý Công việc
- **Thêm công việc mới**: Tạo công việc với tiêu đề, mô tả, ngày đến hạn, mức độ ưu tiên
- **Validation dữ liệu**: Kiểm tra tính hợp lệ của input
- **Kiểm tra trùng lặp**: Ngăn chặn tạo công việc trùng lặp
- **Lưu trữ JSON**: Dữ liệu được lưu trong file `tasks_database.json`

### Thuộc tính Công việc
- **ID**: UUID duy nhất cho mỗi công việc
- **Tiêu đề**: Tên công việc (bắt buộc)
- **Mô tả**: Chi tiết công việc
- **Ngày đến hạn**: Định dạng YYYY-MM-DD
- **Mức độ ưu tiên**: Thấp, Trung bình, Cao
- **Trạng thái**: Mặc định "Chưa hoàn thành"
- **Tính lặp lại**: Boolean cho công việc định kỳ

## Quy trình Refactor

### Giai đoạn 1: Phân tích Code Gốc
- Xác định các vi phạm Clean Code
- Liệt kê các vấn đề cần cải thiện
- Lập kế hoạch refactor từng bước

### Giai đoạn 2: Refactor Từng Bước
```bash
# Commit từng thay đổi nhỏ với message rõ ràng
git add .
git commit -m "feat: thêm validation cho input parameters"

git add .
git commit -m "refactor: tách phương thức validation riêng biệt"

git add .
git commit -m "refactor: tạo lớp TaskRepository cho database operations"
```

### Giai đoạn 3: Cải thiện Cấu trúc
- Tách biệt concerns (Model, Repository, Service)
- Áp dụng Design Patterns phù hợp
- Cải thiện error handling
- Thêm unit tests

## Hướng dẫn Chạy Code

### Yêu cầu
- Java 8 trở lên
- Thư viện json-simple

### Chạy ứng dụng
```bash
# Biên dịch
javac -cp ".:json-simple-1.1.1.jar" PersonalTaskManagerViolations.java

# Chạy
java -cp ".:json-simple-1.1.1.jar" PersonalTaskManagerViolations
```

## Các Nguyên tắc Clean Code Áp dụng

### 1. Single Responsibility Principle (SRP)
- Tách logic validation, database operations, business logic

### 2. Don't Repeat Yourself (DRY)
- Loại bỏ code trùng lặp trong validation và database operations

### 3. You Aren't Gonna Need It (YAGNI)
- Loại bỏ các tính năng không cần thiết trong phiên bản hiện tại

### 4. Meaningful Names
- Đặt tên biến, phương thức rõ ràng và có ý nghĩa

## Kế hoạch Phát triển

### Version 2.0
- [ ] Tách thành các lớp riêng biệt
- [ ] Thêm interface cho TaskRepository
- [ ] Implement Factory Pattern cho Task creation
- [ ] Thêm Exception handling tùy chỉnh

### Version 3.0
- [ ] Thêm GUI interface
- [ ] Database thật thay vì JSON file
- [ ] REST API endpoints
- [ ] Unit tests và Integration tests

## Contribution Guidelines

1. **Fork** repository
2. **Tạo branch** cho feature: `git checkout -b feature/ten-tinh-nang`
3. **Commit** thay đổi: `git commit -m 'feat: thêm tính năng mới'`
4. **Push** lên branch: `git push origin feature/ten-tinh-nang`
5. **Tạo Pull Request** với mô tả chi tiết

## Git Commit Convention

```bash
# Format: <type>(<scope>): <subject>

# Types:
feat: Tính năng mới
fix: Sửa bug
refactor: Refactor code
docs: Cập nhật documentation
test: Thêm tests
style: Formatting, thêm dấu chấm phẩy, etc.

# Examples:
git commit -m "feat(task): thêm validation cho due date"
git commit -m "refactor(database): tách DatabaseManager class"
git commit -m "fix(validation): sửa lỗi check duplicate task"
```

## License

Dự án này được phát triển cho mục đích học tập trong môn Công nghệ Phần mềm.

---

**Lưu ý**: Đây là dự án demo để học về Clean Code và Refactoring. Code hiện tại vẫn chứa một số vi phạm để phục vụ mục đích giảng dạy.