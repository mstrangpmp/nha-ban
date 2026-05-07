---
type: concept
domain: deep-learning
source: "[[Andrew-Ng-Deep Learning - Neural Networks and Deep Learning]]"
status: growing
---

# Continuous Value Prediction

**Tiếng Việt:** Dự đoán giá trị liên tục

**Layer:** L2 — Classical ML[cite: 2]

**⚡ Overlap:**
*   **L3a (Kiến trúc cơ bản):** Là loại đầu ra phổ biến nhất của các mạng nơ-ron thực hiện nhiệm vụ hồi quy[cite: 1].
*   **L0 (Math):** Liên quan đến tập số thực $\mathbb{R}$ trong toán học[cite: 1, 2].
## 🧠 Hiểu theo cách của mình

Kết quả đầu ra của Linear Regression có thể là bất kỳ số thực nào (Liên tục - Regression) **?? trong 1 khoảng xác định**.
Khác với dự đoán phân loại nhãn (Đúng/Sai hoặc Chó/Mèo) (Rời rạc - Classification).

Continuous Value Prediction là khái niệm "bài toán" regression, còn Linear Regression là 1 "phương pháp" giải quyết bài toán.

Ý nghĩa:
- **Định lượng chi tiết** -> có khả năng so sánh để đưa ra quyết định -> có giá trị kinh tế cao. Giải thích bằng tiếng Việt ý nghĩa của việc dự đoán con số 36.5 độ so với việc chỉ nói 'Nóng' hay 'Lạnh'.
- **Tỷ lệ với đầu vào**: có thể thuận/ nghịch (tuyến tính)
- **Giới hạn**: vì số thực có thể âm nhưng trong thực tế ko có -> khắc phục bằng hàm activate để triệt tiêu các giá trị nhỏ hơn 0.
- **Nền tảng cho deep learning**: các hidden layers bên trong mạng nơ-ron đều làm việc với số thực để truyền tải tín hiệu đi xa và phức tạp hơn.

## 📐 Công thức / Cơ chế


## 💡 Ví dụ / Ứng dụng

# 🧠 [Concept] Continuous Value Prediction



---

### 1️⃣ DỰ ĐOÁN GIÁ TRỊ LIÊN TỤC LÀ GÌ?

Trong **Linear Regression** (Hồi quy tuyến tính), dự đoán giá trị liên tục nghĩa là kết quả đầu ra ($y$) có thể là bất kỳ số thực nào trong một khoảng xác định[cite: 1].


Khác với dự đoán phân loại (chỉ ra nhãn Đúng/Sai hoặc Mèo/Chó), giá trị liên tục cho phép mô hình phản ánh mức độ tinh vi và chi tiết của kết quả[cite: 1].

---

### 2️⃣ ĐẶC ĐIỂM VÀ Ý NGHĨA CỦA CON SỐ ĐẦU RA

Con số mà mô hình dự đoán ra mang những ý nghĩa cốt lõi sau:


*   **Định lượng quy mô (Magnitude):** Con số này cho biết "bao nhiêu" hoặc "mức độ nào"[cite: 1]. Ví dụ: Ngôi nhà này đáng giá **5.2 tỷ** chứ không phải 5 tỷ hay 6 tỷ[cite: 1].


*   **Tỷ lệ thuận/nghịch với đầu vào:** Vì là mối quan hệ tuyến tính, ý nghĩa của số này thay đổi trực tiếp theo biến $x$[cite: 1]. Nếu diện tích tăng, con số giá nhà dự đoán sẽ tăng theo một tỷ lệ nhất định ($w$)[cite: 1].


*   **Khả năng so sánh:** Bạn có thể so sánh khoảng cách giữa các kết quả[cite: 1]. Ví dụ: Chênh lệch giữa căn nhà 4 tỷ và 5 tỷ là hoàn toàn có ý nghĩa về mặt kinh tế, giúp người dùng ra quyết định dựa trên ngân sách[cite: 1].


*   **Giới hạn thực tế:** Mặc dù về mặt toán học số thực có thể âm, nhưng trong máy học, con số này thường được ràng buộc bởi ý nghĩa thực tế[cite: 1]. Ví dụ: Giá nhà không thể âm, nên ta dùng hàm **ReLU** để triệt tiêu các giá trị nhỏ hơn 0[cite: 1].

---

### 3️⃣ VÍ DỤ MINH HỌA Ý NGHĨA SỐ THỰC

| Bài toán | Đầu ra ($y$) là số thực | Ý nghĩa của con số |
| :--- | :--- | :--- |
| **Bất động sản** | 7.500.000.000 | Số tiền cụ thể khách hàng phải trả[cite: 1]. |
| **Thời tiết** | 32.5 | Nhiệt độ chính xác tính bằng độ C[cite: 1]. |
| **Quảng cáo** | 0.85 | Xác suất (từ 0 đến 1) người dùng sẽ click vào quảng cáo[cite: 1]. |
| **Chứng khoán** | 125.20 | Giá trị cổ phiếu tại một thời điểm cụ thể[cite: 1]. |

---

### 4️⃣ TẠI SAO PHẢI LÀ SỐ THỰC?

*   **Tính chính xác cao:** Trong các lĩnh vực Lucrative (tạo ra nhiều lợi nhuận) như quảng cáo hay tài chính, việc biết một kết quả là 0.8 hay 0.9 có thể mang lại sự khác biệt hàng triệu đô la về mặt kinh tế[cite: 1].


*   **Nền tảng cho Deep Learning:** Hầu hết các tầng ẩn (Hidden Layers) bên trong mạng nơ-ron đều làm việc với các số thực liên tục để truyền tải tín hiệu đi xa hơn và phức tạp hơn[cite: 1].

---

### 5️⃣ PROMPT MÔ PHỎNG TRÊN GEMINI CANVAS
Copy prompt sau vào Gemini (chế độ Canvas):

"""
Tạo một canvas minh họa sự khác biệt giữa đầu ra Liên tục (Regression) và Rời rạc (Classification).
Yêu cầu:
- Bên trái vẽ một thước đo nhiệt độ cho thấy kim chỉ có thể dừng ở bất kỳ điểm nào (Số thực).
- Bên phải vẽ hai chiếc hộp 'Mèo' và 'Chó' (Phân loại).
- Giải thích bằng tiếng Việt ý nghĩa của việc dự đoán con số 36.5 độ so với việc chỉ nói 'Nóng' hay 'Lạnh'.
- Ngữ cảnh: Bài giảng Introduction to Deep Learning của Andrew Ng.
"""

---
**Gợi ý học tiếp:** Bạn có muốn tìm hiểu về cách **Activation Functions** (như Sigmoid) biến đổi một số thực bất kỳ về khoảng [0, 1] để dự đoán xác suất không? (Nhánh **3a — Kiến trúc cơ bản**)[cite: 1].
# **Status có 3 mức:**
- `seedling` 🌱 — vừa tạo, nội dung còn sơ sài
- `growing` 🌿 — đã điền nội dung, chưa review lại
- `evergreen` 🌳 — đã nắm chắc, đã review
