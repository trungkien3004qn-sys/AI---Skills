---
name: gehihi-motion-design
description: "Thiết kế hoặc nâng cấp front-end lấy cảm hứng từ gehihiai.com: bố cục kể chuyện, typography tiếng Việt, minh họa nhiều lớp, hero có chiều sâu, GSAP và hiệu ứng theo cuộn. Dùng khi người dùng yêu cầu phong cách Gehihi, website giàu chuyển động hoặc áp dụng skill này trong IDE như Antigravity. Để toàn bộ bảng màu cho người dùng tự chọn; không suy ra hoặc sao chép màu của nguồn."
---

# Gehihi Motion Design

Tạo website có cá tính, mạch nội dung rõ và chuyển động có mục đích. Vận dụng cách kể chuyện của tham chiếu vào sản phẩm đang làm.

## Tài nguyên

- Đọc [references/observations.md](references/observations.md) để phân biệt bằng chứng quan sát và đề xuất.
- Đọc [references/layout.md](references/layout.md) trước khi thiết kế bố cục và component.
- Đọc [references/motion.md](references/motion.md) trước khi viết animation.
- Đọc [references/acceptance.md](references/acceptance.md) trước khi kiểm tra và bàn giao.
- Dùng [assets/palette.template.json](assets/palette.template.json) làm biểu mẫu màu duy nhất; mọi giá trị màu trong bản skill gốc đều để trống.
- Giữ framework và quy ước hiện có. Áp dụng được cho HTML/CSS/JS hoặc framework; không bắt buộc chuyển sang React/Next.js/Tailwind.
- Trong IDE, cung cấp thư mục skill và yêu cầu agent đọc SKILL.md cùng tài nguyên liên kết; không giả định thư mục tự kích hoạt skill.

## Bảng màu: hoàn toàn do người dùng chọn

1. Không điền sẵn, sao chép hoặc suy ra màu của Gehihi. Không mặc định theme tối, sáng hoặc màu thương hiệu.
2. Giữ mọi chuỗi rỗng của palette.template.json. Khi làm website, tạo bản cấu hình riêng trong dự án để người dùng điền; không sửa template gốc.
3. Nếu brief có palette người dùng chọn, ánh xạ sang token ngữ nghĩa. Nếu thiếu, hỏi ngắn gọn họ muốn dùng bảng màu nào; vẫn tiếp tục đọc mã nguồn, dựng cấu trúc và lên kế hoạch chuyển động trong khi chờ.
4. Không thay chuỗi rỗng bằng màu mặc định, kể cả nền, chữ, viền, bóng, gradient, focus, trạng thái, icon hay trang trí SVG. Không đưa mã màu mẫu vào tài liệu skill.
5. Khi thiếu palette, giữ màu hiện hữu của website đang sửa để bảo toàn giao diện; không coi đó là màu được duyệt cho thiết kế mới. Với dự án mới, có thể dựng cấu trúc bằng kiểu mặc định của trình duyệt và gọi đúng là bản cấu trúc chưa có bảng màu.
6. Sinh màu qua CSS custom properties từ token người dùng cung cấp. Dùng currentColor cho icon khi hợp lý. Chỉ dẫn xuất độ trong suốt từ token đã chọn; không tạo thêm sắc màu khi chưa được phép.
7. Nếu thiếu vai trò màu hoặc độ tương phản không đạt, chỉ rõ phần cần bổ sung và xin người dùng chọn/cho phép dẫn xuất. Không tự thay mã màu. Có thể sửa cỡ chữ, độ đậm và bố cục trong phạm vi đã được chọn.
8. Không hỏi chọn màu khi nhiệm vụ chỉ là tạo/sửa chính skill này và yêu cầu giữ palette trống.

## Ngôn ngữ thiết kế

- Chọn một ý tưởng thị giác gắn với sản phẩm: dòng chảy, hành trình, công việc, quá trình hoặc hệ thống. Nối nó qua hero, lợi ích và quy trình.
- Dùng tiêu đề lớn và thân thiện, khoảng cách thoáng, phân cấp rõ giữa tiêu đề, mô tả, nhãn nhỏ và dữ liệu.
- Tạo hero bất đối xứng: nội dung chiếm ưu thế, một cảnh minh họa hoặc mô hình sản phẩm có chủ đích ở bên còn lại.
- Phối lớp có kiểm soát: nền, chi tiết trang trí, chữ, mô hình và một vài chi tiết nổi. Giữ vùng đọc sạch và nút bấm không bị che.
- Xen kẽ bố cục theo nội dung: hero, hàng vấn đề–giải pháp, timeline, luồng thông tin, câu chuyện có ảnh, form, FAQ. Không ép tất cả trang phải có đủ các phần.
- Dùng bo góc mềm và độ sâu chọn lọc. Chỉ thêm shadow/glow/texture/mascot nếu hợp brief; tôn trọng yêu cầu không dùng chúng.
- Dùng tài sản của dự án hoặc tài sản được phép. Không sao chép logo, ảnh, mascot, số liệu, nội dung hay thông tin liên hệ của nguồn.
- Dùng chuyển động để giải thích quan hệ và trạng thái; không coi fade-in hàng loạt là đủ để tái hiện cảm giác của tham chiếu.

## Quy trình

### 1. Hiểu dự án

- Đọc hướng dẫn dự án, cấu trúc mã, dependency, component, token và yêu cầu giới hạn phạm vi.
- Xác định người dùng, hành động chính, nội dung thật và phần được sửa. Dùng thông tin sẵn có; chỉ hỏi dữ kiện thiếu có ảnh hưởng lớn.
- Xử lý palette theo quy tắc trên. Với website có sẵn, ghi nhận giao diện trước khi sửa.
- Không đổi kiến trúc hoặc chức năng ngoài phạm vi vì muốn áp dụng phong cách mới.

### 2. Chốt ý tưởng trước khi code

- Nêu ngắn gọn mục tiêu, ý tưởng minh họa, thứ tự section, CTA và ba điểm chuyển động chủ đạo.
- Thích ứng theo lĩnh vực; không bê câu chuyện thợ sửa ống/tiệm bánh sang sản phẩm không liên quan.
- Dùng hình ảnh thật hoặc khung có kích thước và mô tả rõ nếu chưa có tài sản. Nêu phần còn thiếu.
- Tiếp tục trong phạm vi đã được giao; không biến bản kế hoạch thành bước xin xác nhận bắt buộc.

### 3. Hoàn thiện bản tĩnh

- Làm hierarchy, typography, grid, spacing và component trước animation.
- Đặt nội dung thật, tên nút cụ thể, số liệu có nguồn hoặc ghi rõ minh họa.
- Sửa ngắt dòng, crop hình, tỷ lệ cảnh và dấu tiếng Việt ở desktop/mobile.
- Để nội dung và tác vụ chính hoạt động ngay cả khi JavaScript animation không chạy.

### 4. Thêm chuyển động

- Lập motion map: thành phần, trigger, thuộc tính, thời lượng, easing, cuộn ngược, mobile và reduced-motion.
- Dùng CSS cho phản hồi nhỏ/ambient; dùng GSAP và ScrollTrigger khi cần chuỗi và tiến trình theo cuộn. Tái sử dụng thư viện phù hợp đã có.
- Với landing page đủ dài, chọn một chuyển động mở đầu, một ambient nhẹ và một cơ chế theo cuộn. Giảm bớt với trang ngắn hoặc brief ít chuyển động.
- Ưu tiên transform/opacity; dùng scale cho fill. Tránh thay đổi chiều cao nội dung mỗi frame.
- Tách node chạy entrance và float để không tranh transform. Cleanup khi tháo component, đổi breakpoint và chuyển trang.
- Dừng loop ngoài viewport; hỗ trợ giảm chuyển động và cơ chế dừng ambient kéo dài khi cần. Giữ cuộn tự nhiên.

### 5. Làm tương tác thật

- Triển khai anchor, CTA, menu, FAQ, form và phản hồi đúng ý nghĩa.
- Nếu có preview/copy, cập nhật từ dữ liệu thật, xử lý giá trị thiếu, nội dung dài và lỗi clipboard.
- Không báo gửi thành công khi chỉ tạo nháp, copy hoặc mở ứng dụng khác.
- Dùng semantic HTML, nhãn, focus-visible, bàn phím và aria-live cho thông báo cần thiết. Không chỉ dùng màu thể hiện trạng thái.
- Không tự gửi biểu mẫu, liên hệ hoặc xuất bản trong quá trình kiểm tra giao diện.

### 6. Xem và chỉnh bằng trình duyệt

- Dùng công cụ được phép để xem kết quả thực, gồm đầu/giữa/cuối trang và các trạng thái chuyển động.
- Kiểm tra viewport gợi ý 1440, 1024, 768, 390 px; thêm 320 px cho tràn ngang. Chọn bộ tương đương khi môi trường hạn chế.
- Thử bàn phím, reduced-motion, font chưa tải, thư viện animation lỗi và dữ liệu dài.
- Sửa vấn đề quan sát được, chạy build/lint và kiểm tra liên quan của dự án; kiểm tra lại phần bị ảnh hưởng.
- Ghi rõ phần chưa kiểm chứng nếu không truy cập được trình duyệt/thiết bị. Build pass không thay thế đánh giá thị giác.

## Tránh các lỗi này

- Tự chọn màu, hard-code màu trong component/SVG hoặc cài palette riêng ẩn trong trạng thái.
- Lặp cùng một lưới card ở mọi section; rải chuyển động vào toàn bộ vùng đọc.
- Cắt dấu tiếng Việt do line-height/mask, ép br desktop lên mobile, dùng clipping để che tràn nội dung.
- Ẩn nội dung mặc định chờ animation hoặc khiến người dùng phải đợi hiệu ứng mới bấm được.
- Loop mọi phần tử, cập nhật state framework mỗi frame scroll, hoặc cài thư viện nặng cho tác vụ nhỏ.
- Tự thêm WebGL/3D, custom cursor, smooth-scroll library hoặc menu sticky rồi gọi đó là đặc điểm đã xác minh của nguồn.
- Hứa giống hệt tham chiếu hoặc gọi media query là bằng chứng đã kiểm tra mobile.

## Bàn giao

Tóm tắt hướng thiết kế, hiệu ứng đã làm, cách cung cấp palette và kiểm tra thực tế. Nêu rõ hình ảnh/màu/phần chưa kiểm chứng còn thiếu. Chỉ công bố hoặc triển khai khi nhiệm vụ có yêu cầu tương ứng.
