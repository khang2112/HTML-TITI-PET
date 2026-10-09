# CẬP NHẬT MỚI — 09/10/2026

**MỞ ĐÚNG BẢN MỚI:** `MO_GIAO_DIEN_DA_CAP_NHAT.html` hoặc `02_HTML_doc_lap/appointments.html` sau khi GIẢI NÉN ZIP mới. Không sử dụng file `BAN_GOC_MOT_FILE_DE_DOI_CHIEU.html` (lưu bản thiết kế ban đầu để so sánh) và không mở file từ bộ ZIP cũ.

- Đã bỏ badge UCxxx ở phần đầu các màn hình nghiệp vụ.
- Có nút “＋ Thêm khách mới” tại Đặt lịch Spa, POS, tiếp nhận khách vãng lai và form chọn chủ nuôi khi thêm pet.
- Có nút “＋ Thêm thú cưng” tại Đặt lịch Spa và tiếp nhận trực tiếp, hỗ trợ tạo pet ngay sau khi tạo khách.
- Khi lưu khách/pet mới, tự động chọn bản ghi vừa tạo, giữ các giá trị form trước đó nếu có.
- `assets/js/app.js` là mã điều khiển hiển thị động; sửa HTML mà không sửa JS có thể bị ghi đè khi trang render lại.
- Dữ liệu mẫu lưu trong trình duyệt; cần chạy từ cùng một thư mục để các trang kết nối đúng.

---

# TiTi Pet — TOÀN BỘ MÃ NGUỒN TỪNG TRANG HTML

Tạo lại từ bản thiết kế `TITIPET.pdf` và báo cáo nghiệp vụ `Nhom06_REPORT_ApplicationDevelopment[v4].docx`, sử dụng prototype ban đầu làm codebase.

## BẠN ĐƯỢC GÌ?

- `index.html` hoặc `DANH_SACH_TRANG.html`: danh mục liên kết đến tất cả màn hình / trạng thái.
- `01_HTML_tung_trang/`: **16 file HTML riêng**. Mỗi file chứa `#root` với markup *thực tế của trang đó* (không phải trang HTML trống), đồng thời dùng CSS và JS chung để thao tác và cập nhật dữ liệu.
- `assets/css/style.css`: **toàn bộ CSS** (bộ màu, layout, thành phần UI, responsive, in hóa đơn).
- `assets/js/app.js`: **toàn bộ JavaScript, có đánh dấu 24 phần chính** (dữ liệu demo, phân quyền mô phỏng, các xử lý form, navigation, tích điểm, thanh toán, kho, đổi trả, đối soát).
- `02_HTML_doc_lap/`: **16 file HTML TỰ CHỨA**, từng file có đủ CSS và JavaScript của ứng dụng, phù hợp cho người muốn sao chép từng trang một.
- `04_HTML_MARKUP_DE_DOC/`: **16 file markup HTML đã được xuống dòng**, dễ học cấu trúc DOM, dùng lại khi làm Figma.
- `TONG_HOP_TOAN_BO_CODE_16_TRANG_HTML.txt`: **toàn bộ mã HTML/CSS/JS của cả 16 trang trong một file text** để xem/copy bằng VS Code.
- `03_Trang_thai_va_popup/`: **16 file trạng thái form / popup**, có sẵn mã HTML cụ thể để làm từng frame trong Figma.
- `FIGMA_HANDOFF.md`: tài liệu use case, UX flow và design system.

## HƯỚNG DẪN XEM MÃ NGUỒN

1. Mở `DANH_SACH_TRANG.html` để chọn màn hình.
2. Dùng VS Code hoặc trình soạn thảo khác để mở `01_HTML_tung_trang/appointments.html`, `01_HTML_tung_trang/pos.html`, `01_HTML_tung_trang/inventory.html`... Ở đây bạn thấy **đầy đủ các tag HTML của đúng trang**, không phải duy nhất `<div id=root></div>`.
3. Nếu muốn lấy **mã nguồn của một trang bao gồm CSS + JS**, vào `02_HTML_doc_lap/<tên trang>.html`.
4. Khi dựng Figma, mở màn hình trong Chrome ở khổ desktop 1440 × 900 hoặc 1512 × 980, sau đó có thể thiết kế lại frame và component. `03_Trang_thai_va_popup/` giúp xem những popup đặc thù.

## CHẠY CÁC LUỒNG TƯƠNG TÁC

Khuyến nghị dùng local server để `sessionStorage`/`localStorage` dùng chung origin giữa các trang:

```bash
cd TiTiPet_DAY_DU_MA_NGUON_HTML
python -m http.server 8000
```

Sau đó truy cập `http://localhost:8000/01_HTML_tung_trang/login.html`.
Chọn 1 trong 3 vai trò: **Lễ tân**, **Thợ Spa**, **Quản lý**.

- **Mở / Chốt ca**: `shift.html` (cùng một trang có các trạng thái theo dữ liệu).
- **Đặt lịch** → `appointments.html`, rồi **Tiếp nhận** → `reception.html`, sau đó **POS** → `pos.html`.
- **Thực hiện Spa** → `spa.html`, theo dõi tiến độ và bàn giao.
- **Bán hàng / Đổi trả / In hóa đơn** → `pos.html`, `returns.html`, `invoices.html`.
- **Khách hàng / Thú cưng** → `customers.html`, `pets.html`.
- **Quản lý kho / bảng giá / chương trình** → `inventory.html`, `catalog.html`, `promos.html`.
- **Báo cáo và flow** → `reports.html`, `flow.html`.

> Dữ liệu là dữ liệu mô phỏng, các quy tắc bảng giá minh họa được giải thích trong handoff. Không có backend xác thực, SQL, thanh toán thật hoặc tích hợp phần cứng. Một số trạng thái cần dữ liệu tạo trước thông qua thao tác ở các trang khác. Các mẫu popup Figma có thể dùng như khung giao diện ngay cả khi chưa có bản ghi giao dịch.

## DANH SÁCH 16 TRANG

- `login.html` — Đăng nhập: Đăng nhập, đăng nhập nhanh theo vai trò
- `dashboard.html` — Trang chủ và tổng quan: Thống kê, lịch, thao tác nhanh
- `shift.html` — Mở ca và chốt ca: Kiểm tra thiết bị, nhập quỹ, đối soát, quản lý duyệt
- `appointments.html` — Đặt lịch Spa: Lịch hẹn, kiểm tra trùng, thêm/dời/hủy
- `reception.html` — Tiếp nhận thú cưng: Cân nặng, lông/da, phụ thu, xác nhận thanh toán trước
- `spa.html` — Điều phối Spa: Tiến độ thợ, vật tư, bàn giao
- `pos.html` — Bán hàng POS: Giỏ hàng, khuyến mãi, VIP, điểm, thanh toán
- `returns.html` — Đổi trả hàng: Tra cứu hóa đơn, kiểm điều kiện đổi trả
- `invoices.html` — Hóa đơn và giao dịch: Tra cứu, chi tiết, in hóa đơn, xuất dữ liệu
- `customers.html` — Khách hàng và VIP: Quản lý hồ sơ, hạng thành viên, điểm
- `pets.html` — Hồ sơ thú cưng: Quản lý thú cưng và chủ nuôi
- `inventory.html` — Quản lý kho: Nhập hàng, tồn kho, hạn sử dụng
- `catalog.html` — Danh mục và bảng giá: Dịch vụ, sản phẩm và cấu hình giá
- `promos.html` — Khuyến mãi: Tạo, sửa, bật/tắt chương trình
- `reports.html` — Báo cáo: Doanh thu, kênh bán, thống kê
- `flow.html` — Luồng nghiệp vụ: Use Case, thiết kế UX và Figma handoff

## DANH SÁCH POPUP / VARIANTS

- `03_Trang_thai_va_popup/reception__walkin.html` — Khách đến trực tiếp
- `03_Trang_thai_va_popup/appointments__editappt.html` — Dời lịch hẹn
- `03_Trang_thai_va_popup/customers__newcustomer.html` — Thêm khách hàng
- `03_Trang_thai_va_popup/customers__editcustomer.html` — Sửa khách hàng
- `03_Trang_thai_va_popup/pets__newpet.html` — Thêm thú cưng
- `03_Trang_thai_va_popup/pets__editpet.html` — Sửa thú cưng
- `03_Trang_thai_va_popup/catalog__newproduct.html` — Thêm sản phẩm
- `03_Trang_thai_va_popup/catalog__editproduct.html` — Sửa sản phẩm
- `03_Trang_thai_va_popup/catalog__newservice.html` — Thêm dịch vụ
- `03_Trang_thai_va_popup/catalog__editservice.html` — Sửa dịch vụ
- `03_Trang_thai_va_popup/inventory__importstock.html` — Nhập hàng vào kho
- `03_Trang_thai_va_popup/promos__newpromo.html` — Tạo khuyến mãi
- `03_Trang_thai_va_popup/promos__editpromo.html` — Sửa khuyến mãi
- `03_Trang_thai_va_popup/reception__rejectappt.html` — Từ chối tiếp nhận Spa
- `03_Trang_thai_va_popup/pos__addservice.html` — Thêm dịch vụ tại POS
- `03_Trang_thai_va_popup/dashboard__search.html` — Tìm kiếm toàn hệ thống

## LUỒNG TEST NHANH

1. Login bằng Lễ tân. Vào Mở ca: tích 4 mục thiết bị + tiền đầu ca.
2. Vào đặt lịch/tiếp nhận: chọn lịch, cân pet, chuyển sang POS và thanh toán trước 100%.
3. Đổi vai trò Thợ Spa: chạy thao tác bắt đầu → hoàn thành → bàn giao.
4. Đổi vai trò Quản lý: nhập kho, điều chỉnh KM, duyệt chốt ca.

## KIỂM TRA HTML

Các trang đã prerender markup thật. JavaScript sẽ đồng bộ nội dung với dữ liệu demo được lưu trong trình duyệt khi trang tải xong.
