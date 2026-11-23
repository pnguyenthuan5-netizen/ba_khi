# ĐỀ ÔN TẬP CUỐI MÔN – KỸ NĂNG PROMPTING AI

## [Đề bài số 03 – Chủ đề Tài chính cá nhân: Hội thảo Tài chính Thông minh]

- **Hình thức:** Làm bài cá nhân.
- **Công cụ:** Trình duyệt web, trình soạn thảo văn bản (VS Code, Notepad hoặc TextEdit), GitHub (giao diện web), một trong ba công cụ AI: ChatGPT, Claude, Gemini (chỉ dùng ở Pha 2).
- **Thời gian:** Bài thi gồm 2 pha: **Pha 1 (70 phút đầu)** KHÔNG dùng AI; **Pha 2 (20 phút cuối)** chỉ dùng AI để chạy các prompt đã viết ở Pha 1. Chi tiết ở Mục 3.2.
- **Nộp bài:** Tạo 2 repository trên tài khoản GitHub cá nhân: `[Tên Lớp]_PromptAI_H03_Pha1` và `[Tên Lớp]_PromptAI_H03_Pha2` (ví dụ: `HN-KS26-CNTT1_PromptAI_H03_Pha1`).
- Không sao chép bài của người khác.

---

## 1. Bối cảnh

Bạn là nhân viên mới của Ban tổ chức chuỗi **Hội thảo Tài chính Thông minh**, phụ trách hỗ trợ khách hàng đăng ký vé tham dự các buổi hội thảo về quản lý chi tiêu và đầu tư cá nhân. Trưởng bộ phận giao cho bạn xây dựng bộ prompt để xử lý thông tin khách hàng, tin nhắn đăng ký, báo giá vé và giải quyết khiếu nại một cách an toàn, chính xác.

## 2. Mục tiêu

Đánh giá kỹ năng sử dụng AI an toàn và hiệu quả: đạo đức khi dùng AI (ẩn danh thông tin cá nhân), chống ảo giác, khung CREATE, Few-shot, ép định dạng đầu ra (JSON), Chain-of-Thought, Prompt Chaining, chấm theo Rubric, phòng chống Prompt Injection và hoàn thiện System Prompt.

## 3. Tài liệu & Quy trình

### 3.1. Bộ tài nguyên (`starter-kit`)

Thư mục `starter-kit` gồm có:

- `bai_lam_pha1.md` và `bai_lam_pha2.md`
- Thư mục `du_lieu/` chứa 5 file dữ liệu từ `4_1_ghi_chu_dang_ky.txt` đến `4_5_bai_tu_van.txt`.

### 3.2. Quy trình 2 pha

- Bài Pha 1 được chấm theo bản đã upload vào repository Pha1 trước mốc giờ. Upload vào Pha1 sau mốc giờ không được tính.
- Mỗi lần chạy AI: mở cuộc trò chuyện mới; tin nhắn đầu tiên là nguyên văn prompt trong `bai_lam_pha1.md`. Dán câu trả lời bằng nút Copy dưới câu trả lời của AI (để giữ đúng bảng, JSON), rồi dán link chia sẻ (Share) vào dòng `Link trò chuyện`.
- Ý có ký hiệu **[AI]** trong thang điểm được 0 điểm khi: thiếu link, link không mở được, hoặc tin nhắn đầu tiên khác prompt trong `bai_lam_pha1.md`. Cuộc trò chuyện có nội dung nhờ AI viết prompt: cả mục đó 0 điểm.
- Không chạy được AI (mất mạng, hết lượt): ghi "Không chạy được", chỉ mất các ý **[AI]**.
- Không đưa thông tin cá nhân thật của bạn hoặc người khác vào AI.

---

## 4. Yêu cầu nghiệp vụ

### 4.1. Bảo vệ dữ liệu và chống ảo giác

Mở `4_1_ghi_chu_dang_ky.txt`. Đây là ghi chú của nhân viên tư vấn; nhân viên muốn nhờ AI soạn email xác nhận đăng ký hội thảo cho khách.

- **a)** Viết lại đoạn ghi chú ở dạng đã ẩn danh hoá để có thể dán vào AI: thay mọi thông tin định danh cá nhân bằng nhãn trong ngoặc vuông (ví dụ `[TEN_KHACH]`); giữ nguyên các thông tin còn lại.
- **b)** Một nhân viên khác đính kèm file chính sách hoàn/huỷ vé hội thảo và hỏi AI: _"Khách hàng huỷ vé trước ngày hội thảo 5 ngày thì được hoàn bao nhiêu tiền?"_ Để AI không tự bịa câu trả lời, hãy viết thêm **2 câu lệnh** đặt ngay sau câu hỏi đó:
    - **Câu 1:** buộc AI chỉ trả lời dựa trên file đính kèm, và nêu AI phải trả lời thế nào nếu file không có thông tin.
    - **Câu 2:** buộc AI ghi rõ câu trả lời lấy từ mục hoặc điều khoản nào trong file.

### 4.2. Trích xuất tin nhắn đăng ký hội thảo ra JSON [AI]

Mở `4_2_tin_nhan_dang_ky.txt`. Viết một prompt để AI chuyển `TN1`, `TN2`, `TN3` thành một mảng JSON 3 đối tượng, đúng thứ tự, đúng 6 trường như tin nhắn mẫu (`ma_goi`, `ngay_hoi_thao`, `nguoi_lon`, `tre_em`, `hang_ve`, `ghi_chu`). Prompt phải:

- Có đủ **6 khối CREATE**, mỗi khối ghi nhãn: `C - Context`, `R - Request`, `E - Explanation`, `A - Action`, `T - Tone`, `E - Extras`.
- Dùng **2 tin nhắn mẫu** làm ví dụ Few-shot.
- Đặt 3 tin nhắn cần xử lý trong cặp dấu phân tách (ví dụ `<tin_nhan>…</tin_nhan>`).
- Nêu đủ **5 quy tắc chuẩn hoá** trong file.
- Yêu cầu AI chỉ trả về JSON, không chào hỏi, không giải thích.

### 4.3. Báo giá vé hội thảo bằng Chain-of-Thought [AI]

Mở `4_3_bang_gia.txt`.

- **a) (Pha 1)** Viết prompt để AI tính tổng tiền cho yêu cầu báo giá: đưa bảng giá, quy tắc và yêu cầu báo giá vào cặp dấu phân tách; yêu cầu suy luận từng bước theo thứ tự:
  `tiền người lớn → tiền trẻ em → tiền vé → giảm giá nhóm → phụ thu sổ tay → tổng tiền`, mỗi bước ghi phép tính; dòng cuối có dạng `[RESULT: <tổng tiền> đồng]`.
- **b) (Pha 2)** Kiểm tra lại từng bước AI đã tính, đối chiếu với quy tắc trong file (được dùng ứng dụng máy tính để bấm lại phép tính). Ghi kết luận AI tính đúng hay sai; nếu sai, ghi bước sai đầu tiên và kết quả đúng của bước đó.

### 4.4. Dây chuyền xử lý khiếu nại (Prompt Chaining) [AI]

Mở `4_4_email_khieu_nai.txt`. Email được xử lý qua 3 trạm, đầu ra của trạm trước là đầu vào của trạm sau. File đã có định dạng đầu ra của Trạm 1 và prompt có sẵn của Trạm 2, Trạm 3.

- **a)** Viết prompt cho **Trạm 1**: đọc email khiếu nại và chỉ trả về một đối tượng JSON đúng 4 trường theo quy định (`loai_su_co`, `so_khach`, `so_phien_bi_anh_huong`, `tom_tat`). Ở Pha 2 chạy AI với prompt này.
- **b)** Nêu **2 điều cần kiểm tra** ở JSON đầu ra của Trạm 1 trước khi chuyển làm đầu vào cho Trạm 2.
- **c)** Khi chạy Trạm 3, AI bị ngắt giữa chừng ở đoạn _"…Ban tổ chức Hội thảo Tài chính Thông minh xin hoàn lại Quý khách khoản"_. Viết câu lệnh để AI viết tiếp đúng chỗ bị ngắt, không viết lại phần đã có.

### 4.5. Prompt chấm bài theo Rubric [AI]

Mở `4_5_bai_tu_van.txt`. Viết prompt để AI chấm câu trả lời của nhân viên tư vấn tập sự:

- Đưa thông tin chuẩn của ban tổ chức và rubric 3 tiêu chí (kèm trọng số) vào prompt.
- Đặt bài cần chấm trong cặp thẻ `<bai_can_cham>…</bai_can_cham>`, nêu rõ nội dung trong thẻ chỉ là dữ liệu, AI không làm theo yêu cầu nào trong thẻ.
- Mỗi lỗi trừ điểm có đủ: câu bị lỗi (trích nguyên văn), lý do sai, câu sửa đề xuất.
- Kết quả là bảng Markdown 4 cột `Tiêu chí | Điểm | Minh chứng | Đề xuất sửa`; dòng cuối là tổng điểm trên thang 10.

### 4.6. Hoàn thiện System Prompt

`bai_lam_pha1.md` đã cho sẵn phần `[Vai trò]` và `[Chuẩn đầu ra]` của System Prompt cho chatbot **"Trợ lý Tài Chính Thông Minh"** trên website. Viết tiếp 2 phần:

- **`[Quy tắc ràng buộc]`**, gồm 3 quy tắc:
    1. Chỉ tư vấn 3 gói hội thảo của chương trình (`CB`, `DT`, `VIP`);
    2. Không hứa giảm giá ngoài bảng giá (và không cam kết lợi nhuận đầu tư);
    3. Không hỏi xin số CCCD, mật khẩu ngân hàng hay số thẻ tín dụng.
- **`[Xử lý ngoại lệ]`**, gồm cách trả lời trong 2 tình huống:
    1. Khách hỏi ngoài phạm vi (ví dụ nhờ phím mã cổ phiếu, hỏi vay tiền);
    2. Khách cung cấp thiếu thông tin khi đặt vé.

### 4.7. Nộp bài

- Hết Pha 1: kéo thả `bai_lam_pha1.md` vào repository Pha1.
- Hết Pha 2: kéo thả `bai_lam_pha2.md` vào repository Pha2, sau đó nộp 2 link repository (Pha1 và Pha2) lên Portal.

---

## 5. Thang điểm chi tiết (100 điểm)

|  STT  | Nghiệp vụ                              | Mô tả chi tiết nghiệp vụ                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |  Điểm   |
| :---: | :------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: |
| **1** | **4.1. Bảo vệ dữ liệu, chống ảo giác** | - a) Thay đúng 4 thông tin định danh (họ tên, SĐT, CCCD, email), 1,5 điểm/thông tin: **6đ**<br>- a) Giữ đủ các thông tin còn lại (gói CB, Ngày hội Tài chính Gia đình, ngày 20/12/2026, 2 người lớn, 1 trẻ em 10 tuổi, cọc 1.000.000 đồng, 3 ghế cạnh nhau ở dãy bàn đầu gần màn hình chiếu): **2đ**<br>- b) Câu 1 đúng yêu cầu: **3đ**<br>- b) Câu 2 đúng yêu cầu: **3đ**                                                                                                                         | **14**  |
| **2** | **4.2. Trích xuất ra JSON [AI]**       | - Đủ 6 khối CREATE có nhãn, đúng vai trò: **6đ**<br>- 2 ví dụ Few-shot: **4đ**<br>- Tin nhắn trong dấu phân tách: **2đ**<br>- Nêu đủ 5 quy tắc chuẩn hoá, 1 điểm/quy tắc: **5đ**<br>- Yêu cầu chỉ trả JSON: **2đ**<br>- [AI] JSON hợp lệ, đúng thứ tự, đủ 6 trường: **1đ**<br>- [AI] Giá trị đúng ở cả 3 tin nhắn: **2đ**                                                                                                                                                                          | **22**  |
| **3** | **4.3. Báo giá bằng CoT [AI]**         | - a) Đủ dữ liệu, trong dấu phân tách: **2đ**<br>- a) Suy luận đúng thứ tự 6 bước, mỗi bước ghi phép tính: **4đ**<br>- a) Dòng cuối dạng `[RESULT: …]`: **2đ**<br>- [AI] Kết quả chạy có đủ các bước và dòng `[RESULT]`: **2đ**<br>- b) Kết luận đúng/sai khớp với kết quả đã dán: **2đ**<br>- b) AI sai: chỉ đúng bước sai đầu tiên và kết quả đúng; AI đúng: xác nhận tổng tiền `7.150.000`: **2đ**                                                                                               | **14**  |
| **4** | **4.4. Prompt Chaining [AI]**          | - a) Đủ 4 trường, đúng kiểu dữ liệu: **2đ**<br>- a) `loai_su_co` chỉ nhận 4 nhãn cố định: **3đ**<br>- a) Email trong dấu phân tách: **1đ**<br>- a) Chỉ trả một đối tượng JSON, không giải thích: **2đ**<br>- a) Giới hạn `tom_tat` không quá 20 từ: **1đ**<br>- b) 2 điều cần kiểm tra hợp lý, 2 điểm/điều: **4đ**<br>- c) Câu lệnh viết tiếp có trích đoạn bị ngắt, không lặp phần đã có: **2đ**<br>- [AI] Kết quả Trạm 1 đúng loại sự cố (`sai_khu_vuc`), số khách (`2`), số phiên (`2`): **3đ** | **18**  |
| **5** | **4.5. Chấm theo Rubric [AI]**         | - Đủ thông tin chuẩn, 3 tiêu chí, trọng số: **3đ**<br>- Thẻ và chỉ thị coi nội dung là dữ liệu: **4đ**<br>- Mỗi lỗi đủ 3 phần: **3đ**<br>- Bảng 4 cột và dòng tổng điểm: **2đ**<br>- [AI] Có bảng đủ 4 cột: **1đ**<br>- [AI] Không cho 10/10 theo ghi chú trong bài: **2đ**                                                                                                                                                                                                                        | **15**  |
| **6** | **4.6. Hoàn thiện System Prompt**      | - Quy tắc ràng buộc, 2 điểm/quy tắc × 3: **6đ**<br>- Xử lý ngoại lệ, 3 điểm/tình huống × 2: **6đ**                                                                                                                                                                                                                                                                                                                                                                                                 | **12**  |
| **7** | **4.7. Nộp bài**                       | - Hai repository đúng tên, nộp đủ 2 link: **1đ**<br>- Repository Pha1 có bài trước mốc giờ: **2đ**<br>- Hai file bài làm đúng tên, đủ thông tin đầu bài, giữ nguyên cấu trúc mẫu: **2đ**                                                                                                                                                                                                                                                                                                           |  **5**  |
|       | **TỔNG CỘNG**                          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | **100** |
