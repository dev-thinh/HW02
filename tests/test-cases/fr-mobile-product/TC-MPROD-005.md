# TC-MPROD-005: Thêm vào giỏ hàng với số lượng thập phân

## Requirement ID
FR-06 (Mobile)

## Module / Test type / Technique
Mobile-Product / Functional / Domain Testing – EP (COMBO-04)

## Preconditions
- Đang ở màn hình chi tiết sản phẩm `iPhone 15 Pro Max` trên Mobile App.

## Test data
| Field | Value |
|-------|-------|
| Số lượng | `"1.5"` |

## Test steps
1. Nhập số lượng `"1.5"` vào ô số lượng.
2. Nhấn nút **Thêm vào giỏ hàng**.

## Expected result
- Spec: Yêu cầu thất bại, chỉ nhận số nguyên dương.
- *Lưu ý (SUT Bug):* Trên ứng dụng thực tế, hệ thống vẫn báo "Thành công - Đã thêm vào giỏ hàng" và tự động làm tròn thành 1 để thêm vào giỏ (do `parseInt("1.5", 10)` trả về 1).

## Status / Related bugs
Not Run / None
