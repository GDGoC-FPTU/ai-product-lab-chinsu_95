## 🏛️ Bối cảnh: Tôi là ai?

Tôi là **Nam**, AI Engineer tại **Vin Smart Future**. Nhóm chúng tôi được giao nhiệm vụ phối hợp với Khối QA/QC của **Vinfast** để tìm kiếm các cơ hội tối ưu hóa bằng trí tuệ nhân tạo. 

Quy trình kiểm thử xe điện tại VinFast đang có nhiều bước kiểm thử lặp lại giữa các dòng xe khác nhau dù nhiều module/phần cứng có cấu trúc tương đồng.

---

# 🔍 Phase 1 — SCAN: Tìm kiếm cơ hội (Cá nhân)

Dùng **4 Lenses** quét qua vận hành của các công ty thành viên Vingroup.

| # | Subsidiary | Lens | Mô tả ngắn bài toán |
|---|------------|------|---------------------|
| 1 | Vinfast | Lặp lại | Nhiều dòng xe điện có cấu trúc và linh kiện tương đồng nhưng QA team vẫn phải thực hiện full regression testing cho từng model mới.|
| 2 |  | Lặp lại | QA/QC và các phòng ban liên quan vẫn phụ thuộc vào quy trình giấy tờ thủ công như in tài liệu, xin ký xác nhận và đóng dấu qua nhiều cấp phê duyệt. |
|3| |AI-upgrade| Dữ liệu kiểm thử xe hiện được lưu rời rạc giữa nhiều hệ thống và đội vận hành, chưa có AI hỗ trợ phân tích lỗi, gợi ý test case hoặc tái sử dụng tri thức kiểm thử.
|4| |Tốn thời gian| Kỹ sư kiểm thử phải manually đối chiếu log lỗi, lịch sử kiểm thử và tài liệu kỹ thuật từ nhiều nguồn trước khi xác định nguyên nhân sự cố.
| 5 |  | Pain từ người khác | QA team (QA Engineer, PM tester...) phải mang nhiều giấy tờ để kiểm thử.|
| 6 | | Tốn thời gian | Tóm tắt lý do khách hàng hủy chuyến từ cuộc gọi ghi âm và ghi chú của tài xế để tìm pattern lỗi hệ thống. |

---

# 🃏 Phase 2 — QUICK-ASSESS: 3 Quick Problem Cards (Cá nhân)

```text
```md
# QUICK PROBLEM CARD — Lens 1
### Bài toán
Quy trình kiểm thử xe điện tại VinFast đang có nhiều bước kiểm thử lặp lại giữa các dòng xe khác nhau dù nhiều module/phần cứng có cấu trúc tương đồng.

### Ai đang đau
- QA Engineer
- Vehicle Test Engineer
- Validation Team
- PM Tester

### Workflow thủ công hiện tại
1. Khi có model xe mới, QA team tạo hoặc chạy lại bộ test.
2. Tester manually đối chiếu tài liệu kỹ thuật giữa các dòng xe.
3. Các module tương tự vẫn phải thực hiện full regression testing.
4. Kết quả test được tổng hợp và review thủ công.

### Bước nào tốn nhất
- Manual mapping giữa module cũ và module mới.
- Full regression testing cho các component tương đồng.
- Đọc và đối chiếu document kỹ thuật.

### AI có thể nhảy vào hỗ trợ bước nào
- Phân tích similarity giữa các module/phần cứng.
- Gợi ý reusable test cases.
- Prioritize test cases theo mức độ rủi ro.

### Đo thành công bằng gì
- Giảm số lượng test case bị lặp.
- Giảm thời gian regression testing.
- Giảm thời gian release validation.

### Giảm thời gian xử lý sự cố
- Giảm thời gian xác định test case cần chạy lại.
- Rút ngắn thời gian xác định module gây lỗi.

### Quick Architecture
LLM Feature

---

# QUICK PROBLEM CARD — Lens 3
### Bài toán
QA/QC và các phòng ban liên quan vẫn phụ thuộc vào quy trình giấy tờ thủ công như in tài liệu, xin ký xác nhận và đóng dấu qua nhiều cấp phê duyệt.

### Ai đang đau
- QA/QC Team
- PM Tester
- Engineering Manager
- Compliance Team

### Workflow thủ công hiện tại
1. In tài liệu kiểm thử.
2. Chuyển tài liệu qua nhiều phòng ban để ký xác nhận.
3. Theo dõi trạng thái approve bằng thủ công.
4. Scan/lưu trữ tài liệu riêng lẻ.

### Bước nào tốn nhất
- Chờ approve giữa nhiều phòng ban.
- Kiểm tra tính đầy đủ của hồ sơ.
- Tracking trạng thái document.

### AI có thể nhảy vào hỗ trợ bước nào
- Tự động kiểm tra document thiếu thông tin.
- OCR + extract dữ liệu từ biểu mẫu.
- Hỗ trợ classify document theo loại.

### Đo thành công bằng gì
- Giảm thời gian approval.
- Giảm số document thiếu thông tin.
- Giảm workload hành chính.

### Giảm thời gian xử lý sự cố
- Rút ngắn thời gian tìm kiếm document.
- Giảm delay do thiếu hồ sơ hoặc thiếu approve.

### Quick Architecture
Rule Agent

---

# QUICK PROBLEM CARD — Lens 5
### Bài toán
QA Engineer, PM Tester và đội kiểm thử hiện trường phải mang theo nhiều checklist, biểu mẫu và tài liệu giấy khi thực hiện quy trình test xe.

### Ai đang đau
- Field QA Engineer
- PM Tester
- Vehicle Validation Team

### Workflow thủ công hiện tại
1. In checklist kiểm thử.
2. Mang tài liệu đến khu vực test.
3. Ghi chú kết quả thủ công.
4. Chụp ảnh lỗi riêng lẻ.
5. Tổng hợp báo cáo sau khi hoàn tất kiểm thử.

### Bước nào tốn nhất
- Ghi chép thủ công ngoài hiện trường.
- Tổng hợp report sau khi test.
- Đồng bộ dữ liệu giữa các team.

### AI có thể nhảy vào hỗ trợ bước nào
- Digital checklist.
- Voice-to-report logging.
- Auto issue classification.

### Đo thành công bằng gì
- Giảm thời gian tạo report.
- Giảm lỗi nhập liệu thủ công.
- Tăng tốc độ đồng bộ dữ liệu.

### Giảm thời gian xử lý sự cố
- Report issue ngay tại hiện trường.
- Truy xuất nhanh lịch sử validation liên quan.

### Quick Architecture
No AI
```

```

---

# 🗳️ Quyết định lựa chọn của nhóm:
Nhóm quyết định chọn bài toán **"Card #2 — Xanh SM Xử lý sự cố sạc pin thực địa"** để thực hiện Deep-Dive.

## Lý do lựa chọn và loại bỏ các thẻ khác:
* **Card #4 (Vinhomes CSKH):** Mặc dù tốn thời gian nhưng rủi ro sai sót thông tin liên quan đến phí quản lý, tranh chấp căn hộ có thể dẫn đến khiếu nại pháp lý nặng cho Vinhomes. Cần gom thêm dữ liệu và xử lý bằng Rule-based router trước.
* **Card #6 (Xanh SM Hủy chuyến):** Đây là tác vụ phân tích offline (back-office), không ảnh hưởng trực tiếp đến hiệu suất vận hành thời gian thực (real-time) như sự cố hết pin của tài xế trên đường đón khách.

---

# 🏗️ Phase 3 — DEEP-DIVE (Nhóm)

## 3.1. Current-State Workflow
Quy trình xử lý sự cố hết pin thực địa hiện tại của điều phối viên Xanh SM:

```text
┌──────────────┐     ┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│ Bước 1       │     │ Bước 2       │     │ Bước 3       │     │ Bước 4       │
│ Nhận cuộc    │     │ Tra cứu định │     │ Tra cứu trạm │     │ Soạn văn bản │
│ gọi sự cố    │ ──→ │ vị GPS xe   │ ──→ │ sạc VinFast  │ ──→ │ hướng dẫn    │
│              │     │              │     │ còn trụ trống│     │ gửi tài xế   │
│ Ai: Dispatch │     │ Ai: Dispatch │     │ Ai: Dispatch │     │ Ai: Dispatch │
│ ⏱ 2 phút     │     │ ⏱ 2 phút     │     │ ⏱ 5 phút 🔴  │     │ ⏱ 5 phút 🔴  │
│ In: Điện thoại│     │ In: Biển số  │     │ In: Vị trí GPS│     │ In: Raw data │
│ Out: Log sự cố│     │ Out: Toạ độ  │     │ Out: Địa chỉ │     │ Out: SMS     │
└──────────────┘     └──────────────┘     └──────────────┘     └──────────────┘
                                                                      │
                                                                      ▼
                                                               ┌──────────────┐
                                                               │ Bước 5       │
                                                               │ Gọi xe cứu   │
                                                               │ hộ (nếu cần) │
                                                               │ Ai: Dispatch │
                                                               │ ⏱ 1 phút     │
                                                               └──────────────┘
🔴 = Bottlenecks
⏱ Tổng thời gian xử lý thủ công: 15 phút/lượt.
```

---

## 3.2. Problem Statement (6-field) — Vin Smart Future Standard

| Field | Nội dung |
|---|---|
| **1. Actor / Operator** | Điều phối viên (Dispatcher) thuộc Trung tâm Điều vận Xanh SM. |
| **2. Current Workflow** | Khi tài xế báo hết pin, điều phối viên tra cứu vị trí định vị trên bản đồ nội bộ, mở Dashboard trạm sạc VinFast để tìm trụ sạc trống gần nhất, viết tin nhắn chỉ dẫn/định vị gửi qua App tài xế, và gọi cứu hộ nếu pin dưới 5%. 5 bước, hoàn toàn thủ công, mất 15 phút/lượt. |
| **3. Bottleneck** | Bước 3 & 4 (mất 10 phút): Tra cứu thủ công trụ sạc trống phù hợp với dòng xe (VF5/VFe34/VF8) và soạn thảo tin nhắn hướng dẫn đường đi chi tiết bằng Tiếng Việt thân thiện. |
| **4. Business Impact** | Mỗi ngày có ~80 sự cố pin thực địa tại Hà Nội. Gây lãng phí 20 giờ làm việc/ngày của team điều vận. Tăng thời gian chờ đợi của tài xế, dẫn đến rò rỉ doanh thu ~15% do xe không thể đón khách và tài xế bị stress. |
| **5. Success Metric** | 1. Giảm tổng thời gian xử lý sự cố từ 15 phút xuống dưới 3 phút (Efficiency).<br>2. Tỉ lệ hướng dẫn đúng địa điểm và đúng loại trụ sạc phù hợp đạt 98% (Quality). |
| **6. Operational Boundary** | AI được phép truy xuất API định vị xe, API trạm sạc VinFast trống, tự động soạn thảo tin nhắn hướng dẫn dạng nháp (draft). **CẤM:** AI không được tự động gửi tin đi mà không có điều phối viên phê duyệt (Bắt buộc HITL); không được đề xuất trạm sạc không phù hợp với loại cổng sạc của xe. |

---

## 3.3. Future-State Flow & AI Fit

* **AI Fit:** Chọn **LLM Feature** (không cần Agent tự trị vì quy trình có cấu trúc cố định, rủi ro khi điều phối sai trạm sạc có thể khiến xe cạn kiệt pin giữa đường và gây tắc nghẽn giao thông).
* **Quy trình tương lai (Future-State):**

```text
┌──────────────┐     ┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│ Bước 1       │     │ Bước 2       │     │ Bước 3       │     │ Bước 4       │
│ Nhận cuộc    │     │ 🔵 Auto-pull │     │ 🔵 AI draft  │     │ 🟢 Dispatch  │
│ gọi sự cố    │ ──→ │ vị trí &     │ ──→ │ SMS chỉ dẫn  │ ──→ │ click duyệt  │
│              │     │ trạm sạc trống│    │ & chỉ đường  │     │ & gửi tài xế │
└──────────────┘     └──────────────┘     └──────────────┘     └──────────────┘
                                                                      │
                                                                      ▼
                                                               ↩️ Fallback:
                                                               Nếu AI draft lỗi,
                                                               Dispatcher tự viết
                                                               tay lại như cũ.
```

---
