# TC-CAT-SEC-001: Thử tấn công Stored XSS bằng cách chèn thẻ <script>alert(1)</script> vào tên danh mục

## Requirement ID

FR-14

## Module / Test type / Technique

Category / Security / Domain Testing – Security Gap

## Preconditions

- Người dùng đã đăng nhập với tài khoản Admin (`admin@eshop.com` / `Admin123!`)
- Đang ở trang quản lý danh mục trên Web Admin (`http://localhost:5174`)

## Test data

| Field            | Value                       |
| ---------------- | --------------------------- |
| Tên danh mục mới | `<script>alert(1)</script>` |

## Test steps

1. Đăng nhập cổng Web Admin bằng tài khoản admin.
2. Điều hướng tới trang Quản lý danh mục.
3. Nhập tên danh mục: `<script>alert(1)</script>` vào ô nhập liệu.
4. Bấm nút **Thêm mới**.
5. F5 tải lại trang danh sách danh mục hoặc điều hướng sang trang khác rồi quay lại để tải dữ liệu danh mục từ cơ sở dữ liệu lên giao diện.

## Expected result

- Hệ thống từ chối tạo tên chứa thẻ script, hoặc nếu cho phép tạo thì chuỗi nhập vào phải được encode an toàn (HTML entity encoding) khi hiển thị trên giao diện.
- Không có hộp thoại cảnh báo (alert) nào xuất hiện (nghĩa là mã script không bị thực thi).

## Status / Related bugs

Pass / None (React tự động escaping chuỗi render trên giao diện nên mã script không bị thực thi).
