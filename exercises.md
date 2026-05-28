# Ngày 1 — Bài Tập & Phản Ánh
## Nền Tảng LLM API | Phiếu Thực Hành

**Thời lượng:** 1:30 giờ  
**Cấu trúc:** Lập trình cốt lõi (60 phút) → Bài tập mở rộng (30 phút)

---

## Phần 1 — Lập Trình Cốt Lõi (0:00–1:00)

Chạy các ví dụ trong Google Colab tại: https://colab.research.google.com/drive/172zCiXpLr1FEXMRCAbmZoqTrKiSkUERm?usp=sharing

Triển khai tất cả TODO trong `template.py`. Chạy `pytest tests/` để kiểm tra tiến độ.

**Điểm kiểm tra:** Sau khi hoàn thành 4 nhiệm vụ, chạy:
```bash
python template.py
```
Bạn sẽ thấy output so sánh phản hồi của GPT-4o và GPT-4o-mini.

---

## Phần 2 — Bài Tập Mở Rộng (1:00–1:30)

### Bài tập 2.1 — Độ Nhạy Của Temperature
Gọi `call_openai` với các giá trị temperature 0.0, 0.5, 1.0 và 1.5 sử dụng prompt **"Hãy kể cho tôi một sự thật thú vị về Việt Nam."**

**Bạn nhận thấy quy luật gì qua bốn phản hồi?** (2–3 câu)
> Khi temperature thấp như 0.0, mô hình tạo ra câu trả lời ổn định, ngắn gọn và ít thay đổi giữa các lần chạy. Khi temperature tăng lên 1.0 và 1.5, phản hồi trở nên sáng tạo hơn, đa dạng hơn nhưng cũng có xu hướng dài dòng và đôi khi kém nhất quán hơn.

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> Tôi sẽ chọn temperature khoảng 0.2–0.5 cho chatbot hỗ trợ khách hàng vì cần câu trả lời ổn định, chính xác và nhất quán giữa các người dùng. Temperature quá cao có thể khiến phản hồi sáng tạo nhưng dễ không đồng nhất hoặc sai lệch.

---

### Bài tập 2.2 — Đánh Đổi Chi Phí
Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> GPT-4o có giá input/output khoảng:Input: 5.00 / 0.150 ≈ 33 lần, Output: 20.00 / 0.600 ≈ 33 lần, Vì vậy tổng chi phí thực tế cũng xấp xỉ cao hơn khoảng 30–35 lần so với GPT-4o-mini cho cùng workload.

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
> GPT-4o phù hợp cho các tác vụ yêu cầu suy luận mạnh, chất lượng phản hồi cao hoặc phân tích phức tạp như trợ lý nghiên cứu, coding assistant hoặc xử lý tài liệu quan trọng. GPT-4o-mini phù hợp hơn cho chatbot thông thường, FAQ, phân loại dữ liệu hoặc ứng dụng cần tối ưu chi phí và độ trễ.

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
> Streaming đặc biệt quan trọng trong chatbot thời gian thực hoặc coding assistant vì người dùng thấy phản hồi xuất hiện ngay lập tức thay vì phải chờ toàn bộ kết quả hoàn thành, giúp giảm cảm giác delay và tăng trải nghiệm tương tác. Ngược lại, non-streaming phù hợp hơn khi cần xử lý hoàn chỉnh trước khi hiển thị, ví dụ như trả về JSON, báo cáo tổng hợp hoặc kết quả cần kiểm tra đầy đủ trước khi gửi cho người dùng.


## Danh Sách Kiểm Tra Nộp Bài
- [ ] Tất cả tests pass: `pytest tests/ -v`
- [ ] `call_openai` đã triển khai và kiểm thử
- [ ] `call_openai_mini` đã triển khai và kiểm thử
- [ ] `compare_models` đã triển khai và kiểm thử
- [ ] `streaming_chatbot` đã triển khai và kiểm thử
- [ ] `retry_with_backoff` đã triển khai và kiểm thử
- [ ] `batch_compare` đã triển khai và kiểm thử
- [ ] `format_comparison_table` đã triển khai và kiểm thử
- [ ] `exercises.md` đã điền đầy đủ
- [ ] Sao chép bài làm vào folder `solution` và đặt tên theo quy định 
