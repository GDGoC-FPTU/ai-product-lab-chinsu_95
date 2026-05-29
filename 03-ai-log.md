Phase 1: 
Lần hỏi AI 1: 
#	Subsidiary	Lens	Mô tả ngắn bài toán
1	Xanh SM	Repetitive	Ghép cặp tài xế - khách hàng: nhân viên call center thủ công xác định tài xế gần nhất, gọi xác nhận. 500+ lần/ngày, mỗi lần 2-3 phút
2	Vinhomes	Time-consuming	Soạn thảo email phản hồi khiếu nại cư dân: CSKH mất 15-20 phút/email. ~100 email/ngày × 1500 phút = 25 giờ/ngày
3	VinFast	AI-upgrade	Tư vấn bảo trì xe: Chatbot hiện tại chỉ hỏi mẫu cứng. AI có thể dự báo từ GPS/dữ liệu pin để phòng chống trước
4	Vinmec	Pain từ Stakeholder	Bác sĩ ghi chép hồ sơ bệnh án sau khám: 10-15 phút/bệnh nhân × 500 bệnh nhân/ngày. Lãng phí thời gian khám bệnh
5	Vinpearl	Repetitive	FAQ support: 80% câu hỏi là về giá vé/giờ mở cửa/hủy vé. Nhân viên làm việc trên 5+ kênh đồng thời

Thấy phần trả lời đơn giản và trùng lặp ý tưởng nên đã prompt phần example để sáng tạo ra lần cuối là:

| # | Subsidiary | Lens | Mô tả ngắn bài toán |
|---|------------|------|---------------------|
| 1 | **Vinpearl** | Lặp lại | Phân loại yêu cầu hỗ trợ khách du lịch (đặt vé, hoàn tiền, lỗi kỹ thuật, phàn nàn) từ chat/phone hằng ngày. |
| 2 | **Vinhomes** | Pain từ người khác | Cư dân phàn nàn về thời gian chờ sửa chữa: yêu cầu bảo trì mất 3-5 ngày để được phân công thợ phù hợp. |
| 3 | **VinFast** | Tốn thời gian | Xử lý đơn khiếu nại bảo hành: so sánh video, ảnh, giấy tờ khách hàng với tiêu chuẩn công ty (mất 45 phút/case). |
| 4 | **Xanh SM** | AI-upgrade | Phát hiện tài xế mệt mỏi hoặc lái xe nguy hiểm qua dữ liệu GPS, tốc độ, hành vi phanh. |
| 5 | **Vinmec** | Tốn thời gian | Soạn đơn chỉ định xét nghiệm cho bệnh nhân dựa trên triệu chứng và hóa đơn (10-15 phút/đơn, 200+ đơn/ngày). |

và 

phase 2

**Bài toán (1 câu):** Tự động phân loại, ưu tiên, và route các yêu cầu support khách hàng từ chat/call/email đến team phù hợp (Đặt vé, Hoàn tiền, IT, Phàn nàn).

**Công ty thành viên:** [X] Vinpearl  [ ] VinFast  [ ] Xanh SM  [ ] Vinhomes  [ ] Vinmec

**Ai đang đau (Actor)?** 
Nhân viên Support Center Vinpearl (15-20 người) xử lý 200-300 yêu cầu/ngày trên 4 kênh (email, chat app, phone, Facebook). Hiện tại phải đọc từng yêu cầu để gán team thủ công, gây chậm trễ 1-2 tiếng trước khi khách được phục vụ.

**Workflow thủ công hiện tại (3-5 bước):**
1. Yêu cầu đến qua chat/email/phone
2. Support đọc, viết ghi chú, xác định category (Đặt vé/Hoàn tiền/Lỗi website/Phàn nàn)
3. Support gán thủ công cho team phù hợp (Booking team/Finance/IT/Management)
4. Team khác nhận ticket, chuẩn bị reply
5. Phản hồi được gửi lại khách (mất 2-3 tiếng từ bước 1 ➜ 5)

**Bước nào tốn thời gian/lỗi nhất?** 
Bước 2-3: Phân loại & gán team. Sai loại ➜ route sai team ➜ chuyển tiếp 1-2 lần ➜ phản hồi muộn. (⏱ 5-10 phút/yêu cầu × 250 yêu cầu/ngày = 1250-2500 phút/ngày = 20+ giờ/ngày)

**AI có thể nhảy vào hỗ trợ ở bước nào?**
Bước 2-3: Sử dụng LLM đọc nội dung yêu cầu → phát hiện intent (đặt vé, hoàn tiền, lỗi, khiếu nại) → gợi ý category + team. Hỗ trợ nhân viên review 1 giây, nhấn "Confirm" ➜ auto-route.

**Đo thành công bằng gì (Metric có số)?**
1. Giảm thời gian phân loại từ 5-10 min ➜ **dưới 30 giây** (LLM + human review)
2. Độ chính xác phân loại ≥ **92%** (hạn chế re-routing)
3. Giảm SLA từ 2-3 tiếng ➜ **< 45 phút** từ khi nhận yêu cầu đến lần reply đầu

**Quick Architecture:** [ ] No AI  [ ] Rule  [X] LLM  [ ] Agent

---

## 🃏 QUICK PROBLEM CARD #2: Tối Ưu Phân Công Bảo Trì Cư Dân Vinhomes

**Bài toán (1 câu):** Tự động phân công yêu cầu sửa chữa/bảo trì tới thợ phù hợp dựa trên loại sự cố, vị trí, và kỹ năng, thay vì để coordinator xử lý thủ công và khách phải chờ 3-5 ngày.

**Công ty thành viên:** [ ] VinFast  [ ] Xanh SM  [X] Vinhomes  [ ] Vinmec  [ ] Vinpearl

**Ai đang đau (Actor)?**
Cư dân sống tại Vinhomes phàn nàn về độ chậm: yêu cầu sửa điều hòa/ống nước/điện = chờ 3-5 ngày mới có thợ. Coordinator Vinhomes (8 người) phải gọi điện kiểm tra thợ, lịch làm việc, kỹ năng ➜ bottleneck lớn.

**Workflow thủ công hiện tại (3-5 bước):**
1. Cư dân gửi yêu cầu qua app Vinhomes Resident: "Điều hòa phòng ngủ không lạnh, block X2-10"
2. System tạo ticket, coordinator nhận
3. Coordinator gọi/SMS 5-10 thợ để kiểm tra: kỹ năng, lịch rảnh, khoảng cách từ vị trí hiện tại
4. Thợ xác nhận ngày giờ (thường là +2-3 ngày vì bận)
5. Cư dân được thông báo lịch hẹn qua app

**Bước nào tốn thời gian/lỗi nhất?**
Bước 3-4: Coordinator liên lạc thợ (lặp lại 3-5 lần/yêu cầu, mỗi lần 15-20 phút). Thợ thường bận ➜ phải chờ. (⏱ 45-90 phút/yêu cầu × 40 yêu cầu/ngày = 30-60 giờ/ngày coordinator chỉ gọi điện)

**AI có thể nhảy vào hỗ trợ ở bước nào?**
Bước 3-4: Sau khi cư dân gửi yêu cầu, system phân tích loại sự cố (NLP trích xuất "điều hòa", "block X2-10") → query database thợ lân cận có kỹ năng ➜ tự động gửi notification tới thợ, match lịch online. Human chỉ review & xác nhận.

**Đo thành công bằng gì (Metric có số)?**
1. Giảm thời gian phân công từ 45-90 min ➜ **< 5 phút** (LLM matching + tự động notification)
2. Tỉ lệ match thợ lần đầu ≥ **85%** (tránh thợ từ chối vì sai kỹ năng/lịch)
3. Giảm SLA từ 3-5 ngày ➜ **< 24 giờ** từ khi cư dân yêu cầu đến khi được lên lịch

**Quick Architecture:** [ ] No AI  [ ] Rule  [X] LLM  [ ] Agent

---

## 🃏 QUICK PROBLEM CARD #3: Tự Động Xử Lý Khiếu Nại Bảo Hành VinFast

**Bài toán (1 câu):** Sử dụng AI để phân loại, phân tích bằng chứng (ảnh, video, giấy tờ) và đưa ra quyết định bảo hành tự động, thay vì nhân viên QA phải xem từng case 45 phút.

**Công ty thành viên:** [X] VinFast  [ ] Xanh SM  [ ] Vinhomes  [ ] Vinmec  [ ] Vinpearl

**Ai đang đau (Actor)?**
Nhân viên QA (Quality Assurance) bộ phận Warranty VinFast phải review từng khiếu nại bảo hành: kiểm tra video xe gặp sự cố, so sánh với tiêu chuẩn công ty, phân loại (lỗi xe/lỗi khách/lỗi do bên thứ ba) ➜ thực hiện phức tạp, mỏi mắt, mất 45 phút/case × 50 case/ngày = 37.5 giờ/ngày.

**Workflow thủ công hiện tại (3-5 bước):**
1. Khách hàng gửi khiếu nại (email + 2-3 video/ảnh + giấy tờ hóa đơn)
2. QA staff nhận, xem video chi tiết (5-10 phút)
3. QA so sánh với tiêu chuẩn bảo hành: "Cáp cao áp có dây gãy = bảo hành được/không được" 
4. QA ghi nhận kết luận (Approved/Rejected/Need more info) + lý do viết 3-4 dòng
5. Gửi decision lại cho khách qua email

**Bước nào tốn thời gian/lỗi nhất?**
Bước 2-3: QA xem video + phân tích. Lỗi hay xảy ra vì QA xem nhanh, bỏ chi tiết hoặc áp dụng tiêu chuẩn không nhất quán. (⏱ 30-45 phút/case)

**AI có thể nhảy vào hỗ trợ ở bước nào?**
Bước 2-4: Sử dụng vision LLM (gemini-2.5-pro) để: (1) phân tích video/ảnh tìm vị trí lỗi, (2) phân loại loại sự cố (cáp, pin, khung gầm, electronics), (3) so sánh với warranty policy database ➜ gợi ý "Approve" hoặc "Reject" với confidence score. QA chỉ review & click "Confirm".

**Đo thành công bằng gì (Metric có số)?**
1. Giảm thời gian xử lý từ 45 min ➜ **3-5 phút** (AI analyze + human review)
2. Độ chính xác decision ≥ **90%** so với tiêu chuẩn warranty (validate qua 100 case sample)
3. Giảm SLA từ 7 ngày ➜ **1-2 ngày** khách nhận decision
4. Nhân viên QA giải phóng 30+ giờ/tuần để xử lý case phức tạp hoặc training

**Quick Architecture:** [ ] No AI  [ ] Rule  [ ] LLM  [X] Agent (LLM + policy database lookup + human review loop)
