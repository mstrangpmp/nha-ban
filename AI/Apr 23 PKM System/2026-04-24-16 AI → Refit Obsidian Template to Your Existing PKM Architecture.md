

Bạn bắt rất đúng vấn đề cốt lõi:

> ❌ Hiện tại đang bị trộn giữa **“workflow”** và **“item đi qua workflow”**

Nếu không tách rõ chỗ này, hệ của bạn sẽ nhanh chóng:

- khó maintain
- khó reuse
- khó scale

---

# 🧠 I. Làm rõ ranh giới (đây là phần QUAN TRỌNG NHẤT)

## 1. Workflow là gì?

👉 Workflow = **cách bạn xử lý**

- không chứa nội dung cụ thể
- không chứa idea cụ thể
- không chứa raw data

📍 Ví dụ:

Comment → Discussion → Extract → Concept → Output

👉 Đây là:

- logic
- quy trình
- cách vận hành

→ thuộc **99_SYSTEM**

---

## 2. Idea / Item là gì?

👉 Item = **thứ đi qua workflow**

Ví dụ:

- 1 bài group
- 1 comment bạn viết
- 1 thread tranh luận
- 1 insight rút ra
- 1 post
- 1 video script

👉 Đây mới là:

- nội dung thật
- thứ cần lưu

---

# 🔥 II. Vấn đề trong gợi ý trước của tôi

Bạn đúng:

> Tôi đã **dùng template giống nhau cho 2 thứ khác nhau**

Cụ thể:

- “Comment Capture” bị đặt giống như workflow
- không rõ đâu là raw input, đâu là processed item

---

# 🎯 III. Tách lại cho rõ (version đúng hệ của bạn)

---

# 🧭 A. WORKFLOW NOTE (chỉ 1 cái duy nhất)

📍 Path:

99_SYSTEM/Workflows/Comment to Content Engine.md

---

## Nội dung chuẩn (chỉ logic, KHÔNG chứa item)

# Comment to Content Engine  
  
type:: workflow-note  
  
## Purpose  
Biến pain thật từ community thành content và knowledge tái sử dụng  
  
## Flow  
  
1. Find real pain in group  
2. Write comment (reframe)  
3. Observe replies / objections  
4. Capture signal (raw)  
5. Extract reusable idea (concept / topic)  
6. Convert to output (post / video)  
7. Reuse  
  
## Input  
- Group posts  
- Community discussion  
  
## Output  
- Concepts  
- Topics  
- Outputs (post, video)  
  
## Rules  
- Raw luôn đi vào INBOX  
- Concept phải tách riêng  
- Output phải sạch hơn raw

👉 DỪNG Ở ĐÂY  
👉 Không thêm gì nữa

---

# 📥 B. RAW INPUT (đầu vào workflow)

📍 Path:

00_INBOX/

---

## Template: COMMENT SIGNAL (đây là cái bạn thiếu clarity)

# Signal - {{short title}}  
  
type:: inbox-note  
status:: raw  
  
## Source  
- Group:  
- Link:  
- Keyword:  
  
## Original post (pain)  
-   
  
## My comment  
-   
  
## Replies / discussion  
-   
  
## Why this matters (quick note)  
- 

---

👉 Đây KHÔNG phải:

- concept
- workflow
- output

👉 Đây chỉ là:

> **tín hiệu thô từ thực tế**

---

# 🧠 C. EXTRACT → CONCEPT (sau workflow)

📍 Path:

03_RESOURCES/Concepts/

---

## Template

# {{Concept Name}}  
  
type:: concept-note  
  
## Definition  
-   
  
## Key Insight  
-   
  
## Derived from  
- [[Signal - ...]]  
  
## Usage  
- Teaching  
- Content  
- Thinking

---

👉 Đây là:

> thứ bạn có thể dùng lại 100 lần

---

# 🧩 D. SYNTHESIS → TOPIC (nếu có nhiều signal)

📍 Path:

03_RESOURCES/Topics/

---

# {{Topic Name}}  
  
type:: topic-note  
  
## Pattern observed  
-   
  
## Repeated pains  
-   
-   
  
## Misconceptions  
-   
  
## Related concepts  
- [[ ]]

---

👉 Đây là:

> “meta insight” từ nhiều comment

---

# 🚀 E. OUTPUT (sản phẩm sạch)

📍 Path:

05_OUTPUTS/

---

# Post - {{title}}  
  
type:: output-note  
  
## Source  
- [[Signal - ...]]  
- [[Concept - ...]]  
  
## Content  
-   
  
## Format  
- Text  
- Video

---

# 🔁 IV. Flow đúng (rất rõ ràng)

WORKFLOW (99_SYSTEM)  
        ↓  
RAW SIGNAL (00_INBOX)  
        ↓  
CONCEPT / TOPIC (03_RESOURCES)  
        ↓  
OUTPUT (05_OUTPUTS)

---

👉 Mỗi layer làm 1 việc  
👉 KHÔNG trộn

---

# 🧠 V. Nguyên tắc vàng (để không nhập nhằng nữa)

## 🔥 Rule 1

> Workflow KHÔNG chứa nội dung

---

## 🔥 Rule 2

> Inbox KHÔNG phải knowledge

---

## 🔥 Rule 3

> Concept KHÔNG chứa raw

---

## 🔥 Rule 4

> Output KHÔNG chứa messy context

---

# 🎯 VI. Minimal version (để bạn bắt đầu ngay)

Bạn chỉ cần:

### 1. 1 workflow note

→ 99_SYSTEM

### 2. 1 signal note mỗi ngày

→ 00_INBOX

### 3. 1 concept mỗi 2–3 ngày

→ 03_RESOURCES

### 4. 1 output mỗi ngày

→ 05_OUTPUTS

---

# 🧠 Insight cuối

Bạn vừa làm một việc rất quan trọng:

> phân biệt **system logic vs system data**

---

Nếu không tách chỗ này:  
→ system sẽ collapse khi scale

---

# 🚀 Nếu bạn muốn đi tiếp

Tôi có thể:

👉 audit toàn bộ flow này theo đúng vault của bạn  
👉 hoặc build **naming convention + tagging giúp query cực mạnh**

Chỉ cần nói:  
**“optimize naming + tagging”**