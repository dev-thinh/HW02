# TC-MPROD-011: Xem chi tiết sản phẩm bị thiếu trường thông tin bắt buộc

## Requirement ID

FR-06 (Mobile)

## Module / Test type / Technique

Mobile-Product / Functional / Domain Testing – EP (COMBO-10)

## Preconditions

- Trong database tồn tại sản phẩm bị thiếu trường giá trị bắt buộc (ví dụ: thiếu ảnh hoặc thiếu giá `price`).

## Test steps

1. Mở màn hình chi tiết sản phẩm bị thiếu thông tin.
2. Kiểm tra hiển thị màn hình.

## Expected result

- Giao diện xử lý hiển thị bình thường bằng các giá trị mặc định (placeholder image, giá liên hệ, v.v.).

## Status / Related bugs

Pass / None
