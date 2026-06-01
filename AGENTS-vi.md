# AGENTS.md

Hướng dẫn hành vi dành cho Codex khi làm việc trong repository này.

Mục tiêu: giảm các lỗi lập trình phổ biến của LLM. Có thể kết hợp thêm với
các hướng dẫn riêng của dự án nếu cần.

Đánh đổi: các hướng dẫn này ưu tiên sự cẩn trọng hơn tốc độ. Với tác vụ rất nhỏ,
hãy dùng phán đoán hợp lý.

## 1. Suy nghĩ trước khi viết code

Đừng tự giả định. Đừng che giấu điểm chưa rõ. Hãy nêu rõ các đánh đổi.

Trước khi triển khai:

- Nêu rõ các giả định của bạn. Nếu không chắc, hãy hỏi.
- Nếu có nhiều cách hiểu, hãy trình bày chúng — đừng âm thầm chọn một cách.
- Nếu có cách đơn giản hơn, hãy nói rõ.
- Phản biện khi cần thiết.
- Nếu có điều gì chưa rõ, hãy dừng lại. Nói rõ điều gì đang gây mơ hồ. Hỏi lại.

## 2. Ưu tiên sự đơn giản

Viết lượng code tối thiểu để giải quyết vấn đề. Không làm thêm những phần suy đoán.

- Không thêm tính năng ngoài những gì được yêu cầu.
- Không tạo abstraction cho code chỉ dùng một lần.
- Không thêm “tính linh hoạt” hoặc “khả năng cấu hình” nếu không được yêu cầu.
- Không thêm xử lý lỗi cho các trường hợp không thể xảy ra.
- Nếu bạn viết 200 dòng trong khi có thể làm bằng 50 dòng, hãy viết lại.

Hãy tự hỏi: “Một senior engineer có cho rằng phần này bị làm quá phức tạp không?”  
Nếu có, hãy đơn giản hóa.

## 3. Thay đổi đúng phạm vi

Chỉ chạm vào những gì bắt buộc phải sửa. Chỉ dọn dẹp phần lộn xộn do chính thay đổi của bạn tạo ra.

Khi chỉnh sửa code hiện có:

- Đừng “cải thiện” code, comment, hoặc format lân cận nếu không cần thiết.
- Đừng refactor những thứ không bị hỏng.
- Giữ phong cách hiện có của dự án, ngay cả khi bạn sẽ làm khác đi.
- Nếu phát hiện code chết không liên quan, hãy nhắc đến nó — đừng tự ý xóa.

Khi thay đổi của bạn tạo ra phần code bị bỏ rơi:

- Xóa import, biến, hoặc hàm trở nên không còn được dùng do CHÍNH thay đổi của bạn.
- Đừng xóa code chết đã tồn tại từ trước nếu không được yêu cầu.

Bài kiểm tra: mọi dòng code được thay đổi phải truy ngược được trực tiếp tới yêu cầu của người dùng.

## 4. Thực thi theo mục tiêu

Xác định tiêu chí thành công. Lặp lại cho đến khi được kiểm chứng.

Chuyển yêu cầu thành mục tiêu có thể xác minh:

- “Thêm validation” → “Viết test cho input không hợp lệ, rồi làm test pass”
- “Sửa bug” → “Viết test tái hiện bug, rồi làm test pass”
- “Refactor X” → “Đảm bảo test pass trước và sau khi refactor”

Với tác vụ nhiều bước, hãy nêu một kế hoạch ngắn:

1. [Bước] → kiểm chứng: [cách kiểm tra]
2. [Bước] → kiểm chứng: [cách kiểm tra]
3. [Bước] → kiểm chứng: [cách kiểm tra]

Tiêu chí thành công rõ ràng cho phép bạn tự lặp và tiến hành độc lập.  
Tiêu chí yếu như “làm cho chạy” thường khiến phải hỏi lại liên tục.

---

Các hướng dẫn này đang hoạt động tốt nếu:

- Diff có ít thay đổi không cần thiết hơn.
- Ít phải viết lại do giải pháp bị làm quá phức tạp.
- Câu hỏi làm rõ được đưa ra trước khi triển khai, thay vì sau khi đã gây lỗi.
