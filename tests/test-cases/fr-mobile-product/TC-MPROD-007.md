# TC-MPROD-007: Thêm vào giỏ hàng với số lượng chứa ký tự hỗn hợp (chữ và số)

## Requirement ID

FR-06 (Mobile)

## Module / Test type / Technique

Mobile-Product / Functional / Domain Testing – EP (COMBO-06)

## Preconditions

- Đang ở màn hình chi tiết sản phẩm `iPhone 15 Pro Max` trên Mobile App.

## Test data

| Field    | Value  |
| -------- | ------ |
| Số lượng | `"2a"` |

## Test steps

1. Nhập `"2a"` vào ô số lượng.
2. Nhấn nút **Thêm vào giỏ hàng**.

## Expected result

- Yêu cầu thất bại, hệ thống chặn việc thêm vì chứa ký tự phi số.

## Status / Related bugs

Fail / #13
