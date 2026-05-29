### 📝 List bài toán của tôi:
| # | Subsidiary | Lens | Mô tả ngắn bài toán |
|---|------------|------|---------------------|
| 1 | **Vinfast** | Lặp lại | Nhiều dòng xe điện có cấu trúc và linh kiện tương đồng nhưng QA team vẫn phải thực hiện full regression testing cho từng model mới |
| 2 | **Vinhomes** | Pain từ người khác (Stakeholder Pain) | Cư dân vô cùng bức xúc vì các yêu cầu sự cố phải chờ tới 3-5 ngày mới có thợ xử lý. Điểm nghẽn nằm ở khâu điều phối: ban quản lý phải dò tìm, khớp lịch rảnh và chuyên môn của từng thợ với mô tả lỗi của cư dân hoàn toàn thủ công. |
| 3 | **VinFast** | Tốn thời gian | Xử lý đơn khiếu nại bảo hành: so sánh video, ảnh, giấy tờ khách hàng với tiêu chuẩn công ty (mất 45 phút/case) |
| 4 | **Vinfast** | AI-upgrade | Dữ liệu kiểm thử xe hiện được lưu rời rạc giữa nhiều hệ thống và đội vận hành, chưa có AI hỗ trợ phân tích lỗi, gợi ý test case hoặc tái sử dụng tri thức kiểm thử |
| 5| **Vinfast** | Tốn thời gian | Tóm tắt lý do khách hàng hủy chuyến từ cuộc gọi ghi âm và ghi chú của tài xế để tìm pattern lỗi hệ thống |

---

# 🃏 Phase 2 — QUICK-ASSESS (Cá nhân, 30 min)

Chọn **top 3 bài toán** từ danh sách trên và hoàn thiện **3 Quick Problem Cards** dưới đây (10 phút/card).
```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                       │
│                                                             │
│ Bài toán: Quy trình kiểm thử xe điện VinFast lãng phí nguồn │
│ lực do phải lặp lại các bài test thủ công cho những module/ │
│ phần cứng dùng chung giữa các dòng xe.                      │
│ Công ty thành viên: [x] VinFast                             │
│                                                             │
│ Ai đang đau? Kỹ sư QA/Tester (quá tải), Validation Team     │
│                                                             │
│ Workflow thủ công hiện tại (4 bước):                        │
│   1. Nhận model xe mới, QA lên kế hoạch chạy bộ test        │
│   → 2. Đọc đối chiếu thủ công tài liệu kỹ thuật giữa 2 xe   │
│   → 3. Chạy full regression testing cả các module tương đồng│
│   → 4. Tổng hợp, review và báo cáo kết quả hoàn toàn bằng tay│
│                                                             │
│ Bước nào tốn nhất? Bước 2-3 (⏱ 40-50 giờ/kỳ release)        │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2-3              │
│ (Tự động phân tích similarity tài liệu -> Gợi ý tái sử dụng │
│  test case -> Khoanh vùng ưu tiên test để giảm rủi ro)      │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ Giảm 30% số lượng test case lặp lại thừa thãi. Rút ngắn thời│
│ gian regression testing từ 2 tuần ──> dưới 1 tuần/model.    │
│                                                             │
│ Quick Architecture: [x] LLM Feature (Phân tích & Gợi ý)     │
└─────────────────────────────────────────────────────────────┘
```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                       │
│                                                             │
│ Bài toán: Tối ưu hóa khâu phân tích sự cố và điều phối thợ  │
│ bảo trì nhằm giải quyết tình trạng cư dân chờ đợi 3-5 ngày. │
│ Công ty thành viên: [x] Vinhomes                            │
│                                                             │
│ Ai đang đau? Cư dân (bức xúc chờ đợi), Điều phối (quá tải)  │
│                                                             │
│ Workflow thủ công hiện tại (4 bước):                        │
│   1. Cư dân báo lỗi sự cố (điện, nước, điều hòa...) qua App │
│   → 2. Điều phối viên đọc mô tả để xác định loại chuyên môn │
│   → 3. Lật mở bảng Excel/hệ thống để dò tìm lịch rảnh và vị │
│        trí của từng thợ để khớp việc thủ công               │
│   → 4. Gắn việc cho thợ và thông báo lại lịch cho cư dân    │
│                                                             │
│ Bước nào tốn nhất? Bước 2-3 (⏱ 15 phút/lượt, gây tắc nghẽn│
│ dẫn đến backlog tồn đọng kéo dài 3-5 ngày)                  │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2-3              │
│ (LLM đọc hiểu text/ảnh lỗi -> Query database để tìm thợ phù │
│  hợp chuyên môn & lịch rảnh -> Tự động gợi ý ghép cặp)      │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ Xóa bỏ backlog chờ điều phối từ 3-5 ngày ──> dưới 2 giờ.    │
│ Rút ngắn thời gian gán việc thủ công xuống < 2 phút/ticket. │
│                                                             │
│ Quick Architecture: [x] LLM Feature (Đọc lỗi & Gợi ý thợ)   │
└─────────────────────────────────────────────────────────────┘
```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                       │
│                                                             │
│ Bài toán: Ách tắc quy trình xét duyệt bảo hành do kỹ thuật  │
│ viên phải đối chiếu thủ công ảnh/video với cẩm nang công ty.│
│ Công ty thành viên: [x] VinFast                             │
│                                                             │
│ Ai đang đau? Kỹ thuật viên (quá tải), Khách hàng (chờ đợi)  │
│                                                             │
│ Workflow thủ công hiện tại (4 bước):                        │
│   1. Nhận đơn khiếu nại bảo hành kèm file ảnh, video, giấy  │
│      tờ từ khách hàng hoặc xưởng dịch vụ                    │
│   → 2. Kỹ thuật viên mở xem từng ảnh/video bằng mắt thường  │
│   → 3. Lật tìm cẩm nang tiêu chuẩn bảo hành để đối chiếu xem│
│        lỗi này thuộc diện được bảo hành hay do người dùng   │
│   → 4. Viết báo cáo đánh giá và ra quyết định phê duyệt     │
│                                                             │
│ Bước nào tốn nhất? Bước 2-3 (⏱ 45 phút/case)              │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2-3              │
│ (Vision-LLM phân tích ảnh/video lỗi -> RAG truy xuất chéo   │
│  với cẩm nang bảo hành -> Draft báo cáo đối chiếu sơ bộ)    │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ Giảm thời gian kiểm tra và đối chiếu từ 45 phút ──> dưới 10 │
│ phút/case. Không có ca khiếu nại nào bị vượt quá hạn SLA.   │
│                                                             │
│ Quick Architecture: [x] LLM Feature (Vision-LLM & RAG)      │
└─────────────────────────────────────────────────────────────┘

---