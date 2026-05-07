tôi muốn làm 1 luồng tự động hoá công việc như sau: trong file [LHT.md](http://lht.md/) tôi sẽ update các công việc cần làm của các dự án. mỗi khi hoàn thành xong thì quay lại file này cập nhật kết quả, deliverables trên Drive, tiến độ trên Notion. Tôi nên tạo project mỗi dự án 1 project trong cowork hay quản lý chung tất cả dự án trong 1 project cowork để tăng hiệu suất và tiết kiệm token?

2026-05-04-01 AI → Recommend → Cowork Project Architecture (LHT Multi-Project Hub)

Câu trả lời ngắn: **nên dùng mô hình lai, ưu tiên 1 Cowork project trung tâm (Hub) làm "trạm điều phối" cho LHT.md, và CHỈ tách project riêng khi dự án đó có đặc thù đủ nặng.**

Lý do:

**Vì sao 1 Hub project là mặc định tốt hơn cho luồng LHT.md của chị Trang:**

LHT.md đang đóng vai trò _single source of truth_ — nếu tách nhiều Cowork project, mỗi project sẽ phải đọc/ghi cùng 1 file LHT.md, gây mâu thuẫn ngữ cảnh và dễ lệch trạng thái. Token tiết kiệm hơn ở Hub vì: project instructions chỉ load 1 lần, MCP connectors (Notion, Google Drive) chỉ kết nối 1 lần thay vì cấu hình lặp ở từng project, và Claude không phải "khởi động lại" hiểu biết về hệ thống làm việc của chị mỗi lần chuyển dự án. Với cùng 1 Notion workspace và cùng 1 Drive, việc chia project chỉ tạo overhead chứ không tăng hiệu suất.

**Khi nào tách project riêng (sub-project):**

Tách khi dự án có _ít nhất một_ trong các đặc điểm sau: (1) khách hàng/stakeholder khác biệt, cần bảo mật ngữ cảnh; (2) khối lượng tài liệu lớn (>20–30 file tham chiếu thường xuyên) sẽ làm "ô nhiễm" context của Hub; (3) cần bộ skill/connector chuyên biệt khác hẳn (ví dụ 1 dự án dùng Figma MCP, dự án khác dùng GitHub MCP); (4) chu kỳ dự án dài (>3 tháng) và sinh nhiều artifact riêng.

**Kiến trúc đề xuất cho chị:**

Hub project "LHT Operations" chứa LHT.md + workflow tự động hoá + kết nối Notion/Drive dùng chung. Mỗi dự án con là 1 _folder_ trong Hub (không phải project Cowork riêng), chứa tài liệu nặng và deliverables nháp. Khi 1 dự án nào đó "phình to" vượt ngưỡng (tiêu chí ở trên), mới promote nó lên thành Cowork project độc lập, và Hub chỉ giữ trạng thái tổng quan (link sang).

**Về token economy cụ thể:**

Token tốn nhiều nhất ở 2 chỗ: project instructions + file context được load. Hub gọn instructions có khi rẻ hơn nhiều project rườm rà. Nhưng nếu Hub phình ra >50 file tham chiếu thì lại đắt hơn — đó chính là tín hiệu cần tách. Quy tắc đơn giản: _"Tách khi đau, không tách trước khi đau."_

Nếu chị muốn, em có thể giúp thiết kế cụ thể: cấu trúc folder trong Hub, format chuẩn cho LHT.md (để Claude parse được tự động), và prompt mẫu để mỗi lần chị nói "update task X xong" thì em tự động cập nhật cả 3 nơi (LHT.md → Drive → Notion).

**nhưng hiện tại mình đang dùng project này (Citek) đã kết nối MCP với Drive và Notion. Liệu có thể dùng luôn project này làm LHT Operations hub ko?**
[[2026-05-04-02 AI → Evaluate → Citek Reuse Decision (LHT Hub Setup)]]
