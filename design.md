# Thiết kế RESTful API - Hệ thống quản lý Task và User

## 1. Quản lý Người dùng (Users)
- **Lấy toàn bộ danh sách người dùng:**
    - `GET /users`
- **Tạo mới người dùng:**
    - `POST /users`
    - *(Body: Thông tin user dạng JSON)*
- **Cập nhật vai trò (role) của người dùng:**
    - `PATCH /users/{id}/role`
    - *(Body: {"role": "new_role"})*
- **Xóa một người dùng khỏi hệ thống:**
    - `DELETE /users/{id}`

## 2. Quản lý Công việc (Tasks)
- **Lấy toàn bộ danh sách công việc:**
    - `GET /tasks`
- **Tạo mới công việc:**
    - `POST /tasks`
    - *(Body: Thông tin task dạng JSON)*
- **Cập nhật trạng thái một công việc:**
    - `PATCH /tasks/{id}/status`
    - *(Body: {"status": "COMPLETED"})*
- **Xóa một công việc:**
    - `DELETE /tasks/{id}`

## 3. Các Endpoint truy vấn nâng cao và Liên kết (Foreign Key logic)
- **Tìm các công việc có mức độ ưu tiên là "high":**
    - `GET /tasks?priority=high`
- **Liệt kê toàn bộ công việc của 1 người dùng cụ thể:**
    - `GET /users/{userId}/tasks`
- **Tìm các công việc có độ ưu tiên là "high" và được giao cho người dùng với id là 1:**
    - `GET /users/1/tasks?priority=high`
- **Gắn công việc cho người dùng (Assign Task):**
    - `PATCH /tasks/{taskId}/assign`
    - *(Body truyền vào ID của người dùng: {"userId": 1})*