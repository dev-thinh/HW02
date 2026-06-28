# TC-MPROD-010: Xem chi tiết sản phẩm khi sản phẩm không tồn tại (undefined)

## Requirement ID

FR-06 (Mobile)

## Module / Test type / Technique

Mobile-Product / Functional / Domain Testing – EP (COMBO-09)

## Preconditions

- Người dùng truy cập vào liên kết/id chi tiết sản phẩm không hợp lệ hoặc đã bị xóa khỏi hệ thống.

## Test steps

1. Mở màn hình chi tiết sản phẩm với ID không tồn tại.
2. Kiểm tra màn hình sau khi hệ thống phản hồi API không tìm thấy.

## Expected result

- Màn hình hiển thị thông báo lỗi thân thiện: "Sản phẩm không tồn tại (Lỗi trắng trang do data rỗng)".
- Hệ thống xử lý an toàn mà không bị crash trắng màn hình ứng dụng.

## Status / Related bugs

Pass / None
