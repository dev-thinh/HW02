# TC-MPROD-BVA-004: Thêm vào giỏ hàng với số lượng bằng 5 (NOM)

## Requirement ID

FR-06 (Mobile)

## Module / Test type / Technique

Mobile-Product / Functional / BVA (quantity NOM)

## Preconditions

- Đang ở màn hình chi tiết sản phẩm `iPhone 15 Pro Max` trên Mobile App.

## Test data

| Field    | Value |
| -------- | ----- |
| Số lượng | `"5"` |

## Test steps

1. Nhập số lượng `"5"` vào ô số lượng.
2. Nhấn nút **Thêm vào giỏ hàng**.

## Expected result

- Thêm vào giỏ hàng thành công.
- Badge icon giỏ hàng hiển thị số lượng cập nhật chính xác (+5).
- Khi điều hướng sang trang Giỏ hàng:
  - Tên sản phẩm hiển thị đúng (`iPhone 15 Pro Max`).
  - Đơn giá hiển thị đúng.
  - Số lượng hiển thị đúng bằng 5.
  - Nếu sản phẩm đã có sẵn trong giỏ trước đó, tổng số lượng của sản phẩm được cộng dồn (không tạo thêm dòng mới trùng lặp).

## Status / Related bugs

Pass / None
