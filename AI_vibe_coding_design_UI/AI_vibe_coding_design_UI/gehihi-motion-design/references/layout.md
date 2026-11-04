# Bố cục và component

## Thích ứng theo loại trang

| Loại trang | Cách vận dụng |
|---|---|
| Dịch vụ | Lợi ích → nhu cầu → giải pháp → quy trình → bằng chứng → hành động |
| Học tập | Mục tiêu → khó khăn → tài nguyên → lộ trình → kết quả có nguồn → hành động |
| Portfolio | Giới thiệu → dự án → cách làm → năng lực → liên hệ |
| Sản phẩm | Lợi ích → mô hình sản phẩm → cách hoạt động → trường hợp sử dụng → hành động |
| Dashboard | Ưu tiên workflow/dữ liệu; vận dụng chữ, spacing và micro-interaction; hạn chế ambient |

## Grid và nhịp

- Bắt đầu container khoảng 1160–1240 px, gutter co giãn 16–40 px; điều chỉnh theo dữ liệu.
- Hero desktop khoảng 60/40, gap 28–64 px; mobile một cột, nội dung trước minh họa.
- Section gap khoảng 64–112 px, giảm khi nội dung ngắn. Không để ảnh quá cao tạo khoảng trắng vô nghĩa.
- Dùng thang spacing nhất quán: 4, 8, 12, 16, 24, 32, 48, 64 px là một điểm bắt đầu.
- Giới hạn đoạn dài khoảng 55–65 ký tự mỗi dòng khi đủ rộng.
- Dùng minmax(0,1fr), min-width:0 và wrap cho dữ liệu dài. Sửa nguyên nhân tràn trước clipping.

## Typography tiếng Việt

- Có thể dùng Baloo 2 / Be Vietnam Pro / IBM Plex Mono nếu phù hợp; giữ font dự án nếu đã tốt.
- Bắt đầu H1 khoảng 40–86 px, H2 30–52 px, body 16–19 px; dùng clamp và thử tiêu đề thật.
- Dùng leading tiêu đề khoảng 1.05–1.12 rồi kiểm tra dấu. Không rập khuôn leading 0.98 của nguồn.
- Dùng text-wrap:balance nếu thích hợp; tránh br cố định cho desktop trên mọi viewport.
- Dành chỗ cho dấu khi dùng mask theo dòng; không cắt glyph để làm hiệu ứng.
- Dùng mono cho timestamp/số/nhãn ngắn. Tải đúng weight, có fallback và font-display.

## Hero nhiều lớp

1. Tạo nhãn ngắn, H1, mô tả, CTA và bằng chứng thật ở cột nội dung.
2. Chọn phone mockup, cửa sổ app, sơ đồ hoặc ảnh có chú thích theo sản phẩm, không bắt buộc điện thoại.
3. Phối 3–5 lớp, quản lý z-index/pointer-events; không chặn nút hoặc che chữ.
4. Trang trí phải liên quan nội dung. Không thêm mascot chỉ vì trang nguồn có mascot.
5. Reserve ratio/kích thước cho ảnh, crop giữ đối tượng quan trọng.
6. Gắn nhãn dữ liệu minh họa khi cần; không phát lặp thông báo mô phỏng cho screen reader.

## Hàng vấn đề–giải pháp

- Desktop: trục nhỏ → nhu cầu → card giải pháp. Mobile: trục ở cạnh, hai nội dung xếp dọc.
- Đặt trục trang trí absolute trong vùng có kích thước; giữ nội dung ở normal flow.
- Dùng dấu/nhãn/hình thức cạnh màu để thể hiện trạng thái.
- Xác định cuộn ngược có trả trạng thái không; không gọi trạng thái scroll là tác vụ backend hoàn thành.

## Timeline và luồng

- Dùng ngang khi đủ chỗ; chuyển dọc khi nhãn/mô tả chật. Không cố giữ nhiều cột trên màn hình hẹp.
- Giữ điểm mốc, fill và nhãn cùng hệ tọa độ, đúng thứ tự đọc.
- Dùng đầu vào → xử lý → đầu ra khi có quan hệ thật; mobile xếp dọc.
- Dùng đường chia và typography cho phần nguyên tắc để thay nhịp với card.

## Story, form và FAQ

- Giới hạn tỷ lệ ảnh câu chuyện, xoay nhẹ nếu không gây tràn hoặc mất chủ thể.
- Form có nhãn, help text và lỗi rõ; preview/copy chỉ khi hữu ích cho nhiệm vụ.
- Dùng details/summary cho FAQ cơ bản hoặc component accessible hiện có.
- Dùng anchor cho điều hướng và button cho hành động, tên có động từ cụ thể.

## Màu và độ sâu

Lấy mọi màu từ palette người dùng. Tạo độ sâu bằng phân lớp, kích thước, vị trí, viền và độ trong suốt; nếu được dùng shadow/glow, lấy màu từ token đã chọn. Không giấu palette khác trong SVG, gradient hoặc trạng thái hover.
