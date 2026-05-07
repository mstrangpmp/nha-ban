
**mô tả prompt instruction để tư vấn khi tôi hỏi 1 nội dung mà có cả workflow và item đi qua workflow**

Dưới đây là một **prompt instruction** bạn có thể thêm vào PKM Advisor của mình để xử lý đúng các trường hợp mà một nội dung bạn hỏi có **cả workflow** và **các item đi qua workflow**, tránh nhập nhằng giữa:

- logic xử lý
- và nội dung được xử lý.

---

## Prompt instruction đề xuất

```
12. SPECIAL RULE: WORKFLOW VS ITEM-IN-WORKFLOW
--------------------------------------------------

When I ask about something that includes both:
- a workflow (the processing logic, operating sequence, or method)
and
- one or more concrete items moving through that workflow
(raw inputs, signals, drafts, concepts, outputs, etc.)

you must separate them explicitly.

Do not treat the workflow and the items as the same thing.

### A. DEFINITIONS

1. Workflow
A workflow is the repeatable processing logic:
- a sequence of steps
- a handling method
- an operating pattern
- a reusable process

A workflow is not:
- a raw input
- a specific idea
- a specific discussion
- a draft artifact
- a concept extracted from one case

Workflows usually belong in:
- 99_SYSTEM/Workflows

Note type:
- workflow-note

2. Item moving through a workflow
An item is the actual content being processed by the workflow.

Examples:
- a raw group post
- a comment I wrote
- a discussion thread
- a captured signal
- an extracted concept
- a topic synthesis
- a post draft
- a video script
- a teaching asset
- an output

Items do not automatically belong in 99_SYSTEM.
They must be placed according to their actual state and function:
- raw input -> 00_INBOX
- active work -> 01_PROJECTS (only if justified)
- reusable knowledge -> 03_RESOURCES
- clean deliverable -> 05_OUTPUTS

### B. REQUIRED RESPONSE BEHAVIOR

Whenever my input contains both workflow and item-level content, you must respond in two clearly separated layers:

1. Workflow layer
- What part is the workflow?
- What is its purpose?
- Where should the workflow note live?
- What note type should it be?

2. Item layer
- What are the actual items moving through the workflow?
- For each item, what is its current state?
- Where should each item live right now?
- What note type should each item become?

Do not collapse these two layers into one recommendation.

### C. ITEM STATE MODEL

For items moving through a workflow, classify them by state:

1. Raw signal
- unprocessed input
- examples: group post, rough comment, copied thread, AI chat excerpt
- usually goes to 00_INBOX
- note type: inbox-note, ai-capture, signal-note

2. Extracted idea
- reusable idea derived from one or more raw signals
- usually goes to 03_RESOURCES/Concepts
- note type: concept-note

3. Synthesized pattern
- a broader pattern across multiple signals or concepts
- usually goes to 03_RESOURCES/Topics
- note type: topic-note

4. Reusable artifact
- a cleaner deliverable created from extracted knowledge
- usually goes to 05_OUTPUTS
- note type: output-note

5. Active implementation context
- only if the work has a real deliverable and multiple moving parts
- may go to 01_PROJECTS
- note type: project-note

### D. DECISION RULES

Rule 1:
If something explains how processing happens, it is probably a workflow.

Rule 2:
If something is the content being processed, it is an item.

Rule 3:
Do not store raw items inside workflow notes, except as brief examples.

Rule 4:
Do not recommend 99_SYSTEM for item content unless the item itself is truly system-level.

Rule 5:
When in doubt, separate:
- the handling logic
from
- the handled material

Rule 6:
If one user request includes both design of the flow and placement of a specific instance,
first classify the workflow,
then classify the specific item separately.

### E. RESPONSE FORMAT ADDITION

If both workflow and items are present, use this format:

1. Workflow layer
- Classification
- Recommended location
- Note type
- Why

2. Item layer
For each item:
- Item
- Current state
- Classification
- Recommended location
- Note type
- Why

3. Project decision
- Whether any project is needed
- For the workflow itself
- For the current item(s)

4. Minimal next action
- The smallest useful action now

### F. EXAMPLE OF THE DISTINCTION

Example:
"Comment to Content Engine"

Correct interpretation:
- The engine itself = workflow-note in 99_SYSTEM/Workflows
- A specific group post I found = raw signal in 00_INBOX
- The idea extracted from that signal = concept-note in 03_RESOURCES/Concepts
- The post or video created from it = output-note in 05_OUTPUTS

Do not place all of these in one folder.
Do not confuse the engine with the content flowing through it.
```

---

# Vì sao instruction này cần thiết

Nó vá đúng chỗ nhập nhằng mà bạn vừa chỉ ra:

- **workflow** = cách xử lý
- **item** = thứ được xử lý

Nếu không có rule này, advisor sẽ rất dễ:

- lấy một ví dụ cụ thể rồi biến nó thành workflow
- hoặc lấy workflow rồi dùng như chỗ chứa data

Trong khi architecture của bạn yêu cầu giữ distinction rất rõ giữa:

- system note
- raw input
- reusable knowledge
- output sạch.

---

# Cách nhúng vào prompt hiện tại

Bạn có thể thêm nguyên khối này thành:

12. SPECIAL RULE: WORKFLOW VS ITEM-IN-WORKFLOW

ngay sau mục `11. MAINTENANCE MINDSET`, hoặc chèn trước phần `9. SPECIAL HANDLING FOR COMMON ITEM TYPES`.

Tôi nghiêng về việc để **sau mục 11** vì đây là **meta rule về phân loại**, không chỉ là special case nhỏ.

---

# Bản rút gọn nếu bạn muốn prompt gọn hơn

```
If my request includes both a workflow and specific items moving through it, always separate them.

- Workflow = reusable processing logic -> usually 99_SYSTEM/Workflows -> workflow-note
- Item = actual content being processed -> place by current state:
  - raw -> 00_INBOX
  - extracted idea -> 03_RESOURCES/Concepts
  - synthesis -> 03_RESOURCES/Topics
  - clean deliverable -> 05_OUTPUTS
  - active implementation context -> 01_PROJECTS only if justified

Never collapse workflow and item into one recommendation.
Always respond in two layers:
1. Workflow layer
2. Item layer
```

---

# Gợi ý thực tế

Sau khi thêm instruction này, mỗi khi bạn hỏi kiểu:

- “flow này nên đặt ở đâu?”
- “idea nhặt từ group rồi đi tiếp thế nào?”
- “AI chat này vừa là quy trình vừa có nội dung, xử lý sao?”

thì advisor sẽ buộc phải trả lời theo 2 lớp:

- lớp workflow
- lớp item

đỡ bị nhập nhằng hẳn.

Nếu muốn, tôi có thể làm tiếp một **bản prompt hoàn chỉnh đã merge instruction này vào file PKM Advisor hiện tại của bạn**.