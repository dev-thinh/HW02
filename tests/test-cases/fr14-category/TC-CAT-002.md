# TC-CAT-002: Admin tạo danh mục trùng tên

## Requirement ID
FR-14

## Module / Test type / Technique
Category / Functional / Domain Testing – EP (COMBO-02)

## Preconditions
- Người dùng đã đăng nhập với tài khoản Admin (`admin@eshop.com` / `Admin123!`)
- Đang ở trang quản lý danh mục trên Web Admin
- Danh mục `Điện thoại` đã tồn tại trong hệ thống

## Test data
| Field | Value |
|-------|-------|
| Tên danh mục mới | `Điện thoại` |

## Test steps
1. Nhập tên danh mục: `Điện thoại` vào ô nhập liệu.
2. Bấm nút **Thêm mới**.

## Expected result
- Danh mục được tạo thành công với một ID mới (mặc dù trùng tên với danh mục đã có).
- *Lưu ý:* Hệ thống SUT hiện tại cho phép tạo trùng tên danh mục do không có ràng buộc UNIQUE trong DB.

## Status / Related bugs
Not Run / None
