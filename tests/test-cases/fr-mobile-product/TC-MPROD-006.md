# TC-MPROD-006: Thêm vào giỏ hàng với số lượng để trống hoặc chỉ có khoảng trắng

## Requirement ID

FR-06 (Mobile)

## Module / Test type / Technique

Mobile-Product / Functional / Domain Testing – EP (COMBO-05)

## Preconditions

- Đang ở màn hình chi tiết sản phẩm `iPhone 15 Pro Max` trên Mobile App.

## Test data

| Field    | Value             |
| -------- | ----------------- |
| Số lượng | `""` hoặc `"   "` |

## Test steps

1. Xóa trống ô số lượng (hoặc nhập khoảng trắng).
2. Nhấn nút **Thêm vào giỏ hàng**.

## Expected result

- Yêu cầu thất bại, hệ thống chặn việc thêm với số lượng trống.

## Status / Related bugs

Fail / #12
