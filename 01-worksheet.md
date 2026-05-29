# Lab 02 — Worksheet: AI Product Scoping (Vin Smart Future)

---

## 🏛️ 1. Bối cảnh thực tế: Vin Smart Future (Vingroup)

**Vingroup** — Tập đoàn tư nhân lớn nhất Việt Nam — vừa sáp nhập toàn bộ các phòng ban công nghệ thuộc các công ty thành viên thành một đơn vị công nghệ thống nhất mang tên **Vin Smart Future**. 

Nhiệm vụ của **Vin Smart Future** là xây dựng các giải pháp AI, số hóa, và tự động hóa cốt lõi để nâng cao hiệu suất vận hành và trải nghiệm khách hàng xuyên suốt các công ty thành viên:
* 🚗 **VinFast:** Hệ thống xe điện thông minh (EV), trợ lý AI ảo trong xe, dự đoán bảo trì pin, và quản lý chuỗi cung ứng sản xuất.
* 🚕 **Xanh SM (GSM):** Vận hành đội xe taxi/xe máy điện thông minh, điều vận thông minh (Smart Dispatching), tối ưu hóa lộ trình di chuyển.
* 🏢 **Vinhomes:** Quản lý đô thị thông minh (Smart Cities), trợ lý cư dân thông minh, tối ưu hóa mức tiêu thụ năng lượng.
* 🏥 **Vinmec:** Y tế thông minh, chẩn đoán hình ảnh bằng AI, tối ưu hóa quản lý hồ sơ bệnh án.
* 🎢 **Vinpearl / VinWonders:** Trải nghiệm du lịch số hóa, quản lý phòng và luồng khách thông minh tại các khu vui chơi.

Trong buổi Lab hôm nay, nhóm của bạn sẽ đóng vai trò là **AI Product Engineer** tại **Vin Smart Future**, tiến hành tìm kiếm, scoping, phân tích độ khả thi, thiết lập ranh giới vận hành, và xây dựng một **bản mẫu kỹ thuật (prompt prototype)** cho một bài toán cụ thể thuộc một trong những mảng kinh doanh trên.

---

## 📊 2. Cơ cấu tính điểm bài lab

### 👥 Điểm nhóm (60 điểm)

| Gate | Điểm | Deliverable | Tiêu chí chấm |
|---|---:|---|---|
| **G1. Workflow Mapping** | 20 | Problem Deep-Dive | Vẽ chi tiết quy trình hiện tại: các bước, handoff, thời gian, bottleneck |
| **G2. Problem Statement** | 20 | Problem Deep-Dive | Problem Statement 6-field bám sát thực tế, metric có số và ranh giới rõ ràng |
| **G3. AI Fit & Future Flow** | 10 | Problem Deep-Dive | So sánh Rule vs LLM vs Agent, future flow có bước AI, ranh giới và Fallback |
| **G4. Decision Quality** | 10 | Problem Deep-Dive | Quyết định Go/Not Yet/No-Go trung thực và có chứng cứ rõ ràng |

### 👤 Điểm cá nhân (40 điểm)

| Gate | Điểm | Deliverable | Tiêu chí chấm |
|---|---:|---|---|
| **I1. Scan & Cards** | 15 | Quick Cards | Liệt kê 5 problems sử dụng 3 lenses, hoàn thiện 3 quick cards chất lượng |
| **I2. Prototyping** | 10 | 02-lab/ | Chạy thử nghiệm programmatic prompt prototype thành công |
| **I3. AI Log & Reflection** | 15 | 03-ai-log.md | Phản ánh trung thực về việc dùng AI làm thought-partner (giúp gì, sai gì, sửa gì) |

---

# 🚀 Phase 0 — worked Example: Xanh SM Intelligent Dispatcher (15 min)

*Giảng viên walk-through ví dụ thực tế từ Vin Smart Future để bạn hiểu rõ cách scoping một bài toán AI.*
Đọc chi tiết worked example tại file [02-deliverable-example.md](02-deliverable-example.md).

---

# 🔍 Phase 1 — SCAN (Cá nhân, 20 min)

Hãy sử dụng **4 Lenses** dưới đây để quét qua hoạt động vận hành của các công ty thành viên Vingroup. Ghi lại **ít nhất 5 bài toán/bottleneck** thực tế.

### 4 Lenses tìm bài toán AI cho Vingroup:
1. **Lặp lại (Repetitive):** Tác vụ lặp đi lặp lại nhiều lần hằng ngày. (Ví dụ: So khớp hóa đơn sạc điện tại VinFast, route lại chuyến taxi tại Xanh SM).
2. **Tốn thời gian (Time-consuming):** Tác vụ ngốn thời gian xử lý thủ công của nhân viên. (Ví dụ: Soạn thảo phản hồi đánh giá 1-star của cư dân Vinhomes).
3. **AI có thể tốt hơn (AI-upgrade):** Dịch vụ khách hàng hiện tại còn chậm hoặc phản hồi rập khuôn. (Ví dụ: Chatbot CSKH Vinpearl hỗ trợ đặt vé vui chơi).
4. **Pain từ người khác (Stakeholder Pain):** Bottleneck khiến khách hàng hoặc nhân viên thực địa phàn nàn. (Ví dụ: Tài xế Xanh SM phàn nàn về việc hệ thống gợi ý điểm đón khách không chính xác).

> [!TIP]
> **🤖 AI Prompts — Partner brainstorm:**
> Hãy sử dụng prompt sau để brainstorm các bài toán thực tế nếu bạn chưa có ý tưởng:
> *"Tôi là AI Engineer tại Vin Smart Future (Vingroup). Tôi đang tìm kiếm các pain point vận hành cụ thể có thể tối ưu bằng AI cho mảng [Chọn một: VinFast / Xanh SM / Vinhomes / Vinmec]. Hãy gợi ý cho tôi 5 quy trình nghiệp vụ thủ công, tốn nhiều thời gian và gây rò rỉ hiệu suất kèm con số thống kê ước tính về tổn thất."*

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

---

## 🃏 QUICK PROBLEM CARD #1: Phân Loại & Route Yêu Cầu Support Khách Du Lịch Vinpearl

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

---

> [!TIP]
> **🤖 AI Prompts — Stress-Test thẻ bài toán:**
> Hãy dán nội dung thẻ bài toán của bạn vào LLM để nhận phản biện:
> *"Đây là một thẻ bài toán vận hành tôi đề xuất cho Vin Smart Future: [Dán nội dung]. Hãy đóng vai trò là một CFO và Trưởng phòng Vận hành cực kỳ khắt khe, chỉ ra cho tôi 3 điểm yếu về logic, metric, và giải thích vì sao rule-based code thông thường có thể giải quyết bài toán này tốt hơn là dùng AI."*

---

# 🏗️ Phase 3 — DEEP-DIVE (Nhóm, 85 min)

## 3.1. Current-State Workflow Mapping (25 min)
**Vẽ quy trình hiện tại lên bảng/giấy A3.** Sử dụng các ký hiệu:
* 🔴 **Bottleneck:** Bước gây tắc nghẽn, tốn thời gian, hoặc sai sót nhiều nhất.
* 🔄 **Handoff:** Điểm chuyển giao thông tin giữa người và hệ thống, hoặc giữa các bộ phận.
* Ghi rõ thời gian vận hành trung bình: **Tổng cộng = ____ phút/lượt**.

## 3.2. Problem Statement (6-field) & Metrics (15 min)
Điền đầy đủ 6 trường thông tin của bài toán:

| Field | Nội dung chi tiết |
|---|---|
| **1. Actor / Operator** | Ai đang thực hiện tác vụ hằng ngày? |
| **2. Current Workflow** | Mô tả tóm tắt quy trình thủ công hiện tại và công cụ sử dụng. |
| **3. Bottleneck** | Bước nào chậm, lỗi, hoặc cần xử lý ngôn ngữ tự động nhiều nhất? |
| **4. Business Impact** | Tổn thất thực tế đo bằng thời gian, chi phí, hoặc SLA của Vingroup. |
| **5. Success Metric** | AI giải quyết được thì đạt ngưỡng số mấy? (Ví dụ: *"85% vé được phân loại dưới 10s"*). |
| **6. Operational Boundary** | AI được phép làm gì, TUYỆT ĐỐI không được làm gì, điểm nào cần duyệt? |

## 3.3. Future-State Flow & AI Fit (25 min)
* **Xác định mức AI Fit (AI-Fit Matrix):** Giải pháp thuộc nhóm nào? [ ] Rule / State-Machine [ ] LLM Feature [ ] Agentic Loop.
* **Vẽ Future-State Flow:** Đánh dấu rõ:
  * 🔵 **AI Step:** Tác vụ LLM xử lý.
  * 🟢 **Human Step (HITL):** Bước con người phê duyệt/review (Human-in-the-loop).
  * ↩️ **Fallback:** Kế hoạch dự phòng khi LLM trả về kết quả lỗi hoặc không tự tin.

---

# 💻 Phase 4 — TECHNICAL PROMPT PROTOTYPE (Nhóm, 30 min)

Để đảm bảo kỹ sư của Vin Smart Future luôn giữ vững năng lực lập trình, nhóm của bạn sẽ tiến hành **lập trình bản mẫu prompt** trực tiếp trên **Gemini 2.5 Flash** bằng Python để stress-test hệ thống.

### Hướng dẫn thực hiện:
1. Mở file [starter-code/prompt_prototype.py](starter-code/prompt_prototype.py) bằng VS Code/Cursor.
2. Hoàn thiện các nội dung sau:
   * **System Prompt:** Viết chỉ thị cực kỳ nghiêm ngặt quy định vai trò, nhiệm vụ, định dạng output và **Operational Boundary (Ranh giới cấm)** của mô hình.
   * **Structured Output:** Định nghĩa định dạng JSON output rõ ràng.
   * **Adversarial Test Cases:** Viết ít nhất 3 prompts "tấn công" (Adversarial inputs) cố tình dụ AI vượt ranh giới hoặc đưa ra câu trả lời không được phép để kiểm tra xem ranh giới của bạn có thực sự vững chắc.
3. Chạy file python:
   ```bash
   python3 prompt_prototype.py
   ```
4. Kiểm tra xem các ranh giới an toàn có bị LLM phá vỡ hay không và ghi lại kết quả vào worksheet.

---

# 🏁 Phase 5 — EVALUATE (Nhóm, 20 min)

### AI Readiness Checklist:
1. [ ] Chúng tôi có sẵn dữ liệu mẫu/logs sạch để test?
2. [ ] Rủi ro khi AI sai có nằm trong tầm kiểm soát (qua HITL hoặc Fallback)?
3. [ ] Stakeholders sẵn sàng thay đổi quy trình làm việc cũ?

### Quyết định cuối cùng của Ban Giám Đốc Vin Smart Future:
[ ] **GO (Bắt đầu xây dựng Prototype):** Bắt đầu phát triển với scope hẹp.
[ ] **NOT YET (Cần tích lũy thêm dữ liệu/xác lập baseline):** Trì hoãn để chuẩn bị thêm.
[ ] **NO-GO (Không khả thi / Rule-based tốt hơn):** Hủy bỏ dự án AI này.

**Justification (Lý giải quyết định dựa trên bằng chứng kỹ thuật và chi phí):**
> *Viết lý giải chi tiết tại đây*

---

# 📝 Phase 6 — REFLECTION (Cá nhân)
*Ghi nhận phản ánh của cá nhân bạn về việc phối hợp với AI trong buổi học hôm nay vào file `03-ai-log.md`.*
