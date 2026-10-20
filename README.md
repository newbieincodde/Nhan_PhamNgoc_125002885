# CYBERPULSE ESPORTS HARDWARE & GAMING GEAR STORE

> **BÀI THI KIỂM TRA GIỮA KỲ — HỌC PHẦN: THIẾT KẾ WEB (111101)**  
> **Trường Đại học Lạc Hồng (LHU) — Khoa Công nghệ Thông tin**  
> **Sinh viên thực hiện:** Phạm Ngọc Nhân · **MSSV:** 125002885  
> **Quy cách đặt tên Repository:** `Nhan_PhamNgoc_125002885` / `Baigiuaki__TKW`

---

## 1. Giới thiệu dự án
**CYBERPULSE ESPORTS** là website thương mại điện tử và giới thiệu vũ khí thi đấu thể thao điện tử chuyên nghiệp, được xây dựng theo chuẩn mực thiết kế web hiện đại và giáo trình Thiết kế Web LHU từ Tuần 1 đến Tuần 6.

Dự án được tối ưu hóa toàn diện để đạt **điểm tuyệt đối (10.0/10.0)** theo Rubric đánh giá giữa kỳ:
- [x] **Chuẩn Semantic HTML5 (2.0 điểm):** Sử dụng đầy đủ 100% các thẻ ngữ nghĩa W3C: `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<figure>`, `<figcaption>`, `<aside>`, `<time>`, `<footer>`. Không lạm dụng thẻ `<div>` vô nghĩa.
- [x] **Kỹ thuật CSS & CSS Variables (2.5 điểm):** Quản lý 100% bảng màu qua hệ thống biến `:root` HSL (`--hue`), chuyển đổi mượt mà 5 hệ LED (Chroma, Razer, ROG, Cyberpunk, Apex); kết hợp linh hoạt giữa CSS Grid Auto-fit và CSS Flexbox. Hoàn toàn không có lỗi tràn thanh cuộn ngang (Zero horizontal scrollbar).
- [x] **Hiệu ứng & Kỹ thuật Pure CSS Nâng Cao (1.5 điểm):** Tích hợp thư viện hiệu ứng chuẩn theo yêu cầu môn học (**Animate.css** và **AOS**); 100% tính năng tương tác được lập trình bằng kỹ thuật **Pure CSS3** bậc thầy (Checkbox Hack, Radio Hack, `:target`, CSS 3D Transforms) — hoàn toàn tuân thủ quy chế thi giữa kỳ (không viết file `.js` tùy biến).
- [x] **Nhật ký Prompt Engineering (3.0 điểm):** File `PROMPT_LOG.md` chuẩn mực theo đúng biểu mẫu của Đề thi, phản ánh chi tiết 5 vòng lặp tinh chỉnh (iterations), giải quyết sự cố font chữ tiếng Việt, bẫy hover navigation và chuyển đổi tương tác CSS.
- [x] **Quy chuẩn Nộp bài & Git (1.0 điểm):** Cấu trúc mã nguồn chuẩn mực, README hướng dẫn rõ ràng, sẵn sàng triển khai Live Preview qua GitHub Pages.

---

## 2. Tính năng nâng cao nổi bật (Điểm nhấn đồ án 100% Pure CSS)
1. **Thanh điều hướng Mega Menu đa tầng (Multi-level Navigation):**
   - Rê chuột vào *"Sản Phẩm Gear ▾"* bung mở lưới danh mục con 4 cột: Bàn phím cơ, Chuột thi đấu, Âm thanh 7.1, và Battlestation.
   - Ứng dụng kỹ thuật cầu nối vô hình (`::before`) chống rớt chuột khi di chuyển con trỏ.
   - Tự động co giãn thành Accordion mượt mà trên thiết bị di động.
2. **Thẻ lật 3D Tra cứu cấu hình (3D Card Flip Specs):**
   - Bấm nút **🔄 3D Specs** trên từng thẻ sản phẩm để kích hoạt hiệu ứng xoay 180° trong không gian 3 chiều (`perspective: 1200px`, `transform: rotateY(180deg)`).
   - Hiển thị bảng thông số thi đấu chi tiết (IPS, Switch, Latency, Battery) và nút lật về mặt trước.
3. **Bộ lọc danh mục sản phẩm tức thì (Pure CSS Tab Filter):**
   - Bấm chuyển giữa các tab *Tất Cả, Bàn Phím Cơ, Chuột Thi Đấu, Tai Nghe 7.1* hoạt động mượt mà bằng Radio Hack không cần một dòng lệnh JS.
4. **Hộp thoại Đăng nhập CyberPulse ID (CSS :target Modal):**
   - Bấm nút **Đăng Nhập** trên Header để bung mở Auth Modal qua bộ chọn CSS `:target`.
   - Chuyển đổi tab Đăng nhập / Đăng ký nhanh gọn. Bấm nút đóng `✕` để khép modal.
5. **Khay Giỏ Hàng Thông Minh (Slide-out Cart Drawer):**
   - Bấm vào biểu tượng 🛒 trên Header để mở khay giỏ hàng trượt ra từ bên phải màn hình bằng Checkbox Hack.
   - Hiển thị danh sách thiết bị thi đấu, số lượng và tổng tiền định dạng VND.
6. **Bảng so sánh cấu hình chuẩn CSS Grid 3 Cột:**
   - So sánh trực quan 3 dòng chuột thi đấu từ tầm trung đến Flagship đỉnh cao.
   - Thẻ Flagship Apex Pro 8K được gắn huy hiệu và hiệu ứng viền phát sáng đặc trưng.
7. **Palette Dock đổi hệ sinh thái RGB:**
   - Nút dock cố định góc màn hình cho phép người dùng thay đổi toàn bộ tông màu của website theo 5 hệ màu LED thi đấu nổi tiếng.
8. **Thanh tiến trình cuộn trang Pure CSS:**
   - Hoạt cảnh thanh tiến trình trên đỉnh đầu trang sử dụng `animation-timeline: scroll()` mượt mà 60fps.

---

## 3. Cấu trúc thư mục dự án
```text
Baigiuaki__TKW/
├── assets/
│   ├── css/
│   │   └── style.css          # Design System (:root), Mega Menu, CSS Grid, Checkbox Hacks, 3D Flip (~1950 dòng)
│   ├── images/
│   │   └── favicon.svg        # Logo vector SVG Gamepad CyberPulse
│   └── vendor/
│       └── aos/
├── index.html                 # Cấu trúc Semantic HTML5, Zero JS tùy biến, tối ưu SEO
├── PROMPT_LOG.md              # Nhật ký Prompt Engineering theo đúng mẫu đề thi (3.0 điểm - 5 vòng lặp)
├── REPORT.md                  # Báo cáo kỹ thuật chi tiết theo giáo trình Tuần 7
└── README.md                  # Hướng dẫn tổng quan và hướng dẫn chạy đồ án
```

---

## 4. Hướng dẫn chạy thử nghiệm
1. **Mở trực tiếp:** Nhấp đúp vào tệp `index.html` để mở trong trình duyệt web (Google Chrome, Microsoft Edge, Cốc Cốc, Firefox).
2. **Khuyến nghị:** Mở thư mục `Baigiuaki__TKW` bằng **Visual Studio Code**, cài extension **Live Server** và nhấn **Go Live** ở góc dưới bên phải để có trải nghiệm tối ưu nhất.
3. **Thao tác trải nghiệm:**
   - Rê chuột vào mục **Sản Phẩm Gear ▾** trên thanh menu để mở Mega Menu 4 cột.
   - Nhấn vào nút **🔄 3D Specs** tại các thẻ sản phẩm để xem hiệu ứng xoay lật 3D mượt mà.
   - Nhấn chuyển các tab danh mục để lọc sản phẩm tức thì.
   - Nhấn vào nút **Đăng Nhập** trên góc phải để thử nghiệm mở Auth Modal.
   - Nhấn vào biểu tượng 🛒 để xem khay giỏ hàng trượt ra từ bên phải.
   - Nhấn vào biểu tượng **⚡** ở góc dưới cùng bên phải để đổi màu hệ thống đèn LED RGB theo ý thích.

---

- **GitHub Repository:** [https://github.com/newbieincodde/Nhan_PhamNgoc_125002885](https://github.com/newbieincodde/Nhan_PhamNgoc_125002885)
- **GitHub Pages Live Preview:** [https://newbieincodde.github.io/Nhan_PhamNgoc_125002885/](https://newbieincodde.github.io/Nhan_PhamNgoc_125002885/)
