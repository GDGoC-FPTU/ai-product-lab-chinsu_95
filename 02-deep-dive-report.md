### Phase 3 — DEEP-DIVE 

Quyết định lựa chọn: Nhóm thống nhất chọn bài toán Vinmec: Số hóa, trích xuất cấu trúc và tóm tắt hồ sơ bệnh án xuất viện để tiến hành Deep-Dive vì đây là bài toán có nỗi đau (pain point) cực kỳ lớn, cấu trúc rõ ràng và khả năng chứng minh ROI (Tỷ suất hoàn vốn) cao nhất.

# 3.1 Mô tả quy trình hiện tại

Quy trình tổng hợp hồ sơ xuất viện hiện tại của bác sĩ Vinmec:

┌──────────────┐    ┌──────────────┐    ┌──────────────┐    ┌──────────────┐
│ Bước 1       │    │ Bước 2       │    │ Bước 3       │    │ Bước 4       │
│ Nhận yêu cầu │    │ Tra cứu lịch │    │ Gõ tổng hợp  │    │ Ký duyệt &   │
│ xuất viện    │ ──→│ sử khám/xét  │ ──→│ các chỉ số   │ ──→│ phát hành    │
│ cho bệnh nhân│    │ nghiệm (log) │    │ vào biên bản │    │ hồ sơ        │
│ Ai: Bác sĩ   │    │ Ai: Bác sĩ   │    │ Ai: Bác sĩ   │    │ Ai: Bác sĩ   │
│ ⏱ 1 phút     │    │ ⏱ 10 phút 🔴 │    │ ⏱ 12 phút 🔴 │    │ ⏱ 2 phút     │
└──────────────┘    └──────────────┘    └──────────────┘    └──────────────┘
🔴 = Bottlenecks
⏱ Tổng thời gian xử lý thủ công: 25 phút/hồ sơ bệnh nhân.

# 3.2. Problem Statement (6-field) — Vin Smart Future Standard

| Field | Nội dung |
| --------------| -----------|
| 1. Actor/Operator | Bác sĩ điều trị/Bác sĩ trực cấp cứu tại hệ thống bệnh viện Vinmec.
| 2. Current Workflow |"Khi bệnh nhân xuất viện, bác sĩ phải tự lật giở hệ thống, đọc lại toàn bộ kết quả xét nghiệm, đơn thuốc, chẩn đoán trong nhiều ngày qua. Sau đó, họ gõ tay tổng hợp các chỉ số quan trọng, tiền sử bệnh nền và tình trạng lâm sàng vào biên bản xuất viện. 4 bước, hoàn toàn thủ công, mất trung bình 25 phút/ca."
| 3. Bottleneck |"Bước 2 & 3 (mất 22 phút): Khâu đọc chéo hàng tá kết quả xét nghiệm khác nhau và gõ lại văn bản tóm tắt vừa tốn thời gian, vừa tiềm ẩn nguy cơ bỏ sót các ghi chú nhỏ rải rác về dị ứng thuốc hoặc bệnh nền phụ."
| 4. Business Impact | "Bác sĩ bị vắt kiệt sức, lãng phí 2-3 giờ mỗi ngày chỉ để làm công tác hành chính thay vì thăm khám. Bệnh nhân phải chờ đợi rất lâu để nhận giấy tờ xuất viện, làm giảm nghiêm trọng chỉ số hài lòng khách hàng (CSAT) và gây ùn ứ giường bệnh."
| 5. Success Metric | "1. Giảm tổng thời gian xử lý hồ sơ xuất viện từ 25 phút xuống dưới 5 phút (Efficiency).2. Tỷ lệ bỏ sót các thông tin cảnh báo lâm sàng (dị ứng, bệnh nền) là 0% (Quality)."
| 6. Operational Boundary | "AI chỉ đóng vai trò ""Máy trích xuất & Tóm tắt văn bản"". CẤM: Tuyệt đối không được phép sinh ra các chẩn đoán bệnh mới, không được tự ý đưa ra phác đồ điều trị. HITL: Bắt buộc bác sĩ phải đọc duyệt toàn văn, chỉnh sửa (nếu cần) và ký điện tử xác nhận trách nhiệm y khoa cuối cùng trước khi phát hành."

# 3.3. Future-State Flow & AI Fit

Xác định mức AI Fit: Giải pháp thuộc nhóm [x] LLM Feature (Chỉ cần mô hình ngôn ngữ mạnh để xử lý text/ảnh OCR và tóm tắt, không cần Agentic Loop vì quy trình đi theo đường thẳng tuyến tính, không cần gọi API động liên tục).

Future-State Flow:

┌──────────────┐    ┌──────────────┐    ┌──────────────┐    ┌──────────────┐
│ Bước 1       │    │ Bước 2       │    │ Bước 3       │    │ Bước 4       │
│ Bác sĩ bấm   │    │ 🔵 AI Auto-  │    │ 🔵 AI sinh   │    │ 🟢 Bác sĩ    │
│ "Tạo hồ sơ   │ ──→│ pull & trích │ ──→│ Draft tóm tắt│ ──→│ đọc duyệt    │
│ xuất viện"   │    │ xuất dữ liệu │    │ diễn biến    │    │ & Ký xác nhận│
└──────────────┘    └──────────────┘    └──────────────┘    └──────────────┘
                                                              │
                                                              ▼
                                                              ↩️ Fallback:
                                                              Nếu AI trả về kết quả
                                                              ảo giác hoặc thiếu
                                                              dữ liệu, bác sĩ xóa
                                                              nháp và quay lại gõ
                                                              thủ công như cũ.

### Phase 5 — EVALUATE

# AI Readiness Checklist:

[x] Chúng tôi có sẵn dữ liệu mẫu/logs sạch để test?
(Có hệ thống hồ sơ bệnh án điện tử (EMR) lưu trữ lịch sử hàng ngàn ca bệnh để làm tập dữ liệu kiểm thử, có thể dễ dàng ẩn danh hóa thông tin cá nhân PII).

[x] Rủi ro khi AI sai có nằm trong tầm kiểm soát (qua HITL hoặc Fallback)?
(Kiểm soát tuyệt đối 100%. Quy trình được thiết kế "Human-in-the-loop": AI chỉ làm bản nháp, bác sĩ là người chịu trách nhiệm pháp lý ký duyệt. Bệnh viện không đối mặt rủi ro AI tự động gửi sai kết quả cho bệnh nhân).

[x] Stakeholders sẵn sàng thay đổi quy trình làm việc cũ?
(Bác sĩ cực kỳ ủng hộ vì đây là nỗi đau hành chính kéo dài nhiều năm, giải pháp này trực tiếp giải phóng sức lao động của họ).

-> Quyết định cuối cùng của Ban Giám Đốc Vin Smart Future:
[x] GO (Bắt đầu xây dựng Prototype)

# Justification (Lý giải quyết định dựa trên bằng chứng kỹ thuật và chi phí):

Về mặt kỹ thuật: Tóm tắt (Summarization) và trích xuất thực thể (NER) từ dữ liệu phi cấu trúc là thế mạnh tuyệt đối và ổn định nhất của các mô hình LLM hiện nay (như Gemini 1.5 Pro). Việc thiết lập ranh giới vận hành thông qua System Prompt hoàn toàn khả thi để ép mô hình tuân thủ quy tắc không chẩn đoán bậy.

Về mặt chi phí (ROI): Ước tính chi phí gọi API để xử lý toàn bộ text của một hồ sơ bệnh án dài dao động khoảng 500 - 1,500 VNĐ/ca. Trong khi đó, việc tiết kiệm được 20 phút làm việc của một bác sĩ chuyên khoa mang lại giá trị thặng dư khổng lồ (vài chục đến hàng trăm nghìn VNĐ/ca). ROI ngay lập tức đạt mức dương cực cao.

Về mặt vận hành: Thiết kế cổng kiểm soát bằng con người (HITL) giúp dự án vượt qua dễ dàng cổng kiểm duyệt pháp lý (Legal Gate) của bệnh viện.


