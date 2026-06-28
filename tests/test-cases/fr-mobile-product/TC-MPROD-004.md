# TC-MPROD-004: Thêm vào giỏ hàng với số lượng âm

## Requirement ID

FR-06 (Mobile)

## Module / Test type / Technique

Mobile-Product / Functional / Domain Testing – EP (COMBO-03)

## Preconditions

- Đang ở màn hình chi tiết sản phẩm `iPhone 15 Pro Max` trên Mobile App.

## Test data

| Field    | Value  |
| -------- | ------ |
| Số lượng | `"-3"` |

## Test steps

1. Nhập số lượng `"-3"` vào ô số lượng.
2. Nhấn nút **Thêm vào giỏ hàng**.

## Expected result

- Yêu cầu thất bại, hệ thống chặn việc thêm vào giỏ hàng với số lượng âm.

## Status / Related bugs

Fail / #10
