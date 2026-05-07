2026-05-04-07 AI → Refine → Three-Layer Sync Architecture (Obsidian-Drive-Notion)

À, đây là điểm cốt lõi mà em chưa nắm trước đó — cảm ơn chị clarify. Em điều chỉnh toàn bộ logic theo nguyên tắc này.

**Vai trò 3 nơi (đã sửa lại):**

- **Obsidian** = source of truth, _private_. Mọi file `.md`, file working, raw data đều nằm đây. **Không bao giờ rời Obsidian.**
- **Drive** = collaboration _với khách_. Chỉ chứa deliverable thành phẩm (html, docx, pptx, pdf) để khách xem/comment.
- **Notion** = collaboration _về tiến độ_. Page mỏng theo dõi task — không chứa nội dung deliverable, chỉ chứa trạng thái + link đến file Drive.

**Hệ quả với 3 file template em đề xuất:**

`LHT.md` và `00_README.md` của mỗi dự án **chỉ ở Obsidian** — không sync sang Drive, không copy nội dung sang Notion. Chúng là _bộ não cá nhân_ của chị, không phải tài liệu collab.

Notion page chỉ là _bảng theo dõi_ — mirror task list (đang làm / đã xong) + link tới deliverable trên Drive. Khi đồng đội/khách vào Notion, họ thấy "task này xong rồi, click link xem deliverable trên Drive" — không thấy file md gốc của chị.

Drive chỉ có 1 folder per dự án, chứa các deliverable đã _publish_. Working drafts vẫn ở Obsidian.

**Workflow mới khi chị báo "CITEK-001 xong":**

1. Em mở `Citek/00_README.md` trong Obsidian → tick task → move xuống "Đã xong" + ghi tên file deliverable.
2. Em upload (hoặc xác nhận đã có) file deliverable lên folder Drive của dự án đó. _Chỉ file deliverable_ — không upload `00_README.md` hay file working.
3. Em vào Notion page của dự án → tick task tương ứng → paste link Drive vào ô deliverable.
4. Em update `LHT.md` (Obsidian) — chuyển task từ "Tuần này" xuống "Vừa hoàn thành".
5. Báo lại chị: ✓ Obsidian, ✓ Drive (file X uploaded), ✓ Notion (link added).

So với version cũ — nguyên tắc sửa: **md files không bao giờ ra khỏi Obsidian.** Chỉ deliverable đi ra Drive.

**Hệ quả với Hub Cowork project:**

Workspace của Hub nên mount thẳng `D:\LHTBrain\` (toàn vault Obsidian) — không phải `00_HUB` riêng — để Claude đọc được cả `LHT.md` lẫn từng `00_README.md` của các dự án con. MCP Drive chỉ dùng để upload deliverable. MCP Notion chỉ dùng để update task status.

Project instructions của Hub nên thêm 1 dòng: _"Không upload file `.md` từ Obsidian lên Drive. Drive chỉ nhận deliverable định dạng html/docx/pptx/pdf/xlsx. Notion chỉ chứa task progress + link Drive, không paste nội dung deliverable."_

**Em check 1 điểm với chị trước khi update template:**

Khi chị viết draft (ví dụ outline khoá học) — chị viết nháp ở Obsidian dạng `.md` rồi _export_ ra docx/pdf để bỏ vào Drive cho khách comment? Hay chị viết thẳng trong docx/Google Docs ngay từ đầu? Cái này quyết định 2 thứ:

(a) Trong `00_README.md` deliverable nên ghi link tới đâu — file md trong Obsidian, hay file docx trên Drive, hay cả hai;

(b) Có cần thêm step "export md → docx" vào workflow không.

Chị trả lời cái này em viết lại template chuẩn xác cho cả 3 lớp.