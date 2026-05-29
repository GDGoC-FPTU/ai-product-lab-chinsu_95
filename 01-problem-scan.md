🔍 Phase 1 — SCAN (Cá nhân, 20 min)
Hãy sử dụng 4 Lenses dưới đây để quét qua hoạt động vận hành của các công ty thành viên Vingroup. Ghi lại ít nhất 5 bài toán/bottleneck thực tế.

4 Lenses tìm bài toán AI cho Vingroup:
Lặp lại (Repetitive): Tác vụ lặp đi lặp lại nhiều lần hằng ngày. (Ví dụ: So khớp hóa đơn sạc điện tại VinFast, route lại chuyến taxi tại Xanh SM).
Tốn thời gian (Time-consuming): Tác vụ ngốn thời gian xử lý thủ công của nhân viên. (Ví dụ: Soạn thảo phản hồi đánh giá 1-star của cư dân Vinhomes).
AI có thể tốt hơn (AI-upgrade): Dịch vụ khách hàng hiện tại còn chậm hoặc phản hồi rập khuôn. (Ví dụ: Chatbot CSKH Vinpearl hỗ trợ đặt vé vui chơi).
Pain từ người khác (Stakeholder Pain): Bottleneck khiến khách hàng hoặc nhân viên thực địa phàn nàn. (Ví dụ: Tài xế Xanh SM phàn nàn về việc hệ thống gợi ý điểm đón khách không chính xác).
Tip

🤖 AI Prompts — Partner brainstorm: Hãy sử dụng prompt sau để brainstorm các bài toán thực tế nếu bạn chưa có ý tưởng: "Tôi là AI Engineer tại Vin Smart Future (Vingroup). Tôi đang tìm kiếm các pain point vận hành cụ thể có thể tối ưu bằng AI cho mảng [Chọn một: VinFast / Xanh SM / Vinhomes / Vinmec]. Hãy gợi ý cho tôi 5 quy trình nghiệp vụ thủ công, tốn nhiều thời gian và gây rò rỉ hiệu suất kèm con số thống kê ước tính về tổn thất."

### 📝 List bài toán của tôi:
| # | Subsidiary Vinhomes | Lens | Mô tả ngắn bài toán |
|---|----------------------------------|------|---------------------|
| 1 | Phê duyệt và Kiểm soát thi công nội thất | Time-consuming | Ban quản lý (BQL) phải kiểm tra thủ công xem bản vẽ có vi phạm kết cấu, hệ thống PCCC hay điện nước chung hay không. |
| 2 |Kiểm soát an ninh và Đỗ xe trái phép | Stakeholder Pain | Các camera an ninh không phân biệt được xe cư dân và xe ngoài, thường xuyên bỏ sót xe vi phạm |
| 3 |Phân loại và Điều hướng phản ánh trên App VinID/Vinhomes |Repetitive |Nhân viên CSKH thường xuyên phải đọc và điều hướng phản ánh của cư dân đến đúng phòng ban, tốn nhiều thời gian |
| 4 |Giám sát chất lượng dịch vụ vệ sinh và cảnh quan |AI-upgrade |Giám sát viên đi bộ quanh đại đô thị để kiểm tra xem rác có đầy không, cỏ có được cắt không, bể bơi có sạch không |
| 5 |Đối soát thanh toán phí dịch vụ và điện nước | Repetitive |Nhân viên phải đối soát thủ công danh sách căn hộ, diện tích, loại phí và số tiền trên bảng tính Excel, so sánh với dữ liệu trên hệ thống tính cước của tòa nhà |

🃏 Phase 2 — QUICK-ASSESS (Cá nhân, 30 min)
Chọn top 3 bài toán từ danh sách trên và hoàn thiện 3 Quick Problem Cards dưới đây (10 phút/card).

┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #01                                      │
│                                                             │
│ Bài toán (1 câu): Thẩm định tự động bản vẽ thi công nội     │
│ thất căn hộ nhằm phát hiện vi phạm kết cấu và PCCC.         │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [X] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Chuyên viên kỹ thuật Ban quản lý (BQL)  │
│ và Cư dân (chờ đợi duyệt hồ sơ lâu).                        │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Cư dân nộp bản vẽ (PDF/CAD) ──> 2. Kỹ thuật viên đối   │
│   soát thủ công với bản vẽ gốc tòa nhà ──> 3. Đánh dấu các │
│   vị trí vi phạm (nếu có) ──> 4. Phê duyệt/Từ chối & gửi   │
│   phản hồi lý do cho cư dân.                                │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2 (⏱ 120-180 phút/lượt)│
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2 và Bước 3      │
│ (Tự động quét bản vẽ, đối chiếu layout gốc và phát hiện     │
│ điểm bất thường).                                           │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│   Giảm thời gian thẩm định bản vẽ từ 3 ngày ──> dưới 15 phút│
│   Tỷ lệ phát hiện lỗi vi phạm kết cấu/PCCC đạt trên 95%.     │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [X] LLM  [X] Agent │
│ *Ghi chú: Sử dụng Multimodal LLM (Vision) kết hợp RAG để    │
│  đọc bản vẽ kỹ thuật và đối chiếu với tập luật SOP Vinhomes.│
└─────────────────────────────────────────────────────────────┘
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #02                                      │
│                                                             │
│ Bài toán (1 câu): Giám sát chất lượng vệ sinh và cảnh quan  │
│ đô thị theo thời gian thực.                                 │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [X] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Giám sát viên vận hành, Đội vệ sinh   │
│ (tránh bị khiển trách oan), Cư dân (cần môi trường sống    │
│ sạch đẹp).                                                  │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Giám sát viên đi bộ/lái xe quanh khu vực ──> 2. Phát    │
│   hiện rác đầy, cỏ chưa cắt hoặc bể bơi bẩn ──> 3. Ghi chú   │
│   vào sổ tay/điện thoại ──> 4. Gửi yêu cầu điều phối vệ sinh │
│   qua app nội bộ.                                           │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 1 (⏱ 3-4 giờ/ngày)   │
│ do diện tích đại đô thị rất lớn (hơn 100 ha).              │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 1 và Bước 2      │
│ (Sử dụng drone/camera AI phân tích ảnh, xác định vị trí      │
│ và mức độ bẩn/lộn xộn).                                   │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│   Tăng tần suất kiểm tra từ 1 lần/ngày ──> 3 lần/ngày cho  │
│   cùng diện tích. Giảm 40% khiếu nại của cư dân liên quan  │
│   đến vệ sinh.                                              │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [X] LLM  [X] Agent │
│ *Ghi chú: Agent điều khiển drone/webcam, sử dụng Vision LLM │
│  để phân tích hình ảnh và Agent điều phối công việc cho đội │
│  vệ sinh.
└─────────────────────────────────────────────────────────────┘
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #03                                      │
│                                                             │
│ Bài toán (1 câu): Tự động hóa kiểm định và báo cáo chất   │
│ lượng thi công nội thất căn hộ.
│                                                             │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [X] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Chuyên viên kỹ thuật Ban quản lý (BQL)  │
│ và Cư dân (chờ đợi duyệt hồ sơ lâu).                        │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Cư dân nộp bản vẽ (PDF/CAD) ──> 2. Kỹ thuật viên đối   │
│   soát thủ công với bản vẽ gốc tòa nhà ──> 3. Đánh dấu các │
│   vị trí vi phạm (nếu có) ──> 4. Phê duyệt/Từ chối & gửi   │
│   phản hồi lý do cho cư dân.                                │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2 (⏱ 120-180 phút/lượt)│
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2 và Bước 3      │
│ (Tự động quét bản vẽ, đối chiếu layout gốc và phát hiện     │
│ điểm bất thường).                                           │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│   Giảm thời gian thẩm định bản vẽ từ 3 ngày ──> dưới 15 phút│
│   Tỷ lệ phát hiện lỗi vi phạm kết cấu/PCCC đạt trên 95%.     │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [X] LLM  [X] Agent │
│ *Ghi chú: Sử dụng Multimodal LLM (Vision) kết hợp RAG để    │
│  đọc bản vẽ kỹ thuật và đối chiếu với tập luật SOP Vinhomes.│
└─────────────────────────────────────────────────────────────┘

