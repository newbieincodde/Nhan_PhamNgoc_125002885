# NHẬT KÝ PROMPT ENGINEERING (VIBE CODING LOG)

- **Họ và tên:** Phạm Ngọc Nhân
- **MSSV:** 125002885
- **Tên đề tài Website:** CYBERPULSE ESPORTS HARDWARE & GAMING GEAR STORE
- **Công cụ AI đã sử dụng:** Google Antigravity & Claude 3.5 Sonnet (Vibe Coding Assistant)
- **Môi trường lập trình:** Visual Studio Code, Git, Chrome DevTools (F12)

---

## 1. Yêu cầu ban đầu (System/Initial Prompt)

> *"Hãy đóng vai trò một Kiến trúc sư Giao diện Front-end (Senior UI/UX Architect). Tôi cần xây dựng một website hoàn chỉnh cho thương hiệu thiết bị thi đấu thể thao điện tử 'CYBERPULSE Esports Hardware'.*  
> *Website phải tuân thủ nghiêm ngặt chuẩn mực W3C và giáo trình Thiết kế Web LHU (111101) từ Tuần 1 đến Tuần 6:*  
> *1. Cấu trúc Semantic HTML5: `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<figure>`, `<figcaption>`, `<aside>`, `<footer>`. Tuyệt đối không lạm dụng thẻ `<div>` vô nghĩa.*  
> *2. CSS Variables `:root`: Quản lý 100% màu sắc bằng hệ màu Neon HSL dựa trên biến góc quay `--hue: 185`, không hardcode mã màu hex rải rác.*  
> *3. Bố cục hiện đại: Kết hợp CSS Grid Auto-fit cho lưới sản phẩm và CSS Grid 3 cột bắt buộc cho bảng so sánh cấu hình Gear.*  
> *4. Thư viện hiệu ứng: Tích hợp cả Animate.css và AOS (Animate on Scroll).*  
> *5. Tính năng nâng cao: Thanh điều hướng đa tầng với Mega Menu Dropdown hiển thị các nhánh con; Giỏ hàng và Đăng nhập lưu trữ trạng thái vào LocalStorage."*

---

## 2. Quá trình tinh chỉnh & Giải quyết sự cố (Iteration Iterations)

### Lần 1: Dựng khung Semantic HTML & CSS Variable
- **Prompt đã dùng:**  
  *"Tạo khung HTML5 và hệ thống Design System trong `style.css` cho CyberPulse. Định nghĩa các biến `:root` quản lý màu nền Dark (#07090e), màu chữ, khoảng cách spacing và dải màu Neon RGB dựa trên công thức HSL `hsl(var(--hue) 100% 55%)`. Hãy chia bố cục các vùng nội dung chính bằng thẻ ngữ nghĩa."*
- **Kết quả AI tạo ra:**  
  AI đã sinh ra cấu trúc trang và hệ thống biến CSS đầy đủ. Tuy nhiên, ở phần Hero Stats và phần Bảng thông số kỹ thuật, AI vẫn sử dụng nhiều thẻ `<div class="hero-stats">` lồng nhau và các thẻ `<div class="sensor-box">` thay vì sử dụng thẻ ngữ nghĩa minh họa kỹ thuật.
- **Nhận xét & Tinh chỉnh của SV:**  
  Em nhận thấy việc lạm dụng thẻ `<div>` sẽ vi phạm tiêu chí chấm 2.0 điểm của Tiêu chí 2 (Semantic HTML5). Em đã yêu cầu AI:  
  1. Thay thế khu vực biểu đồ cảm biến thành cặp thẻ `<figure class="tech-figure">` và `<figcaption class="tech-figcaption">` chuẩn W3C của bài học Tuần 2.  
  2. Bổ sung thẻ `<aside class="cyber-aside">` cho khu vực Flash Sale & Đặc quyền VIP nhằm phản ánh đúng nội dung bổ trợ ngữ nghĩa.  
  3. Bổ sung thuộc tính `aria-label`, `role="status"` cho thanh thông báo và các nút tương tác để đạt chuẩn Accessibility (A11y).

---

### Lần 2: Tích hợp thư viện Animate.css & AOS
- **Prompt đã dùng:**  
  *"Tích hợp Animate.css và AOS (Animate on Scroll) vào dự án qua CDN. Thêm các class hiệu ứng `animate__animated animate__fadeInDown` cho tiêu đề Hero và gán `data-aos='fade-up'` cho từng thẻ sản phẩm trong lưới và bảng so sánh."*
- **Kết quả AI tạo ra:**  
  Hiệu ứng xuất hiện tốt khi tải trang, nhưng xuất hiện hiện tượng xung đột: Khi cuộn chuột nhanh, một số thẻ sản phẩm mang thuộc tính `data-aos` bị ẩn hoàn toàn (`opacity: 0`) và không chịu hiển thị do sự kiện cuộn chưa kích hoạt ngưỡng `offset` mặc định của AOS trên màn hình laptop nhỏ.
- **Thách thức gặp phải:**  
  AOS làm ẩn phần tử với `opacity: 0` khi script chưa kích hoạt hoàn tất hoặc khi người dùng lướt nhanh qua vùng scroll. Ngoài ra, trên điện thoại xảy ra hiện tượng thanh cuộn ngang (horizontal scrollbar) do hiệu ứng `animate__fadeInRight` bay từ ngoài khung nhìn vào.
- **Cách sửa prompt (Debug prompt):**  
  *"Khắc phục 2 lỗi sau:*  
  *1. Trong `style.css`, thêm thuộc tính `overflow-x: hidden` cho cả `html` và `body` để triệt tiêu hoàn toàn lỗi vỡ layout cuộn ngang do hiệu ứng bay vào.*  
  *2. Trong `assets/js/main.js`, cấu hình lại AOS với `offset: 80`, `once: true`, `duration: 750` và bổ sung hàm dọn dẹp dự phòng (fallback timeout 1.5s): tự động quét và thêm class `.aos-animate` cho các thẻ bị treo nếu trình duyệt tải chậm hoặc người dùng tắt JS."*  
  -> **Kết quả sau sửa:** Trang web cuộn cực kỳ mượt mà 60fps, không hề có thanh cuộn ngang và 100% nội dung đều hiển thị sắc nét.

---

### Lần 3: Xây dựng Mega Menu đa tầng & Hệ sinh thái RGB lưu LocalStorage
- **Prompt đã dùng:**  
  *"Hãy bổ sung thanh Mega Menu Dropdown đa tầng cho menu 'Sản Phẩm Gear ▾' và 'Hệ Sinh Thái RGB ▾' với 4 cột phân nhánh danh mục con. Viết hệ thống Đăng nhập (Auth Modal) và Giỏ hàng (Cart Drawer) lưu trữ dữ liệu vào `localStorage` để khi tải lại trang (F5) thông tin tên người dùng, avatar VIP và danh sách sản phẩm đã chọn không bị mất."*
- **Kết quả AI tạo ra:**  
  AI viết mã JavaScript tương đối tốt nhưng sử dụng hàm `alert()` để thông báo khi thêm giỏ hàng và đăng nhập thành công. Điều này làm giảm tính chuyên nghiệp và phá vỡ phong cách Cyberpunk Dark Mode của giao diện.
- **Nhận xét & Tinh chỉnh của SV:**  
  Em đã yêu cầu AI loại bỏ 100% các câu lệnh `alert()` mặc định của trình duyệt và xây dựng một component Toast Notification riêng (`#toastNotification`) với viền Neon phát sáng, tự động thu gọn sau 3.8 giây. Đồng thời, cấu hình Mega Menu trên Mobile hiển thị dạng Accordion khi chạm vào mũi tên, còn trên Desktop hiển thị mượt mà với hiệu ứng trượt 3D và đổ bóng Glow.

---

### Lần 4: Debug lỗi Font chữ Tiếng Việt, Khắc phục Nav Bar & Ứng dụng Không gian 3D
- **Prompt đã dùng:**  
  *"1. Kiểm tra và debug lại toàn bộ font chữ vì một số ký tự tiếng Việt có dấu bị lỗi/vỡ hình dạng.*  
  *2. Sửa lỗi thanh Nav Bar: Menu con đã hiện nhưng không nhấp chọn được các danh mục con (Bàn phím cơ, Chuột thi đấu,...).*  
  *3. Ứng dụng thêm các hiệu ứng 3D trực quan phù hợp với website Gaming Gear (Lưới 3D di chuyển ở Hero, Thẻ 3D nghiêng theo chuột, Lật thẻ 3D 180° xem cấu trúc vi mạch)."*
- **Kết quả AI tạo ra & Phân tích nguyên nhân:**  
  - *Về font chữ:* Font `Rajdhani` ban đầu không có bảng mã ký tự tiếng Việt (`vietnamese subset`) trên Google Fonts, khiến các nguyên âm có dấu (ơ, ư, ế, ẩ,...) bị ép nhảy sang font fallback hệ thống tạo nên cảm giác lởm chởm ("lỗi font chữ").  
  - *Về Nav Bar:* Trên Desktop có khoảng hở (gap) 14px giữa link menu và hộp Mega Menu, khiến khi người dùng di chuột xuống thì bị mất sự kiện `:hover`. Đồng thời các link con chưa được gắn sự kiện lọc và vị trí menu bị lệch khỏi màn hình bên trái.  
- **Nhận xét & Tinh chỉnh của SV:**  
  1. Thay thế `Rajdhani` bằng **`Chakra Petch`** – font chữ gaming cyberpunk chính thức hỗ trợ 100% tiếng Việt của Google Fonts, giúp mọi tiêu đề hiển thị đồng nhất, sắc lẹm.  
  2. Bổ sung cầu nối hover vô hình (`::before` bridge) và cho phép bấm trực tiếp để ghim menu (`.is-active-menu`). Gắn sự kiện click cho từng danh mục con trong Mega Menu để tự động kích hoạt bộ lọc tab, cuộn mượt xuống `#products` và phát hiệu ứng `card-highlight-3d`.  
  3. Xây dựng bộ hiệu ứng 3D hoàn chỉnh: Lưới không gian viễn tưởng 3D bám sàn Hero (`.hero-3d-grid`), hiệu ứng nghiêng thẻ 3D (`perspective: 1100px; rotateX/rotateY`) kèm vệt phản xạ ánh sáng (`.card-sheen`), và cơ chế lật thẻ 3D 180° (`.product-card-inner`) để soi sơ đồ giải phẫu *3D Tactical Blueprint*.

---

### Lần 5: Chuyển đổi toàn diện sang Pure CSS & HTML (Tuân thủ triệt để quy định không dùng file JS riêng)
- **Prompt đã dùng:**  
  *"Đề bài học phần chỉ kiểm tra kiến thức HTML5 & CSS3 từ Tuần 1 đến Tuần 6 (chưa học JavaScript), do đó không cho phép viết file .js riêng. Hãy loại bỏ hoàn toàn file `main.js`, chỉ giữ đúng 1 lệnh inline `AOS.init()` theo yêu cầu thư viện của đề thi. Hãy chuyển đổi 100% các tính năng tương tác (Đổi màu LED RGB, Bộ lọc Tab sản phẩm, Lật thẻ 3D 180°, Drawer giỏ hàng, Modal đăng nhập, Hamburger menu) sang các kỹ thuật Pure CSS nâng cao (Checkbox Hack, Radio Hack, :target, :checked)."*
- **Kết quả AI tạo ra:**  
  1. Sử dụng Radio Hack (`#theme-xxx:checked ~ * { --hue }`) để đổi toàn bộ bảng màu Neon LED RGB chỉ bằng CSS thuần.  
  2. Sử dụng Radio Hack (`#filter-xxx:checked ~ .product-grid .product-card:not(...)`) để lọc sản phẩm ngay tức thì mà không cần một dòng JS nào.  
  3. Sử dụng Checkbox Hack (`.flip-checkbox:checked ~ .product-card-inner`) để thực hiện xoay lật 3D 180° mượt mà.  
  4. Sử dụng `:target` cho Auth Modal và Checkbox Hack cho Cart Drawer.  
  5. Sử dụng `animation-timeline: scroll()` cho thanh tiến độ cuộn trang.  
- **Nhận xét & Tinh chỉnh của SV:**  
  Website vẫn giữ nguyên 100% trải nghiệm tương tác sinh động, đồ họa 3D sắc sảo và hiện đại, nhưng đáp ứng tuyệt đối yêu cầu học thuật không sử dụng file JS của học phần Thiết kế Web LHU. Toàn bộ mã nguồn hoàn toàn sạch bóng JavaScript tự viết.

---

### Lần 6: Nâng cấp Toàn diện Bộ sưu tập Animation Chuẩn Esports & Cyberpunk (100% Pure CSS)
- **Prompt đã dùng:**  
  *"Đề xuất và triển khai các hiệu ứng animation đỉnh cao cho CyberPulse Esports:  
  1. Hiệu ứng Cyberpunk RGB Glitch Text (tách quang sai Cyan/Magenta) cho tiêu đề Hero `CYBERPULSE APEX PRO 8K`.  
  2. Tia Laser Holographic Scanner Sweep quét lướt qua card sản phẩm khi hover chuột.  
  3. Hiệu ứng Dải viền Neon xung điện tuần hoàn (Flagship Pulse Glow) trên thẻ so sánh Apex Pro 8K.  
  4. Vệt sáng quét qua nút bấm kêu gọi hành động (CTA Button Shimmer) mỗi 3.8s.  
  5. Cột sóng âm Audio Equalizer 4 vạch nhảy động bên cạnh biểu tượng âm thanh 7.1.  
  6. Con trỏ Terminal dòng lệnh nhấp nháy ở khung System Badge.  
  7. Hiệu ứng ngàm kỹ thuật HUD 4 góc (Corner Brackets) bung nở ánh sáng neon khi hover card sản phẩm.  
  Yêu cầu bắt buộc: 100% Pure CSS keyframes, tăng tốc phần cứng GPU, 60fps mượt mà, không dùng JS."*
- **Kết quả AI tạo ra & Tinh chỉnh của SV:**  
  1. Tích hợp trọn vẹn bộ 7 hiệu ứng animation đỉnh cao bằng `@keyframes`, `clip-path: inset(...)`, pseudo-elements `::before`/`::after` và `filter: drop-shadow()`.  
  2. Tối ưu hóa chu kỳ phát động (glitch chỉ giật nhẹ mỗi 3-4s thay vì giật liên tục để tránh mỏi mắt người dùng).  
  3. Toàn bộ hiệu ứng được biên dịch trực tiếp trên GPU máy khách, giữ tốc độ khung hình ổn định 60fps trên cả thiết bị di động.

---

## 3. Đánh giá cá nhân về quá trình Vibe Coding

### AI đã giúp bạn tiết kiệm thời gian ở phần nào nhất?
1. **Khởi tạo Design System & CSS Boilerplate:** AI tính toán cực nhanh các dải màu HSL, gradient cyberpunk phức tạp và các biến khoảng cách, giảm 80% thời gian viết CSS lặp lại.
2. **Xây dựng dữ liệu mẫu & thông số kỹ thuật:** Các card sản phẩm với thông số eSports thực tế (8.000Hz, 30.000 DPI, Switch Quang Gen-3) được điền đầy đủ, giúp website trông sống động như một trang thương mại điện tử chuyên nghiệp thật sự.
3. **Kỹ thuật Pure CSS State Management:** AI áp dụng thành thạo các kỹ thuật CSS nâng cao (Checkbox Hack, Radio Hack, :target) để thay thế hoàn toàn JavaScript, giúp trang web đạt tính tương tác cao mà không vi phạm quy định cấm viết file JS của đề thi.

### Bài học rút ra khi đặt câu hỏi (Prompt) cho AI trong thiết kế web?
1. **Nguyên tắc "Đặc tả kỹ thuật trước, viết mã sau":** Cần nêu rõ chuẩn thẻ ngữ nghĩa (`<figure>`, `<aside>`, `<nav>`) và phương pháp bố cục (Flexbox hay CSS Grid) ngay trong Prompt ban đầu. Nếu chỉ yêu cầu "Làm cho tôi một website bán hàng", AI sẽ có xu hướng lạm dụng thẻ `<div>` vô nghĩa.
2. **Kỹ năng "Debug & Refine" (Tinh chỉnh lặp lại):** AI không bao giờ hoàn hảo ở lần sinh mã đầu tiên. Sinh viên với vai trò "Kiến trúc sư trưởng" (Human Architect) phải trực tiếp soi mã nguồn trên Chrome DevTools (F12), phát hiện các điểm nghẽn (cuộn ngang, lỗi trễ AOS, màu hardcode) để ra lệnh sửa đổi đích danh từng class và dòng code.
3. **Tôn trọng tính nhất quán UI/UX:** Luôn ép AI tuân thủ biến `:root` đã khai báo thay vì để AI tự do sinh thêm mã màu lạ làm mất đi sự đồng nhất của toàn bộ trang web.
