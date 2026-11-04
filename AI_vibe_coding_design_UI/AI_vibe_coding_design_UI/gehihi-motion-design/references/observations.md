# Ghi nhận tham chiếu

Nguồn: https://www.gehihiai.com/ — quan sát ngày 27/10/2026, Asia/Saigon.

## Bằng chứng và giới hạn

- Đã mở website, quan sát desktop khoảng 1363 × 936 px, dùng anchor đi qua các phần.
- Đã xem hero, cảnh nhân vật ở đoạn chuyển tiếp, các hàng vấn đề–giải pháp, timeline và câu chuyện có ảnh.
- Đã đọc DOM, computed style, CSS và mã animation inline để phân tích giao diện. Không có mã backend hoặc quyền vào dự án nguồn.
- Đã đọc responsive/reduced-motion trong CSS, chưa trực tiếp kiểm tra viewport mobile của nguồn.
- Đã thấy cấu trúc form có input, lựa chọn, preview, copy và mở email; chưa gửi hay kiểm thử gửi thông tin.
- Không xác minh tuyên bố kinh doanh/sản phẩm của nguồn; trang có thể thay đổi sau ngày quan sát.

## Cơ chế quan sát được

- Hero hai cột bất đối xứng: tiêu đề rất lớn bên trái, mô hình điện thoại có ảnh và thông báo bên phải.
- Dây đèn SVG, texture nhẹ, khung thiết bị và thẻ nổi tạo nhiều lớp chiều sâu.
- Nhân vật nhỏ dùng SVG và phụ kiện theo vai trò; mắt/dụng cụ có CSS animation.
- Nhân vật ở đoạn chuyển tiếp di chuyển qua lại trên một đường dẫn, nhún nhẹ và phân lớp xa/gần.
- Các hàng nhu cầu–giải pháp gắn với trục dọc; fill theo cuộn, hàng đổi trạng thái gần vùng giữa viewport và có thể trả trạng thái khi cuộn ngược.
- Timeline nhiều mốc có fill theo cuộn; một mốc đặc biệt được nhấn rõ.
- Các phần tiếp theo thay nhịp: luồng ba khối, nguyên tắc, câu chuyện có ảnh, các bước, form, lộ trình, FAQ.
- Navigation dùng anchor nội trang. Không có bằng chứng đủ để gán custom cursor, WebGL, Three.js, menu sticky hoặc smooth-scroll library cho nguồn.

## Thông số đọc được

| Thành phần | Giá trị ở nguồn |
|---|---|
| Container | Max 1160 px |
| Gutter | Clamp 16–40 px |
| Section spacing | Clamp 64–112 px |
| Hero grid | 1.25 : 0.75 |
| Display font | Baloo 2 |
| Body font | Be Vietnam Pro |
| Font dữ liệu ngắn | IBM Plex Mono |
| H1 | Clamp 42–86 px, weight 800, leading gốc rất chặt |
| H2 | Clamp 30–52 px, weight 800 |
| Body | 16 px / 1.65 |
| Card radius | Khoảng 20–24 px |
| Phone | Rộng tối đa khoảng 300 px, màn hình 9:19 |
| Responsive khai báo | 900 px và 480 px |

Dùng các số này làm điểm tham chiếu, không áp cứng. Nới leading khi cần để không mất dấu tiếng Việt; kiểm tra tỷ lệ ảnh và độ cao section trong bản render thật.

## Chuyển động đọc được

- Có GSAP và ScrollTrigger; hiệu ứng không đòi hỏi React.
- Tiêu đề vào theo dòng, từ dưới lên kèm xoay nhỏ: khoảng 1 giây, stagger 0.12 giây.
- Điện thoại vào khoảng 1.2 giây, sau đó float nhẹ với nhịp 2.6 giây mỗi chiều.
- Thông báo xuất hiện theo thứ tự: khoảng 0.5 giây mỗi lần, lệch khoảng 1.4 giây.
- Trục các hàng có scrub khoảng 0.6 giây; điểm đổi trạng thái gần 62% viewport.
- Timeline dùng scaleX/scaleY theo breakpoint, scrub khoảng 0.5 giây.
- Có nhánh reduced-motion và fallback khi không có thư viện, kèm một số CSS tắt animation.

Chỉ lưu cơ chế đã phân tích, không lưu mã nguồn sao chép. Đề xuất bổ sung cleanup, xử lý đổi breakpoint, dừng loop ngoài viewport và kiểm tra accessibility trong dự án mới.

## Phần cố ý bỏ khỏi skill

Không lưu palette, mã màu, theme mặc định, ảnh/logo/mascot, văn bản thương mại hoặc thông tin liên hệ của nguồn. Giữ quyền chọn màu và tài sản cho người dùng.
