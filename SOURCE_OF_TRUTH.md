# 🏠 SOURCE OF TRUTH — Dự Án BDS Khang Ngô Nhà Phố

> **Mục đích:** File này là nguồn thông tin duy nhất (single source of truth) cho toàn bộ dự án website bất động sản của Khang Ngô Nhà Phố. Mọi thay đổi cần được ghi chép lại ở đây.

> **Cập nhật lần cuối:** 2026-05-10

---

## 0. 🔄 WORKFLOW — Cách Làm Việc Với AI

### Mỗi khi bắt đầu session mới, nói với AI:

> *"Đọc SOURCE_OF_TRUTH tại `d:\LHTBrain\01_PROJECTS\BDS-KhangNgo\SOURCE_OF_TRUTH.md` trước khi làm."*

Hoặc ngắn gọn hơn:

> *"Web khangngonhapho, đọc SOT trước"*

---

### Luồng xử lý yêu cầu:

```
Bạn đặt yêu cầu
       ↓
AI đọc SOURCE_OF_TRUTH.md  ← lấy đủ context (repo, file path, schema...)
       ↓
AI implement thay đổi trong nha_ban_sheets.html
       ↓
AI copy → index.html → git commit → git push origin main
       ↓
AI cập nhật Change Log + Backlog trong file này
```

---

### Cách đặt yêu cầu theo từng loại:

| Loại yêu cầu            | Cách nói                               | AI sẽ làm                         |
| -------------------------- | ---------------------------------------- | ----------------------------------- |
| **Làm ngay**        | *"Thêm filter khoảng giá vào web"* | Implement + push + cập nhật SOT   |
| **Ghi vào backlog** | *"Ghi vào backlog: [mô tả]"*        | Chỉ cập nhật Backlog, chưa code |
| **Xem trạng thái** | *"Backlog còn gì chưa làm?"*       | Đọc SOT và báo cáo             |
| **Fix bug**          | *"Web bị lỗi [mô tả]"*             | Debug + fix + push + ghi log        |
| **Hỏi thông tin**  | *"Sheet ID là gì?"*                  | Đọc SOT và trả lời ngay        |

---

### ⚠️ Lý do cần đọc SOT trước:

- AI **không nhớ** context giữa các session
- Chat history cũ **không được load tự động**
- File này chứa đủ: repo URL, file path, schema, password, lịch sử — đọc 1 file là đủ

---

## 1. 🔗 THÔNG TIN KẾT NỐI CỐT LÕI

| Mục                                 | Giá trị                                                             |
| ------------------------------------ | --------------------------------------------------------------------- |
| **GitHub Repo**                | `https://github.com/khangngonhapho/nha-ban`                         |
| **GitHub Pages URL**           | `https://khangngonhapho.github.io/nha-ban/`                         |
| **Owner GitHub**               | `khangngonhapho`                                                    |
| **Collaborator GitHub**        | `mstrangpmp` (vẫn có quyền push)                                 |
| **Branch deploy**              | `main`                                                              |
| **File nguồn (edit)**         | `d:\LHTBrain\01_PROJECTS\BDS-KhangNgo\index.html`                |
| **File deploy (GitHub Pages)** | `index.html` (cùng file, không cần copy)                          |
| **⚠️ QUY TẮC:**             | Chỉ edit trực tiếp `index.html`, commit và push từ thư mục dự án |

### Quy trình deploy chuẩn:

```powershell
# Chạy từ thư mục d:\LHTBrain\01_PROJECTS\BDS-KhangNgo
git add index.html
git commit -m "feat: mô tả thay đổi"
git push origin main
```

---

## 2. 📊 GOOGLE SHEETS

| Mục                          | Giá trị                                                                                               |
| ----------------------------- | ------------------------------------------------------------------------------------------------------- |
| **Sheet ID**            | `1klR5iKt_gxempDi9dguJMS8PGEe2YjqRHrMREzwnXc0`                                                        |
| **Truy cập dữ liệu** | JSONP endpoint (tránh CORS khi mở local)                                                              |
| **Endpoint**            | `https://docs.google.com/spreadsheets/d/{SHEET_ID}/gviz/tq?tqx=out:json;responseHandler:__gsCallback` |

### Schema cột Google Sheet Public (24 cột thực tế):

| Cột  | Index JS        | Tên field JS       | Tên cột Schema      | Mô tả                                                                         |
| ----- | --------------- | ------------------- | --------------------- | ------------------------------------------------------------------------------- |
| A     | `r.c[0]`      | `id`              | `id`                | Mã căn (13 ký tự, khóa chính)                                             |
| B     | `r.c[1]`      | `t`               | `tieu_de`           | Tiêu đề hiển thị                                                           |
| C     | `r.c[2]`      | `dt`              | `dien_tich`         | Diện tích (m²)                                                               |
| D     | `r.c[3]`      | `tang`            | `so_tang`           | Số tầng                                                                       |
| E     | `r.c[4]`      | `mat`             | `mat_tien`          | Mặt tiền căn nhà (m)                                                        |
| F     | `r.c[5]`      | `gia`             | `gia`               | Giá bán (tỷ VND)                                                             |
| G     | `r.c[6]`      | `q`               | `quan`              | Mã quận (lowercase, không dấu)                                              |
| H     | `r.c[7]`      | `ql`              | `ten_quan`          | Tên quận đầy đủ                                                           |
| I     | `r.c[8]`      | `phuong`          | `phuong`            | Phường                                                                        |
| J     | `r.c[9]`      | `loai_hinh`       | `loai_hinh`         | `Mặt tiền` hoặc `Hẻ m`                                                  |
| K     | `r.c[10]`     | `huong`           | `huong_nha`         | Hướng nhà                                                                    |
| L     | `r.c[11]`     | `duong_truoc_nha` | `duong_truoc_nha`   | Loại đường:`Hẹm ba gác` / `Hẹm ô tô lý thuyết` / `Hẹm ô tô` |
| M     | `r.c[12]`     | `rong_hem`        | `do_rong_hem`       | Độ rộng hẹm (m)                                                             |
| N     | `r.c[13]`     | `tinh_trang`      | `tinh_trang_nha`    | Tình trạng:`Mới` / `Bình thường` / `Nát`                           |
| O     | `r.c[14]`     | `danh_gia`        | *(mở rộng)*       | Đánh giá nội bộ:`Hàng Ngon` / `Hàng Lỗi`                            |
| P     | `r.c[15]`     | `ngu_tang_tret`   | `ngu_tang_tret`     | Ngủ tầng trệt                                                                |
| Q     | `r.c[16]`     | `chdv`            | *(mở rộng)*       | CHDV (căn hộ dịch vụ)                                                       |
| R     | `r.c[17]`     | `m`               | `mo_ta`             | Mô tả đã viết lại cho khách                                              |
| S–AB | `r.c[18..27]` | `imgs[]`          | `anh_1`..`anh_10` | URLs ảnh (tối đa 10)                                                         |

> ⚠️ **Nguồn thực tế:** Schema này được xác nhận từ header thực tế của Google Sheet ngày 2026-05-09. Cột O, P, Q là cột mở rộng ngoài Schema chuẩn ban đầu. AI không tự truy cập được Google Sheet — khi có thay đổi cấu trúc cột, cần paste header vào đây để AI sửa code chính xác.

### Mã quận (nhập vào cột G):

| Quận        | Mã nhập |
| ------------ | --------- |
| Quận 3      | `q3`    |
| Phú Nhuận  | `pn`    |
| Tân Bình   | `tb`    |
| Bình Thạnh | `bt`    |
| Gò Vấp     | `gv`    |
| Quận 10     | `q10`   |

> ⚠️ Nhập **lowercase, không dấu** đúng như bảng trên. Nếu muốn thêm quận mới, cần thêm cả nút filter vào HTML.

### Mã đánh giá (nhập vào cột O):

| Đánh giá    | Giá trị nhập | Màu hiển thị  |
| -------------- | --------------- | ---------------- |
| Hàng tốt     | `Hàng Ngon`  | Xanh lá         |
| Hàng xấu     | `Hàng Lỗi`  | Xám             |
| Bình thường | (để trống)   | Không hiện tag |

---

## 3. 🔐 PHÂN QUYỀN TRUY CẬP

| Role                               | Cách truy cập                      | Tính năng                                                                  |
| ---------------------------------- | ------------------------------------ | ---------------------------------------------------------------------------- |
| **Admin (Trang)**            | Thêm `?pwd=trang` vào URL        | Xem tất cả căn, filter theo quận, chọn & tạo share link, xem tab/stats |
| **Khách (có link share)**  | Nhận link dạng `?s=BASE64_TOKEN` | Chỉ xem đúng các căn được chọn                                      |
| **Khách (không có link)** | URL gốc                             | Chỉ thấy thông báo liên hệ                                             |

### Logic share link (Bitmask — cập nhật 2026-05-10):

- **Format mới `?b=<bitmask>`**: Mỗi căn = 1 bit (chọn=1, bỏ=0). Nén bằng bảng ký tự URL-safe (64 ký tự). 64 căn → chỉ ~11 ký tự URL.
- **Lý do đổi**: Mã căn chứa Unicode → `btoa()` crash. Liệt kê 64+ ID → URL >2000 ký tự → bị Zalo/Messenger cắt. Link rút gọn → khách sợ virus.
- **Encode**: `DATA.map(id → SELECTED_IDS.has(id) ? '1' : '0')` → nhóm 6 bit → ký tự B64
- **Decode**: Trong `loadData()` callback, giải mã bitmask → map bit thứ N → ID thứ N trong `fullList`
- **Backward-compatible**: Vẫn hỗ trợ `?s=<IDs>` (comma-separated hoặc base64 JSON cũ)
- **⚠️ Lưu ý**: Bitmask phụ thuộc thứ tự dữ liệu trong Sheet. Nếu thêm/xoá hàng giữa lúc link đang active, vị trí bit sẽ lệch.

---

## 4. 📞 THÔNG TIN LIÊN HỆ WEBSITE

| Mục                          | Giá trị                      |
| ----------------------------- | ------------------------------ |
| **Số điện thoại**   | `0979841573`                 |
| **Zalo link**           | `https://zalo.me/0979841573` |
| **Biến JS cấu hình** | `const SDT = '0979841573';`  |

> Để đổi SĐT: chỉ cần sửa biến `SDT` trong file HTML, hệ thống tự động cập nhật tất cả link.

---

## 5. 🎨 THIẾT KẾ / UI

| Token          | Giá trị                                      |
| -------------- | ---------------------------------------------- |
| `--red`      | `#c0392b` (màu chủ đạo)                  |
| `--gold`     | `#e0a800` (màu nhấn, nút share, tag Ngon) |
| `--blue`     | `#0068ff` (Zalo)                             |
| `--bg`       | `#f2f2f7` (nền)                             |
| `--card`     | `#fff`                                       |
| `--border`   | `#e5e5ea`                                    |
| **Font** | `Be Vietnam Pro` (Google Fonts)              |

### Layout responsive:

- **Mobile** (< 768px): List view, bottom sheet modal
- **Desktop** (≥ 768px): Grid 3 cột, modal trung tâm màn hình

---

## 6. 📝 LỊCH SỬ THAY ĐỔI (Change Log)

### 2026-05-10 (buổi tối)

- **feat: Lightbox toàn màn hình** — Click ảnh/video trong chi tiết → mở full-screen viewer với nền đen, dải thumbnail cuộn ngang, vuốt trái/phải chuyển ảnh. Không mở link ảnh gốc nữa.
- **fix: Video iframe bị cắt chiều cao** — Sửa CSS `aspect-ratio: 9/16; width: auto; height: 100%` để fit theo chiều cao, hai bên letterbox.
- **perf: Tối ưu hiệu năng iOS filter** — Refactor: `render()` chỉ chạy 1 lần khi load. Tách `applyFilter()` chỉ toggle CSS `display:none` → phản hồi <50ms, hết đơ iPhone.
- **fix: Share link Unicode crash** — Bỏ `btoa/atob` (crash ký tự Việt). Dùng ID trực tiếp.
- **feat: Bitmask share link** — Nén 64+ căn thành ~11 ký tự URL-safe, giữ domain GitHub tin cậy.
- **feat: Admin Chọn tất cả / Bỏ chọn tất cả** — Nút floating ☐/☑, hoạt động theo danh sách đang hiển thị sau filter.
- **ux: Auto-close bộ lọc** — Đóng khi bấm ra ngoài header hoặc cuộn xuống, giải phóng màn hình.
- **feat: Icon đánh giá trên card** — ▶ xanh (Hàng Ngon) / ⏸ đỏ (Hàng Lỗi), kế chip "tầng".
- **chore: Di dời repo** — Chuyển từ `00_INBOX` sang `01_PROJECTS/BDS-KhangNgo`, xoá file cá nhân khỏi GitHub.

### 2026-05-10 (buổi chiều)

- **fix: Mô tả xuống dòng** — Thêm `white-space: pre-wrap` để hiển thị đúng ký tự xuống dòng từ Google Sheet.
- **feat: Facebook Reel** — Tự động nhúng iframe cho link FB (`facebook.com`, `fb.watch`, `fb.gg`). Video ưu tiên vị trí #1 trong gallery chi tiết, ảnh đại diện trang chủ chỉ dùng ảnh tĩnh.
- **feat: Tìm kiếm Real-time** — Thanh search lọc đồng thời Mã căn, Tiêu đề, Tên đường, Phường.
- **feat: Smart Scroll Header** — Header trượt ẩn khi cuộn xuống, hiện khi cuộn lên.
- **feat: Avatar + rebrand header** — Thay icon nhà bằng avatar Khang Ngô, chữ xuống hàng.

### 2026-05-09

- **feat: add reset filter button** (`b0df8c2`)

  - Nút "↺ Xóa lọc" xuất hiện bên phải summary bar — **chỉ hiện khi đang có filter active**
  - Tap → clear tất cả filter, reset toàn bộ tabs về "Tất cả", render lại danh sách
- **feat: multi-select filters + reorder districts + separate Đánh giá row** (`f7ed663`)

  - **Multi-select:** tất cả filter đều toggle (chọn nhiều cùng lúc). Cùng loại = OR, khác loại = AND
  - **Thứ tự quận:** Q3 → Q10 → Phú Nhuận → Tân Bình → Bình Thạnh → Gò Vấp
  - **Tách Đánh giá:** 💎 Ngon / ⚠️ Lỗi thành dòng riêng bên dưới Khoảng giá
  - Refactor toàn bộ JS: thay `cur*` string → `sel*` Set; thêm `getFiltered()`, `tSel()`, `syncTabUI()`
  - `updateStats()` và `render()` dùng chung `getFiltered()` — đảm bảo nhất quán
- **feat: add price range filter** (`da754c2`)

  - 5 khoảng: Dưới 7 tỷ / 7–10 / 10–15 / 15–20 / Trên 20 tỷ
  - Filter giá **độc lập** với quận/phường/đường (không reset khi đổi các filter khác)
  - Summary hiện đầy đủ: *"Quận 3 · P.10 · Hẻm ô tô · 10–15 tỷ"*
- **fix: rename `p_ngu_tret` → `ngu_tang_tret`** (`8a1d16b`)

  - Header thực tế trong sheet là `ngu_tang_tret` (không phải `p_ngu_tret`)
  - Sửa trong mapping JS và hiển thị modal
  - **Lưu ý về quy trình:** AI không tự truy cập Google Sheet. Nếu thêm/xóa cột, paste header thực tế vào chat để AI sửa đúng.
- **feat: add `duong_truoc_nha` filter + fix field name** (`e6fa89a`)

  - Sửa lỗi tên biến: `duong` → `duong_truoc_nha` cho khớp Schema Public thực tế (cột L = loại đường trước nhà)
  - Thêm filter “Đường trước nhà” vào panel: generate động từ data
  - Filter có cấp bậc: Quận → Phường → Đường trước nhà
  - Chọn quận mới → reset phường + đường; chọn phường mới → reset đường
  - Summary hiện đủ: *“Quận 3 · P.10 · Hẹm ô tô”*
  - Sửa SOT: cập nhật Schema đúng với thực tế (24 cột, tên đúng)
- **feat: add compact collapsible filter with ward (phuong) support** (`8ed558f`)

  - Header gọn mặc định: chỉ hiện nút "🎚 Bộ lọc" + tóm tắt filter đang active
  - Tap nút → mở panel trượt xuống với 2 tầng: Quận/TP + Phường
  - Phường được generate động từ DATA, tự thay đổi khi chọn quận khác
  - Đổi quận → tự reset phường về "Tất cả"
  - Summary bar hiện filter đang chọn (ví dụ: "Quận 3 · P.10")
  - Áp dụng cho Admin only (public không thấy)
- **feat: sort listing by price high to low** (`b3c72ac`)

  - Thêm `DATA.sort()` theo giá giảm dần ngay sau khi load data xong
  - Áp dụng cho cả Admin và khách có share link

### 2026-05-07 (buổi chiều)

- **Fix data override bug: use fullList** (`d726153`)
  - Bug: Biến `list` chưa được định nghĩa trong scope → DATA bị ghi đè thành `undefined`
  - Fix: Đổi tên mảng map thành `fullList`, gán đúng vào `DATA`
- **Fix undefined fields** (`5c8d3b6`)
  - Khôi phục mapping `rong_hem` (col M) và `tinh_trang` (col N)
  - Các trường này bị mất sau lần refactor trước

### 2026-05-07 (buổi sáng)

- **Fix share logic and sync** (`2fc3a1e`)
  - Sửa logic share link persistent: lưu danh sách ID thay vì encode cả data
  - Sử dụng `mstrangpmp` làm collaborator để push code
  - Transfer ownership repo sang `khangngonhapho`
- **Simplify address format** (`5912f69`)
  - Đổi format địa chỉ thành `P.{phường}, Q.{quận}` thay vì tên đầy đủ
- **Fix image box stretching** (`6529751`)
  - Thêm `height: 125px` cố định cho `.ibox` → ảnh đứng không kéo giãn card
- **Add District 10 filter** (`82d56e6`)
  - Thêm nút filter Quận 10, mã `q10`

### 2026-05-05 ~ 2026-05-06

- **Hide assessment from public** (`df1a1f9`)
  - Tab filter "Ngon/Lỗi" chỉ hiện cho Admin (`body.is-admin`)
  - Stats bar cũng ẩn với public
- **Add CHDV field** (`de741c2`)
  - Thêm trường "Căn hộ dịch vụ" (col Q)
- **Add Assessment tags** (`531d432`)
  - Tag màu xanh "Hàng Ngon", màu xám "Hàng Lỗi" hiện trên card
  - Thêm trường "Phòng ngủ trệt" (col P)
- **Replace Frontage with Street** (`aa4f0d6`)
  - Card ngoài hiện tên đường thay vì mặt tiền
- **Rebrand to Khang Ngô Nhà Phố** (`65f563d`)
  - Đổi từ "Nhà Bán HXH" sang "Khang Ngô Nhà Phố"
  - Đổi badge "căn HXH" → "BĐS"
- **Add Ward (Phường)** (`89472b6`)
  - Thêm cột Phường (col I), hiển thị trên card và modal chi tiết
- **Support 10 images** (`8e9b17c`)
  - Mở rộng từ 5 → 10 ảnh mỗi căn (col S đến AB)

### 2026-05-04 (khởi tạo)

- **first commit: nha ban HXH website** (`673ed04`)
  - Khởi tạo website với Google Sheets JSONP integration
  - Filter theo quận (q3, pn, tb, bt, gv)
  - Card list view với ảnh, giá, thông tin cơ bản
  - Bottom sheet modal xem chi tiết
  - Tính năng yêu thích (♡)

---

## 7. ⚠️ LƯU Ý KỸ THUẬT QUAN TRỌNG

### 7.1 Workflow đã đơn giản hoá (từ 10/05/2026)

- Chỉ còn 1 file duy nhất: `index.html` (không cần `nha_ban_sheets.html` nữa)
- Edit trực tiếp `index.html`, commit và push
- Thư mục dự án: `d:\LHTBrain\01_PROJECTS\BDS-KhangNgo`

### 7.2 JSONP thay vì fetch

- Website dùng JSONP callback (`__gsCallback`) thay vì `fetch()` vì:
  - Tránh lỗi CORS khi test local bằng `file://`
  - Hoạt động ngay cả không có server

### 7.3 Google Drive image URL

- Ảnh Google Drive cần convert sang thumbnail URL:
  - Input: `https://drive.google.com/file/d/{ID}/...`
  - Output: `https://drive.google.com/thumbnail?id={ID}&sz=w800`
- Hàm `fixImgUrl(url, sz)` xử lý tự động
- List view dùng `w400`, modal chi tiết dùng `w1200`

### 7.4 Admin password

- Password hiện tại: `trang`
- Kiểm tra qua URL param: `?pwd=trang`
- Để đổi: sửa biến `const ADMIN_PASSWORD = 'trang';`

### 7.5 Sort order

- Danh sách luôn được sort theo **giá từ cao → thấp** sau khi load
- Sort áp dụng trước khi render, sau khi lọc Admin/Share/Public

---

## 8. 🚀 TÍNH NĂNG CẦN THÊM (Backlog)

> Cập nhật khi có thêm yêu cầu mới

- [x] ~~Thêm filter theo khoảng giá~~ ✅ Done 2026-05-09
- [ ] Thêm filter theo loại hình (Mặt tiền / Hẻm)
- [x] ~~Tìm kiếm theo tên đường / phường~~ ✅ Done 2026-05-10
- [x] ~~Sort động~~ ✅ Done 2026-05-09 (toggle ⬇⬆)
- [ ] Thêm quận mới khi có nhu cầu

---

---

### 📌 Quy tắc cập nhật file này:

1. **Sau mỗi lần deploy** → thêm entry vào Change Log (section 7)
2. **Sau mỗi yêu cầu backlog** → thêm vào Backlog (section 9), xóa khi done
3. **Nếu thay đổi schema Sheet** → cập nhật bảng section 3
4. **Nếu đổi password/SĐT** → cập nhật section 4 và 5

*File này được tạo và duy trì bởi Antigravity AI Assistant. Cập nhật lần cuối: 2026-05-10.*

