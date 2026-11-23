# Danh sách lớp v0 — Nguyễn Thanh Sơn · G10

Viết tiếp từ slide 54 bài giảng. Mỗi lớp trả lời: **model cần nhận ra cái này để làm gì?**
Xóa 2 dòng ví dụ trước khi nộp.

## DMS (Driver Monitoring System – Giám sát người lái)

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng DMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | person | rectangle; seat: driver | Xác định vị trí người lái, làm vùng tham chiếu cho các tác vụ giám sát | Có, thường thấy được hình dáng cơ thể |
| 2 | face | rectangle | Xác định khuôn mặt người lái, làm vùng tham chiếu để phân tích trạng thái khuôn mặt | Có, nhưng có thể bị ảnh hưởng bởi bóng tối, vật che hoặc góc mặt |
| 3 | face13 | 13 facial landmarks | Xác định vị trí các bộ phận trên khuôn mặt để hỗ trợ phân tích mắt, mũi và miệng | Có thể, phụ thuộc chất lượng ảnh và độ rõ của khuôn mặt |
| 4 | eye_state | open / closed / unknown | Phát hiện dấu hiệu buồn ngủ thông qua trạng thái mắt, đặc biệt khi mắt nhắm trong thời gian dài | Có, nhưng kính phản xạ hoặc mắt bị che có thể khiến không xác định được |
| 5 | gaze_zone | Các vùng hướng nhìn theo guideline | Xác định người lái đang nhìn đường hay nhìn sang vị trí khác, phát hiện mất tập trung | Có thể, nhưng khó xác định chính xác khi mắt bị che hoặc ảnh IR phản xạ |
| 6 | glasses | yes / no / unknown | Nhận biết người lái có đeo kính hay không để hỗ trợ đánh giá độ tin cậy của nhận diện mắt | Có thể, nhưng khó phân biệt khi kính phản xạ ánh sáng IR |
| 7 | head_pose | Các hướng đầu theo guideline / unknown | Xác định hướng quay đầu của người lái, phát hiện hành vi quay đầu hoặc không quan sát đường | Có, có thể nhận biết tương đối qua hình dạng và hướng khuôn mặt |

## OMS (Occupant Monitoring System – Giám sát người ngồi trong xe)

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng OMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | person | rectangle | Phát hiện người ngồi trong xe, xác định số lượng và vị trí người trên các ghế | Có, thường thấy được hình dáng cơ thể |
| 2 | seat | driver / front_passenger / rear_left / rear_middle / rear_right | Xác định người đang ngồi ở vị trí ghế nào để quản lý trạng thái từng vị trí | Không phải thuộc tính hình ảnh độc lập; cần xác định vị trí tương đối trong cabin |
| 3 | seatbelt | worn_correct / worn_incorrect / not_worn / unknown | Kiểm tra tình trạng thắt dây an toàn để cảnh báo người ngồi chưa thắt hoặc thắt sai | Có thể, phụ thuộc độ tương phản, vị trí dây và chất lượng ảnh IR |
| 4 | child_seat | occupied: no / unknown | Xác định tình trạng ghế trẻ em để hỗ trợ giám sát việc sử dụng ghế an toàn | Có, có thể nhận biết hình dạng ghế; không tự suy diễn có trẻ nếu không đủ bằng chứng |
| 5 | infant_seat | facing: rear / front | Xác định ghế dành cho trẻ sơ sinh đang quay về phía trước hay phía sau để hỗ trợ kiểm tra lắp đặt an toàn | Có, thường nhận biết được hình dạng và hướng ghế nếu không bị che khuất |
| 6 | object | bag / box / cup / other | Phát hiện đồ vật trong cabin để hỗ trợ nhận biết vật dụng và tình trạng bên trong xe | Có thể, tùy hình dạng, độ tương phản và mức độ che khuất |
| 7 | phone | held / mounted / lap | Phát hiện điện thoại trong cabin, hỗ trợ nhận biết hành vi sử dụng điện thoại hoặc vị trí đặt điện thoại | Có thể, nhưng phụ thuộc kích thước, vị trí và độ rõ của vật thể |

## 2 câu hỏi leo thang

Câu hỏi bạn muốn hỏi người viết guideline (hoặc khách hàng) vì guideline v1.0 chưa trả lời. Mỗi câu kèm **tên khung** làm ví dụ.

1. 
- Câu hỏi: Khi người lái đeo kính và ánh sáng IR phản xạ trên tròng kính khiến không nhìn rõ một bên mắt, annotator nên gán trạng thái mắt bên đó là unknown hay có thể suy luận theo mắt còn lại?
- Khung ví dụ: D03 – ảnh real_IR có đốm phản xạ trên tròng kính che khuất mắt phải.
- Bạn tạm gán thế nào và vì sao: Gán mắt phải là unknown, không gán closed hoặc suy luận theo mắt trái vì không có đủ bằng chứng trực quan để xác định trạng thái mắt phải.
2. 
- Câu hỏi: Khi dây an toàn khó nhìn thấy trên ảnh RGB nhưng ảnh IR-sim thể hiện rõ hơn, annotator có được sử dụng ảnh IR-sim để xác nhận trạng thái dây an toàn hay chỉ sử dụng ảnh này để tham khảo?
- Khung ví dụ: S01_ir – ảnh IR-sim có độ sáng cao hơn ảnh RGB, trong khi ảnh RGB khá tối.
- Bạn tạm gán thế nào và vì sao: Chỉ ghi nhận trạng thái dây an toàn khi có bằng chứng trực quan đủ rõ. Nếu không xác định được thì gán unknown, không suy luận chỉ dựa trên độ sáng của ảnh IR-sim vì đây là ảnh xám mô phỏng, không phải ảnh IR thật.
