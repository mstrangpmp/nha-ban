2026-05-04-03 AI → Build → LHT Hub Setup Guide & Template (LHT Operations System)

Để chuẩn hoá đúng theo cách chị đang làm, em check file LHT.md hiện tại trước rồi đề xuất format phù hợp.File LHT.md chưa tồn tại — hợp lý vì đây là hệ thống chị đang thiết kế. Em sẽ làm đồng thời 2 phần: hướng dẫn tạo Hub + tạo sẵn template LHT.md.

**Phần 1: Các bước tạo Hub project mới**

Trong Cowork app, chị làm theo thứ tự sau:

Bước 1, tạo project mới: nhấn vào dropdown chọn project (góc trên) → "Create new project" → đặt tên _"LHT Operations Hub"_ → chọn folder gốc trên máy là `D:\LHTBrain\01_PROJECTS\` (hoặc tạo riêng `D:\LHTBrain\00_HUB\` để tách bạch hoàn toàn với folder dự án).

Bước 2, set project instructions: vào Settings của project mới → paste instruction sau:

> _"Đây là Hub điều phối trung tâm cho tất cả dự án của Ms Trang. File LHT.md ở thư mục gốc là single source of truth — chứa danh sách task của tất cả dự án đang chạy. Khi user yêu cầu cập nhật task, luôn thực hiện đồng bộ 3 nơi theo thứ tự: (1) cập nhật trạng thái trong LHT.md, (2) upload/link deliverable lên Google Drive, (3) cập nhật tiến độ tương ứng trên Notion. Luôn đọc LHT.md đầu phiên để nắm bối cảnh tổng. Không tự ý suy diễn task ngoài LHT.md."_

Bước 3, kết nối MCP: Settings → Connectors → enable Google Drive và Notion (sẽ tự kế thừa quyền đã xác thực từ Citek project, không cần đăng nhập lại).

Bước 4, copy file LHT.md (em tạo bên dưới) vào folder gốc của Hub.

**Phần 2: Template LHT.md**

Em đang tạo template với cấu trúc tối ưu cho cả người đọc + Claude parse tự động.Em đã tạo template tại đây — chị mở xem, chỉnh thông tin (Notion link, project codes, deadline) rồi lưu thành `LHT.md` ở folder gốc của Hub khi tạo xong:

[Xem LHT_template.md](https://claude.ai/local_sessions/local_8049f4eb-5436-4c3e-8b39-1deb88b53326)

**Logic thiết kế template (để chị hiểu vì sao em chọn cấu trúc này):**

Mỗi task có _task code_ (`CITEK-001`) — đây là chìa khoá để Claude tham chiếu chính xác giữa LHT.md ↔ Drive folder name ↔ Notion task name. Không có code thì Claude sẽ phải đoán bằng tên task, dễ sai khi tên dài hoặc trùng.

Status dùng ký hiệu trong dấu ngoặc vuông `[ ] [~] [!] [x] [-]` thay vì emoji — vì markdown checkbox parse được bởi cả Notion và GitHub-style markdown, đồng thời Claude regex match nhanh.

Section _"Quy ước cho Claude"_ nằm ngay trong file là chủ ý — không phải để đẹp mà để mỗi lần Claude đọc LHT.md là tự đọc luôn rule, không cần load thêm instruction. Tiết kiệm token và đảm bảo behavior nhất quán kể cả khi chị mở phiên mới.

Tách _Tasks_ và _Done log_ để dashboard luôn gọn — Claude khi liệt kê "việc hôm nay" sẽ chỉ scan section Tasks.

**Bước tiếp theo cho chị:**

1. Tạo Hub project trong Cowork theo 4 bước Phần 1 ở trên.
2. Sau khi tạo xong Hub folder (gợi ý `D:\LHTBrain\00_HUB\`), copy file `LHT_template.md` vào đó, rename thành `LHT.md`.
3. Điền 2–3 task thật cho Citek + dự án thứ 2 (nếu có) để test.
4. Mở phiên mới trong Hub project, gõ thử _"hôm nay làm gì"_ — nếu Claude trả lời đúng list task có Due trong 7 ngày là setup OK.

Nếu chị muốn em tinh chỉnh template (thêm field, đổi format status, hoặc đổi ngôn ngữ rule cho Claude), cứ nói cụ thể chị muốn sửa gì là em update.

**đặc biệt lưu ý: obsidian luôn là nơi chứa toàn bộ dữ liệu gốc. Drive là nơi dùng để collaboration xem và comment và notion là nơi để colab tiến độ. Nên các file md sẽ ko share. Chỉ share các deliverables như dự án Citek vừa làm.**
[[2026-05-04-04 AI → Refine → Three-Layer Sync Architecture (Obsidian-Drive-Notion)]]
