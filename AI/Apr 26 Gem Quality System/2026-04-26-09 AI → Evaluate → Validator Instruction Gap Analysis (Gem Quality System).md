
**Hỏi: mình xác nhận lại là có những trường hợp kết quả GEM ko chính xác, mình muốn tìm chỗ trong spec đang có vấn đề để nâng cấp, bổ sung thêm trường hợp vụ thể là bổ sung gì, ở đâu để cover trường hợp mới, nhằm nâng cao chất lượng của GEM. Ví dụ vậy thì instruction bạn đưa ra đã đáp ứng chưa**

Chưa đáp ứng đủ. Instruction mình vừa viết thiên về **audit/report** — tìm lỗi và gắn nhãn — nhưng chưa có **upgrade loop**: từ lỗi → tìm đúng chỗ trong spec → đề xuất bổ sung cụ thể.

Để rõ hơn, đây là gap thực sự:

**Instruction cũ làm được:**

- Parse spec thành checklist tiêu chí
- Simulate hành vi Gem gốc
- Chấm Pass/Fail/Partial từng tiêu chí
- Gắn nhãn lỗi (ROLE_VIOLATION, FORMAT_VIOLATION…)

**Instruction cũ thiếu — đúng với mục tiêu của bạn:**

- Sau khi phát hiện lỗi → **pinpoint đúng dòng/đoạn nào trong spec** đang gây ra lỗi đó
- Phân tích tại sao đoạn đó không cover được ví dụ mới
- Đề xuất **text cụ thể** để bổ sung vào spec — không chỉ "nên sửa phần này"
- Chỉ rõ **vị trí chèn**: trước đoạn nào, sau đoạn nào, hay tạo section mới
- Phân biệt: lỗi do **spec thiếu** (cần thêm) vs lỗi do **spec sai** (cần sửa) vs lỗi do **spec mơ hồ** (cần làm rõ)

---

Nói cách khác, mục tiêu thật sự của bạn là một vòng khép kín:

```
Ví dụ lỗi → Tìm root cause trong spec → Đề xuất patch cụ thể → Spec tốt hơn
```

Mình cần thêm một **Bước 5 — Spec Patch** vào instruction, với format rõ ràng như sau:

```
LOẠI VẤN ĐỀ
  Spec thiếu / Spec sai / Spec mơ hồ

VỊ TRÍ TRONG SPEC
  Section: [tên section cụ thể]
  Đoạn hiện tại: "[trích nguyên văn]"

NGUYÊN NHÂN KHÔNG COVER ĐƯỢC VÍ DỤ NÀY
  [giải thích ngắn]

ĐỀ XUẤT BỔ SUNG / SỬA
  Chèn vào: [trước/sau đoạn nào, hoặc tạo section mới tên gì]
  Nội dung đề xuất:
  "[text mới viết sẵn, dùng được luôn]"
```