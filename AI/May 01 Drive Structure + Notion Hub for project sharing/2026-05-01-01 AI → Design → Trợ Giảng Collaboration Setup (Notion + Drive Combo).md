primary vẫn là nội bộ, nhưng ko tránh khỏi vẫn gửi cho HR của Citek. Theo hướng combo thực tế bạn đã gợi ý nhé

OK, mình triển khai theo combo này. Phân vai rõ trước:

**Notion = "phòng làm việc trợ giảng"** — không gửi cho Citek HR. Dùng cho task tracking, brainstorm, prep notes, decision log, version history của các bản nháp. Citek không cần account.

**Drive (Google Drive hoặc OneDrive) = "kho deliverables"** — chứa file thật. Đây là nơi chị link tới khi cần share ra ngoài.

**Email + link Drive = "kênh gửi cho Citek HR"** — read-only, kèm tóm tắt 3-5 dòng. Mỗi lần gửi tạo thư mục riêng theo phiên bản để tránh KH mở nhầm bản cũ.

---

**Cấu trúc Notion Hub đề xuất**

Tạo 1 page gốc tên "Citek PM Training Hub" với cấu trúc sub-page như sau (chị có thể copy nguyên cấu trúc này vào Notion):

```
📂 Citek PM Training Hub
   ├─ 📋 Status & Tasks (Kanban: Backlog → Doing → Review → Done)
   ├─ 📝 Decision Log (mỗi quyết định 1 dòng + ngày + lý do)
   ├─ 🗂 Deliverables Index (link tới từng file trên Drive + ghi version)
   ├─ 💡 Notes & Brainstorm (prep ý tưởng, draft outline)
   ├─ 📨 Communication Log (lần nào gửi gì cho ai, kèm reply)
   └─ 📎 References (link tới khoá Cơ bản, PMBOK refs, SAP Activate)
```

Riêng "Deliverables Index" nên là 1 database table với cột: **Tên file · Loại · Version · Ngày cập nhật · Drive link · Trạng thái (Draft/Final/Archived) · Đã gửi Citek? (Y/N + ngày)**.

---

**Cấu trúc Drive đề xuất**

```
📂 Citek - PM Course Assistant/
   ├─ 01_Phan_Tich_Khao_Sat/      ← bộ hiện tại (00_README, 01-03, Report HTML)
   ├─ 02_Thiet_Ke_Khoa_Hoc/        ← outline 2 ngày (sẽ làm sau)
   ├─ 03_Slides_Bai_Giang/          ← deck final
   ├─ 04_Tai_Lieu_Hoc_Vien/         ← handout, exercise
   ├─ _Shared_with_Citek/           ← chỉ chứa bản đã gửi (clone từ thư mục chính)
   └─ _Archive/                     ← bản cũ deprecated
```

Quy tắc: **chỉ thư mục `_Shared_with_Citek/` mới được set "Anyone with link can view"**. Các thư mục khác giữ private — tránh KH vô tình lạc vào draft.

---

**Mẫu email gửi Citek HR**

```
Subject: [Citek PM Training] Báo cáo phân tích khảo sát Cấp độ Nâng cao – v1.0

Chị/Anh [tên HR],

Gửi anh/chị bản phân tích kết quả khảo sát năng lực PM ERP (Cấp độ Nâng cao)
sau khi tổng hợp 34 phản hồi. Bản này là input từ phía giảng viên/trợ giảng để
tham khảo khi chuẩn bị khoá học.

🔗 Link xem báo cáo (Drive, read-only):
   [link Drive folder _Shared_with_Citek/v1.0]

Nội dung chính:
   • Phát hiện then chốt (3 điểm)
   • Phân bố 4 nhóm học viên + định hướng cải thiện
   • Bảng chi tiết 34 người (mặc định ẩn tên — toggle ở góc phải)

Cách mở: tải file Report_Phan_Tich_*.html → double-click → mở trong browser.

Anh/chị có gì cần làm rõ hoặc muốn điều chỉnh, em sẵn sàng trao đổi thêm.

Trân trọng,
[chị Trang]
```

---

**Lưu ý vận hành**

Mỗi lần có version mới: tạo subfolder mới `v1.1`, `v2.0`... thay vì overwrite. KH nhận link cũ vẫn xem đúng bản đã được duyệt; khi gửi link mới mới có nội dung mới. Tránh lỗi "anh xem version nào, tôi xem version khác".

Cập nhật Notion "Communication Log" mỗi lần gửi — sau này tra lại nhanh: "Bản v1.0 mình gửi ngày nào, KH phản hồi gì, bản v1.1 thay đổi gì."

---

Nếu chị muốn, tôi đóng gói luôn 3 file template để chị copy:

1. Markdown template cho "Citek PM Training Hub" (paste vào Notion là ra cấu trúc)
2. CSV cho "Deliverables Index" (import vào Notion database)
3. File `.eml` hoặc `.txt` cho email template

Chị bảo cần file nào trong 3 cái thì làm.