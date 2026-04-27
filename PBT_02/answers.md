## Phần A

### Câu A1 (5đ) — Input Types
1. type="email" → Ô nhập text, tự kiểm tra có @ → Dùng cho đăng ký tài khoản
2. type="password" → Ô nhập bị ẩn ký tự → Dùng cho đăng nhập
3. type="number" → Ô nhập số, có nút tăng/giảm → Nhập số lượng sản phẩm
4. type="tel" → Ô nhập số điện thoại → Nhập thông tin giao hàng
5. type="url" → Kiểm tra định dạng link → Nhập website
6. type="date" → Hiển thị chọn ngày → Chọn ngày giao hàng
7. type="file" → Upload file → Upload ảnh sản phẩm
8. type="checkbox" → Tick nhiều lựa chọn → Lọc sản phẩm
9. type="radio" → Chọn 1 → Chọn phương thức thanh toán
10. type="search" → Ô tìm kiếm → Thanh search sản phẩm

### Câu A2 (5đ) — Validation Attributes

<!-- Trường hợp 1 -->
`<input type="text" required value="">`   <!-- User để trống -->
    - không submit được vì required bắt buộc phải nhập dữ liệu

<!-- Trường hợp 2 -->
`<input type="email" value="abc">`        <!-- User gõ "abc" -->
    - Không submit được vì ko đúng định dạng email (thiếu @)

<!-- Trường hợp 3 -->
`<input type="number" min="1" max="10" value="15">` <!-- User gõ 15 -->
    - ko submit được vì vượt quá giá trị max

<!-- Trường hợp 4 -->
`<input type="text" pattern="[0-9]{10}" value="abc123">` <!-- User gõ "abc123" -->
    -Ko submid dc vì pattern phải là 10 chữ số

<!-- Trường hợp 5 -->
`<input type="password" minlength="8" value="123">`  <!-- User gõ "123" -->
    - vẫn submit dc vì không có thuộc tính required nên trường này không bắt buộc. minlength không đủ để chặn submit nếu input không required.

### Câu A3 (5đ) — Accessibility

1. Tại sao `<label for="email">` quan trọng cho người dùng screen reader?
    - Vì nó hỗ trợ cho screen reader đọc đước label này cho cái gì.
    
2. Khi nào dùng `<fieldset>` + `<legend>`? Cho ví dụ cụ thể.
    - dùng khi nhóm các thông tin liên quan với nhau trong form
    - vd: dùng để nhóm thông tin giao hàng
        ```
        <fieldset>
            <legend>Thông tin giao hàng</legend>

            <label for="name">Tên</label>
            <input id="name" type="text">

            <label for="address">Địa chỉ</label>
            <input id="address" type="text">
        </fieldset>
        ```
3. aria-label dùng khi nào? Tại sao KHÔNG nên dùng aria-label khi đã có <label>?
    - dùng aria-label khi ko dùng text hiện thị(như label) hoặc dùng khi sử dụng nút ko rõ nội dung nhứ icon,..vv
    - Khi có label rồi thì screen reader sẽ có thể đọc trùng nội dung giữa label và aria-label

### Câu A4 (5đ) — Media

1. Giải thích thuộc tính `loading="lazy"` trên thẻ `<img>`. Nó cải thiện gì? Khi nào KHÔNG nên dùng?
    - thuộc tính `loading="lazy"` làm ảnh tải khi người dùng lăn chuột tới. 
    - giúp load trang nhanh hơn, tiết kiệm băng thông cho người dùng và máy chủ.
    - Không lazy load ảnh "above the fold" (ảnh hero, logo, ảnh đầu tiên user thấy) 
    nếu không thì trang lúc mới vào sẽ bị trống . vậy nên chỉ lazy load ảnh bên dưới

2. Tại sao nên cung cấp nhiều `<source>` trong thẻ `<video>`? Liệt kê ít nhất 3 format video web phổ biến.
    - Vì không phải trình duyệt nào cũng hỗ trợ cùng một định dạng video
    - các format video web phổ biến là:
        - MP4 (.mp4)
        - WebM (.webm)
        - OGG / OGV (.ogv)

3. Thuộc tính `alt` trên `<img>` dùng để làm gì? 
    - Thuộc tính `alt` trên `<img>` dùng để mô tả ảnh nếu ko load đc,
    giúp cho screen reader đọc và SEO hiểu nội dung ảnh.


   Viết `alt` tốt cho 3 trường hợp: 
    - Ảnh sản phẩm iPhone 16 ->> `<img src = "Iphone16.jpg" alt = "Iphone 16, 256GB, màu Tintan ">`
    - Ảnh trang trí (decorative) `<img src = "background.jpg" alt = "">`
    - Ảnh biểu đồ doanh thu Q1/2026 ` <img src = "chart.png" alt = "Biểu đồ doanh thu quý 1 năm 2026">`

### Câu A5 (5đ) — So sánh `<figure>` vs `<img>`
```html
<!-- Cách 1 -->
<img src="product.jpg" alt="iPhone">

<!-- Cách 2 -->
<figure>
    <img src="product.jpg" alt="iPhone 16 Pro Max 256GB Titan">
    <figcaption>iPhone 16 Pro Max — 25.990.000đ</figcaption>
</figure>
```

- Khi nào dùng Cách 1, khi nào dùng Cách 2? Cho 2 ví dụ thực tế cho mỗi cách.
    - dùng cách 1 khi:
        - ảnh đơn giản ko cần cần chú thích riêng.
        - thông tin đã có trong text xung quanh.
        - ảnh chỉ đóng vai tro minh họa
    - vd:
        1. Ảnh thumbnail sản phẩm trong danh sách:
            `<img src="iphone.jpg" alt="iPhone 16">`
        2. Icon hoặc ảnh nhỏ trong bài viết:
            `<img src="icon-cart.png" alt="Giỏ hàng">`
    - dùng cách 2 khi:
        - ảnh là nội dung chính
        - Cần chú thích riêng biệt
        - Muốn nhóm ảnh + mô tả thành 1 khối sematic
    - vd:
        1. Trang chi tiết sản phẩm:
            ```
            <figure>
                <img src="iphone16.jpg" alt="iPhone 16 Pro Max màu Titan">
                <figcaption>iPhone 16 Pro Max — Giá 25.990.000đ</figcaption>
            </figure>
            ```
        2. Biểu đồ trong báo cáo:
            ```
            <figure>
                <img src="chart.png" alt="Biểu đồ doanh thu Q1 2026">
                <figcaption>Doanh thu tăng trưởng liên tục qua 3 tháng</figcaption>
            </figure>
            ```
## Phần B
### Câu B1
Xác nhận password: (cùng rules — giải thích trong answers.md tại sao HTML không thể validate confirm password)
   - HTML không thể tự validate “xác nhận password” vì nó chỉ kiểm tra từng input riêng lẻ, không so sánh được giá trị giữa hai input khác nhau. 

