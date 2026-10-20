# BÁO CÁO GIẢI TRÌNH DỰ ÁN GIỮA KỲ (REPORT.MD)

- **Học phần:** Thiết kế Web (111101) – Trường Đại học Lạc Hồng (LHU)
- **Đề tài:** **CYBER GAMING GEAR (CYBERPULSE ESPORTS HARDWARE)**
- **Sinh viên thực hiện:** Phạm Ngọc Nhân
- **Mã số sinh viên (MSSV):** 125002885
- **Giáo viên chấm điểm:** Giảng viên Bộ môn Công nghệ Thông tin - LHU
- **Đường link GitHub Repository:** [https://github.com/newbieincodde/Nhan_PhamNgoc_125002885](https://github.com/newbieincodde/Nhan_PhamNgoc_125002885)
- **Đường link Live Preview:** [https://newbieincodde.github.io/Nhan_PhamNgoc_125002885/](https://newbieincodde.github.io/Nhan_PhamNgoc_125002885/)

---

## 1. Ý TƯỞNG THIẾT KẾ VÀ KIẾN TRÚC TỔNG THỂ

### 1.1. Bối cảnh & Cảm hứng
Dự án được xây dựng dựa trên định hướng phát triển một cổng thông tin và thương mại thiết bị thể thao điện tử (Esports Gear & Hardware) đạt chuẩn quốc tế. Lấy cảm hứng từ các thương hiệu phần cứng gaming hàng đầu thế giới (Razer Chroma, ASUS ROG, SteelSeries):
- **Phối màu Cyber Dark Palette (`#07090e`, `#0d121d`, `#131a29`):** Nền đen ánh xanh sâu thẳm mô phỏng không gian đấu trường ánh sáng công nghệ cao, tạo chiều sâu thị giác và làm nổi bật các thiết bị phần cứng.
- **Động cơ màu Neon HSL linh hoạt (`--hue: 185`):** Toàn bộ các hiệu ứng viền sáng (glow), vệt màu gradient và đường cắt laser đều được sinh ra từ biến góc màu `--hue`. Người dùng có thể tùy biến sang các hệ sinh thái LED khác như Razer Emerald (140°), ROG Crimson (345°), Cyberpunk Violet (275°), Apex Amber (38°) chỉ với 1 cú click chuột qua Palette Dock.
- **Thanh điều hướng Mega Menu đa tầng (Multi-level Navigation):** Đáp ứng nhu cầu mở rộng của các website thương mại điện tử chuyên nghiệp; khi rê chuột hoặc chạm vào danh mục *"Sản Phẩm Gear ▾"* và *"Hệ Sinh Thái RGB ▾"*, giao diện lập tức bung mở lưới danh mục con 4 cột phân cấp rõ ràng.
- **Kiến trúc tương tác đỉnh cao 100% Pure CSS (Tuân thủ tuyệt đối quy định không dùng file JS tùy biến):** Theo đúng yêu cầu kiểm tra giữa kỳ (chỉ đánh giá kiến thức Tuần 1 đến Tuần 6 - HTML5 & CSS3), website **hoàn toàn không dùng bất kỳ file JavaScript riêng nào**. Mọi tính năng phức tạp như đổi màu Theme RGB, Lọc Tab sản phẩm, Lật thẻ 3D Specs, Giỏ hàng Slide-out Cart Drawer, và Hộp thoại Đăng nhập đều được hiện thực hóa thông qua các kỹ thuật CSS3 bậc thầy: **Checkbox Hack**, **Radio Hack**, **CSS `:target`**, và **CSS 3D Transforms**.

---

## 2. TOP 3 PROMPTS THÀNH CÔNG NHẤT

### Prompt 1: Dàn trang Lưới sản phẩm Auto-fit và Bảng so sánh CSS Grid 3 cột bắt buộc
- **Nội dung Prompt:**
  > *"Hãy viết mã CSS Grid cho 2 khối nội dung then chốt của CyberPulse:*  
  > *1. Khối Lưới sản phẩm Arsenal Showcase: sử dụng `grid-template-columns: repeat(auto-fit, minmax(280px, 1fr))` kết hợp với Flexbox bên trong từng card để giữ nút bấm luôn thẳng hàng ở đáy.*  
  > *2. Khối So sánh cấu hình chuột Flagship: bắt buộc chia 3 cột cân xứng (`grid-template-columns: repeat(3, 1fr)`) trên Desktop và 1 cột trên Mobile. Card ở giữa là Flagship đỉnh cao được viền neon sáng rực và gắn huy hiệu nổi bật."*
- **Giải thích lý do thành công:**
  - Đáp ứng 100% tiêu chí chấm điểm kỹ thuật CSS Grid (Tuần 3 & Tuần 4).
  - Tự động thích ứng trên mọi kích thước màn hình mà không cần viết quá nhiều media queries thủ công.
  - Phân cấp thị giác rõ ràng, hướng sự chú ý của người mua vào dòng sản phẩm Flagship chủ lực.

### Prompt 2: Xây dựng Thanh Mega Menu Dropdown đa tầng phân cấp
- **Nội dung Prompt:**
  > *"Viết cấu trúc HTML và CSS cho thanh điều hướng Header: Tích hợp Mega Menu Dropdown khi rê chuột vào mục 'Sản Phẩm Gear ▾'. Mega Menu phải hiển thị dạng popover kích thước lớn 760px căn giữa màn hình, chứa lưới 4 cột con: Bàn phím cơ, Chuột thi đấu, Âm thanh 7.1, và Battlestation. Trên Mobile, Mega Menu tự động chuyển sang chế độ Accordion sổ dọc khi chạm vào. Dùng kỹ thuật cầu nối vô hình ::before để chống rớt chuột khi rê từ menu cha sang menu con."*
- **Giải thích lý do thành công:**
  - Giải quyết bài toán phân cấp thông tin sâu trong các trang web phần cứng nhiều linh kiện.
  - Trải nghiệm mượt mà với chuyển động trượt 3D `cubic-bezier(0.16, 1, 0.3, 1)` và hiệu ứng phát sáng Neon.
  - Thao tác độc lập và tối ưu hoàn hảo trên cả điện thoại di động lẫn máy tính để bàn.

### Prompt 3: Hiện thực hóa State Management và Tương tác Động 100% Pure CSS (Zero JS)
- **Nội dung Prompt:**
  > *"Quy chế thi giữa kỳ nghiêm ngặt không cho phép viết file .js riêng. Hãy tái cấu trúc toàn bộ các tính năng tương tác của CyberPulse sang 100% Pure CSS:*  
  > *1. Hệ thống đổi màu LED: Dùng Radio Button Hack (`#theme-cyan:checked ~ * { --hue: 185; }`) với các radio ẩn đặt ngay đầu thẻ `<body>`.*  
  > *2. Lọc sản phẩm theo danh mục: Dùng Radio Hack `#filter-xxx:checked ~ .product-grid .product-card:not([data-category='xxx']) { display: none; }`.*  
  > *3. Thẻ xoay lật 3D (Card Flip): Dùng Checkbox Hack đặt trong từng card, khi checked thì kích hoạt `transform: rotateY(180deg)` cho mặt sau hiển thị thông số specs.*  
  > *4. Khay giỏ hàng & Hộp thoại Đăng nhập: Dùng Checkbox Hack và CSS `:target` để đóng/mở mượt mà mà không chạm vào 1 dòng lệnh JavaScript nào."*
- **Giải thích lý do thành công:**
  - Giải quyết triệt để rào cản quy chế thi của môn học mà vẫn giữ nguyên được trải nghiệm người dùng hiện đại, sống động.
  - Thể hiện sự am hiểu sâu sắc về bộ chọn CSS nâng cao (`:checked`, `:target`, sibling combinators `~`, `+`, `not()`).
  - Tối ưu hóa hiệu năng render tuyệt đối: trình duyệt biên dịch trực tiếp bằng GPU, không tốn tài nguyên chạy JavaScript Engine.

---

## 3. LỖI KHÓ NHẤT ĐÃ GẶP VÀ CÁCH XỬ LÝ (THE BUG HUNTER)

### Lỗi 1: Font chữ Tiếng Việt bị vỡ nét (Diacritic Typography Bug)
- **Hiện tượng:** Khi sử dụng font chữ Google Fonts `Rajdhani` cho phong cách Cyberpunk, các nguyên âm có dấu Tiếng Việt (như `ế, ơ, ư, ẩ, ộ, ắ...`) hiển thị với nét chữ khác biệt, nhảy font sang Times New Roman/Arial mặc định của hệ thống.
- **Nguyên nhân:** Font `Rajdhani` trên Google Fonts chỉ hỗ trợ bộ ký tự `latin, latin-ext, devanagari`, hoàn toàn **không hỗ trợ bộ ký tự Tiếng Việt (vietnamese subset)**.
- **Giải pháp:** Thay thế toàn bộ hệ thống font tiêu đề sang **`Chakra Petch`** kết hợp với **`Plus Jakarta Sans`**. `Chakra Petch` có đầy đủ 100% bộ dấu Tiếng Việt chuẩn Unicode mà vẫn giữ trọn vẹn đường nét góc cạnh, hầm hố của ngôn ngữ thiết kế Gaming Gear.

### Lỗi 2: Tràn thanh cuộn ngang do Animate.css trên màn hình Mobile
- **Hiện tượng:** Trên màn hình điện thoại (375px - 414px), trang web bị trôi lệch sang phải khoảng 20px, xuất hiện thanh cuộn ngang gây ức chế khi vuốt.
- **Nguyên nhân:** Các phần tử mang class của Animate.css ban đầu được đẩy ra ngoài tọa độ hiển thị (`translateX(100%)`), kéo giãn chiều rộng ảo của tài liệu quá `100vw`.
- **Giải pháp:** Thiết lập CSS Reset nghiêm ngặt:
  ```css
  html, body {
    overflow-x: hidden;
    width: 100%;
    position: relative;
  }
  ```

### Lỗi 3: "Rớt chuột" khi rê vào Mega Menu Dropdown (Hover Tunnel Disconnect)
- **Hiện tượng:** Khi người dùng rê chuột từ thanh Menu cha xuống Mega Menu con, chỉ cần con trỏ chuột lướt qua khoảng trống (gap 12px) thì Mega Menu lập tức biến mất.
- **Giải pháp:** Ứng dụng kỹ thuật "cầu nối vô hình" bằng pseudo-element `::before`:
  ```css
  .nav-mega::before {
    content: '';
    position: absolute;
    top: -16px;
    left: 0;
    width: 100%;
    height: 16px;
    background: transparent;
  }
  ```
  Nhờ đó, con trỏ chuột luôn nằm trong vùng phủ hover, đảm bảo menu mở mượt mà 100%.
