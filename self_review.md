# Tự đánh giá — Nguyễn Thanh Sơn · G10

## 1. Tự rà soát 4 cảnh

| Ảnh | Đối tượng | Loại lỗi | Ghi chú | Đã sửa? |
|---|---|---|---|---|
| S01 | person / face | `box` | Kiểm tra lại bounding box, đảm bảo bao sát đối tượng và không bị lệch khỏi vùng cần gán nhãn. | Có |
| S03 | child_seat / object | `missing` | Rà soát lại các đối tượng trong ảnh, tránh bỏ sót vật thể hoặc ghế trẻ em bị che khuất một phần. | Có |
| D01 | person / face | `flag` | Kiểm tra các landmark trên khuôn mặt, bổ sung cờ `occluded` hoặc `outside` khi điểm bị che khuất hoặc nằm ngoài vùng ảnh. | Có |
| D03 | seatbelt | `guess` | Không nên đoán trạng thái dây an toàn khi hình ảnh không đủ rõ; chuyển sang `unknown` nếu chưa có bằng chứng chắc chắn. | Có |

## 2. Lỗi mình lặp lại nhiều nhất hôm nay

**Lỗi:** `guess` – suy đoán nhãn khi hình ảnh không đủ rõ.

**Vì sao mình mắc:** Khi quan sát ảnh, đặc biệt là ảnh thiếu sáng hoặc có vùng bị che khuất, mình đôi khi dựa vào suy đoán thay vì chỉ sử dụng những thông tin thực sự nhìn thấy được. Điều này có thể dẫn đến gán sai trạng thái đối tượng.

**Lần sau tránh bằng cách:** Quan sát kỹ cả ảnh RGB và IR, đối chiếu các vùng tương ứng. Nếu không đủ căn cứ để xác định thì sử dụng `unknown` thay vì tự suy đoán. Đồng thời kiểm tra lại guideline trước khi đưa ra quyết định.

## 3. Ghi chú về disagreement_log

Một dòng bạn của mình đúng và mình sai: trường hợp đánh giá trạng thái `seatbelt`. Mình đã suy đoán trạng thái dây an toàn dựa trên vùng hình ảnh chưa rõ, trong khi bạn mình chọn `unknown` vì không đủ bằng chứng quan sát.

**Mình học được:** Khi gán nhãn DMS-OMS, không phải lúc nào cũng cần cố gắng đưa ra một trạng thái cụ thể. Nhãn `unknown` là lựa chọn cần thiết khi dữ liệu không đủ rõ. Quan trọng nhất là nhãn phải dựa trên bằng chứng trong ảnh và tuân thủ guideline, không dựa vào phỏng đoán cá nhân.
