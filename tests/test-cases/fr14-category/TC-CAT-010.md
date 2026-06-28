# TC-CAT-010: Admin xóa danh mục không tồn tại

## Requirement ID
FR-14, FR-12

## Module / Test type / Technique
Category / Functional / Domain Testing – EP (COMBO-10)

## Preconditions
- Người dùng đã đăng nhập với tài khoản Admin (`admin@eshop.com` / `Admin123!`)
- Danh mục có ID = `999` không tồn tại trong hệ thống
- Đang ở trang quản lý danh mục trên Web Admin

## Test data
| Field | Value |
|-------|-------|
| ID danh mục cần xóa | `999` |

## Test steps
1. Gửi request DELETE tới `http://localhost:3000/api/categories/999` kèm theo JWT Token của Admin.

## Expected result
- Yêu cầu thực hiện thành công nhưng không có thay đổi nào trong cơ sở dữ liệu (0 row bị ảnh hưởng).
- *Lưu ý:* API trả về phản hồi thành công và không báo lỗi không tìm thấy danh mục.

## Status / Related bugs
Not Run / None
