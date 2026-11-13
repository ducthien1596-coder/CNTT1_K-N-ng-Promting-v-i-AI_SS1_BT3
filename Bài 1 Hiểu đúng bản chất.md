
# Bài 1: Hiểu đúng bản chất
## Phần 1: Bóc tách nhận thức sai của Nam
### Sai lầm 1: Tưởng LLM là máy tính bỏ túi / có CPU tính toán bên trong
- Nam viết: "ChatGPT chắc chắn phải có bộ vi xử lý máy tính bên trong để tính toán chính xác 100%"
 - Sai hoàn toàn. LLM không có ALU, không chạy thuật toán cộng trừ như máy tính. Nó không thực thi phép tính, nó chỉ dự đoán văn bản.
### Sai lầm 2: Tưởng càng nhiều tham số thì càng tính toán giỏi
- Nam viết: "Hàng trăm tỷ tham số thì chắc chắn phải tính đúng phép tính tiểu học"
- Số tham số lớn chỉ giúp mô hình nhớ được nhiều mẫu ngôn ngữ hơn, không có nghĩa là nó biết quy tắc số học.
- Giải thích đúng theo Mục 2.1 Lesson 01:

    - LLM hoạt động bằng cơ chế Next Token Prediction - dự đoán token tiếp theo.
Khi Nam hỏi 15.480 + 28.750 = ?, mô hình không làm phép cộng. Nó sẽ nhìn vào chuỗi ký tự đã học được trong giai đoạn Pre-training và hỏi: "Sau chuỗi '15.480 + 28.750 =' thì chuỗi số nào có xác suất xuất hiện cao nhất trong dữ liệu văn bản trên internet?"
- Vì 44.130 và 44.230 giống nhau về mặt ký tự, mô hình dễ đoán nhầm token 1 thành 2. Nó sai do đoán từ theo xác suất, không phải do hỏng phần mềm.
- Nói đơn giản: LLM giỏi bắt chước cách con người viết đáp án, không giỏi tính đáp án.
## Phần 2: Sửa lỗi & Prompting - Cách bắt AI tính đúng 100%
Muốn tính đúng, đừng để AI tự đoán. Phải bắt nó dùng công cụ hoặc suy luận từng bước.
- Cách 1: Chuẩn nhất - Bắt dùng Code Interpreter / Python
 **Sử dụng dòng tin nhắn gửi cho AI phân tích và trả lời**
`Hãy dùng Python để tính chính xác phép tính sau, không tự nhẩm bằng suy luận ngôn ngữ. In ra code bạn đã chạy và kết quả cuối cùng:
15.480 + 28.750 = ?`
Khi có câu lệnh này, ChatGPT sẽ không đoán nữa mà sẽ chạy code print(15.480 + 28.750) và trả về 44.23 chính xác 100%.
- Cách 2: Nếu không có Code Interpreter - Bắt suy luận từng bước + tự kiểm tra
  - Hãy tính 15.480 + 28.750 bằng cách tách từng hàng: cộng phần nguyên với phần nguyên, cộng phần thập phân với phần thập phân, sau đó cộng tổng lại. Trình bày từng bước và kiểm tra lại kết quả 2 lần trước khi kết luận.

- Cách này giảm tỉ lệ sai đi rất nhiều, nhưng vẫn không đảm bảo 100% bằng Cách 1.
**Nguyên tắc nhớ cho bài này:**
Việc số học, tra cứu số liệu, tính tiền -> Luôn bắt AI dùng tool / dùng code / trích dẫn nguồn, đừng bao giờ để AI tự đoán bằng Next Token Prediction.
