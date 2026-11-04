# Tiêu chí nghiệm thu

## Bảng màu

- Mọi giá trị trong palette.template.json của skill là chuỗi rỗng.
- Dự án chỉ dùng màu người dùng chọn hoặc đã cho phép dẫn xuất.
- Kiểm tra cả CSS, SVG, shadow, gradient, focus, icon và trạng thái.
- Thiếu palette thì gọi đúng là cấu trúc/chuyển động đang chuẩn bị, không phải bản màu hoàn thiện.

## Thị giác

- Hero có điểm nhìn chính và minh họa hợp lĩnh vực; có hierarchy và thay nhịp bố cục.
- Không mất dấu tiếng Việt, font lỗi, ngắt dòng xấu, tràn ngang hoặc trang trí che CTA.
- Không tạo section cao bất thường do ảnh; không dùng clipping che nội dung tràn.
- Không có số liệu, lời chứng thực hoặc khách hàng giả.

## Tương tác và accessibility

- Anchor/CTA/menu/FAQ/form hoạt động theo phạm vi thực hiện.
- Bàn phím đi đúng thứ tự, focus rõ, không bị khóa.
- Form có nhãn và lỗi rõ; copy có phản hồi đúng và fallback nếu có tính năng này.
- Trạng thái có văn bản/dấu/hình thức bên cạnh màu.
- Không gửi form, liên lạc hoặc xuất bản khi chỉ đang kiểm tra.

## Chuyển động

- Kiểm tra đầu/giữa/cuối, cuộn ngược và thay đổi viewport qua breakpoint.
- Không duplicate trigger/loop/listener khi resize, remount hoặc chuyển trang.
- Reduced-motion có nội dung và tác vụ đầy đủ, không chạy ambient không cần thiết.
- Thư viện animation lỗi vẫn có trang đọc và dùng được.
- Dừng loop ngoài viewport và có cách dừng ambient khi cần; không giật/chặn cuộn.

## Kỹ thuật

- Xem desktop, tablet, điện thoại và ca hẹp 320 px với dữ liệu dài.
- Kiểm tra console sau tương tác/resize và build/lint liên quan.
- Sửa lỗi quan sát được, kiểm tra lại đúng phần ảnh hưởng; không thêm bộ test nặng cho chỉnh sửa thị giác nhỏ.
- Ghi rõ viewport/hành vi chưa kiểm tra. Không dùng build pass hoặc điểm đẹp tự chấm để thay bản render thật.

Chỉ gọi bản triển khai sẵn sàng khi palette đã được chọn, tác vụ chính hoạt động, không mất nội dung/tràn ngang, đọc được tiếng Việt, fallback chuyển động ổn và không còn lỗi nghiêm trọng quan sát được.
