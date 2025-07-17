# refactor-du-an
Thực hiện các commit rõ ràng trong quá trình refactor
tách các hàm ra thành 4 cho tuân thủ các nguyên tắc KISS, DRY, YAGNI:

Task.java – đại diện cho một nhiệm vụ.

TaskValidator.java – kiểm tra hợp lệ đầu vào.

TaskRepository.java – quản lý lưu/đọc file JSON.

PersonalTaskManager.java – quản lý logic thêm nhiệm vụ.

Dễ đọc – Dễ hiểu hơn (KISS)
Không lặp lại (DRY): Hàm kiểm tra input (isValidTitle, isValidPriority)
Dễ kiểm thử (Testability)
Loại bỏ tính năng không cần thiết (YAGNI)
Bỏ các phần:
UUID.randomUUID() (thay bằng thời gian)
isRecurring và recurrence_pattern (chưa dùng tới)
