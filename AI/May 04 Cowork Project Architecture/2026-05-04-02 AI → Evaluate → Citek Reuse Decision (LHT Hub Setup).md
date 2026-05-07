2026-05-04-02 AI → Evaluate → Citek Reuse Decision (LHT Hub Setup)

Câu trả lời thẳng: **được về mặt kỹ thuật, nhưng không nên về mặt chiến lược.** Em khuyên tạo project Hub mới.

**Vì sao kỹ thuật thì OK:**

MCP connectors trong Cowork thường ở 2 cấp — _user-level_ (như Google account của chị) và _project-level_ (cấp quyền cho project cụ thể được dùng connector đó). Account Notion và Drive đã xác thực thì khi tạo project mới chỉ cần "enable" lại, không phải đăng nhập từ đầu. Mất ~3–5 phút setup, không phải làm lại từ con số 0.

**Vì sao chiến lược thì không nên:**

Project Citek hiện đang có _project instructions_ khoá chặt vào vai trò: _"Trợ giảng khoá học với các nhiệm vụ từ phân tích khảo sát, soạn outline, làm proposal, nội dung slide giảng dạy."_ Mỗi lần chị mở phiên mới trong project này, Claude sẽ load instruction đó và _tự động giả định_ mọi yêu cầu đều thuộc context khoá học Citek. Khi chị ném vào 1 task của dự án khác (ví dụ làm báo cáo cho khách hàng X), Claude vẫn sẽ "nhuốm màu Citek" trong cách phản hồi — dẫn đến lệch tone, gợi ý không đúng domain, và tốn token để chị đính chính.

Thêm vào đó, tên project "Citek - PM Course Assistant" sẽ gây nhầm lẫn lâu dài: 6 tháng nữa chị nhìn vào dashboard Cowork, sẽ không phân biệt được "đây là project Citek thật sự" hay "hub điều phối tất cả".

**Đề xuất cụ thể:**

Tạo project mới tên "LHT Operations Hub" (hoặc "LHT Command Center"), enable lại Drive + Notion connectors (5 phút), copy file LHT.md vào folder của Hub. Project Citek hiện tại giữ nguyên — nó vẫn là 1 trong những "dự án con" mà LHT.md theo dõi. Khi chị làm việc liên quan trực tiếp đến nội dung khoá học Citek (soạn slide, làm outline...) thì vào Citek project; khi điều phối tổng hoặc xử lý dự án khác thì ở Hub.

**Trường hợp duy nhất nên reuse Citek:**

Nếu hiện tại chị _chỉ có Citek_ là dự án duy nhất đang chạy, và LHT.md cũng gần như chỉ track Citek, thì reuse được. Nhưng ngay khi có dự án thứ 2 xuất hiện trong LHT.md, chị nên tách ngay — càng để lâu càng khó migrate vì context Citek sẽ bám vào lịch sử hội thoại.

Chị muốn em hướng dẫn từng bước tạo Hub project mới và chuẩn hoá format LHT.md để Claude tự parse không?

**Đồng ý**
[[2026-05-04-03 AI → Build → LHT Hub Setup Guide & Template (LHT Operations System)]]
