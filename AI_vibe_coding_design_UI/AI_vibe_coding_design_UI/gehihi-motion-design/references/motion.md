# Chuyển động và triển khai

## Mục lục

- Motion map để điều chỉnh
- Công nghệ và lifecycle
- Mẫu lifecycle
- Ambient và hiệu năng
- Token màu

## Motion map để điều chỉnh

| Thành phần | Trigger | Chuyển động | Nhịp gợi ý | Reduced-motion |
|---|---|---|---|---|
| H1 | Mount | y 24–48 px → 0, xoay tối đa 2° → 0 | 0.8–1 s, stagger 0.08–0.12 s | Hiện ngay |
| Mô hình sản phẩm | Mount | y 40–60 px → 0, xoay 4–6° → 0 | 1–1.2 s, ease-out | Tĩnh |
| Lớp float | Khi trong viewport | y 6–10 px, yoyo | 2.5–3 s mỗi chiều | Tắt loop |
| Thông báo minh họa | Sau hero | y 20–30 px, scale 0.94 → 1 | 0.4–0.5 s, lệch 1.2–1.6 s | Bản tĩnh |
| Trục tiến trình | Cuộn trong section | scaleX hoặc scaleY 0 → 1 | ease none, scrub khoảng 0.5 s | Hiện đầy đủ |
| Hàng giải pháp | Qua khoảng 60% viewport | Bỏ xoay/độ lệch nhỏ, hiện dấu | 0.3–0.45 s | Ổn định |
| Trang trí | Trong viewport | Nhún/chuyển động giới hạn trong cảnh | Lệch nhịp, có dừng | Tĩnh |
| Button | Hover/focus/press | Dịch lên tối đa 2 px | 0.12–0.18 s | Không dịch |

Ưu tiên một điểm nhìn. Tránh zoom mạnh, nhấp nháy, scroll hijack, custom cursor mất con trỏ chuẩn hoặc bắt người dùng chờ hiệu ứng.

## Công nghệ và lifecycle

- Dùng CSS cho tương tác nhỏ; GSAP/ScrollTrigger cho timeline và scroll khi cần. Tái sử dụng dependency hiện có nếu phù hợp.
- Dùng CSS/SVG trước khi cân nhắc WebGL. Xem tài liệu chính thức phù hợp phiên bản trước khi dùng API chưa chắc chắn.
- Quản lý thư viện bằng package manager và chính sách dự án; không thêm CDN không ghim phiên bản vào production.
- Tách wrapper layout, entrance và float để không tranh transform.
- Với React, dùng context/hook cleanup phù hợp; không tạo animation trên mỗi render. Với HTML thuần, trả hàm cleanup.

## Mẫu lifecycle

Đoạn mẫu được viết riêng cho skill, không trích nguồn. Cung cấp root chứa data attribute tương ứng và dependency do dự án quản lý. Nội dung phải hiển thị mặc định.

```js
export function mountNarrativeMotion(root, gsap, ScrollTrigger) {
  if (!root || !gsap || !ScrollTrigger) return () => {};
  gsap.registerPlugin(ScrollTrigger);
  const media = gsap.matchMedia();
  media.add({
    reduce: '(prefers-reduced-motion: reduce)',
    wide: '(min-width: 901px)',
    narrow: '(max-width: 900px)'
  }, ({ conditions }) => {
    const find = s => root.querySelector(s);
    const all = s => [...root.querySelectorAll(s)];
    const title = all('[data-title-part]');
    const scene = find('[data-scene-entrance]');
    const section = find('[data-progress-section]');
    const fill = find('[data-progress-fill]');
    const rows = all('[data-progress-row]');
    if (conditions.reduce) {
      if (fill) gsap.set(fill, { scaleX: 1, scaleY: 1 });
      rows.forEach(row => row.classList.add('is-revealed'));
      return () => rows.forEach(row => row.classList.remove('is-revealed'));
    }
    if (title.length) {
      gsap.from(title, {
        y: 32, rotation: 1.5, duration: 0.85,
        stagger: 0.1, ease: 'power3.out'
      });
    }
    if (scene) {
      gsap.from(scene, { y: 48, rotation: 4, duration: 1.1, ease: 'power3.out' });
    }
    if (section && fill) {
      const axis = conditions.wide ? 'scaleX' : 'scaleY';
      gsap.set(fill, {
        scaleX: 1, scaleY: 1,
        transformOrigin: conditions.wide ? 'left center' : 'center top'
      });
      gsap.fromTo(fill, { [axis]: 0 }, {
        [axis]: 1, ease: 'none',
        scrollTrigger: {
          trigger: section, start: 'top 75%', end: 'bottom 55%',
          scrub: 0.5, invalidateOnRefresh: true
        }
      });
    }
    rows.forEach(row => {
      ScrollTrigger.create({
        trigger: row, start: 'top 62%',
        onEnter: () => row.classList.add('is-revealed'),
        onLeaveBack: () => row.classList.remove('is-revealed')
      });
    });
    return () => rows.forEach(row => row.classList.remove('is-revealed'));
  }, root);
  return () => media.revert();
}
```

Giữ breakpoint CSS khớp JS. Mẫu dành cho trục ngang desktop, dọc mobile; với trục luôn dọc, dùng scaleY cho mọi breakpoint. Khi đổi breakpoint, matchMedia cần revert và tái tạo đúng hướng.

Ẩn fill trang trí khỏi accessibility tree; để danh sách mốc có ngữ nghĩa. Không coi is-revealed là trạng thái nghiệp vụ.

Refresh trigger khi font/ảnh làm đổi layout, chỉ khi component còn mount; cleanup listener. Không refresh mỗi scroll event.

## Ambient và hiệu năng

- Tách node float khỏi entrance; lưu animation handle.
- Dùng IntersectionObserver pause/resume khi ra/vào viewport; disconnect/kill khi cleanup.
- Tắt khi reduced-motion hoặc người dùng chọn dừng. Với ambient kéo dài, cung cấp cách dừng có tên/trạng thái rõ khi cần.
- Giới hạn quãng đường trong kích thước cảnh thay vì window; tính lại có cleanup khi resize.
- Không đặt opacity:0 cho nội dung thiết yếu trong CSS mặc định.
- Khi thư viện lỗi hoặc reduced-motion, giữ nội dung, thứ tự đọc và tác vụ; dùng minh họa tĩnh.
- Không cập nhật state framework mỗi frame scroll. Tránh blur/backdrop-filter/shadow nặng hàng loạt và will-change thường trực.
- Reserve ảnh đúng ratio, tối ưu kích thước và lazy-load ảnh dưới fold; không lazy-load ảnh hero quan trọng một cách máy móc.

## Token màu

Ánh xạ tên trong palette sang CSS kebab-case, ví dụ accentText → --accent-text. Chỉ sinh giá trị sau khi người dùng cung cấp hoặc cho phép dẫn xuất. Không thêm fallback màu. Icon/SVG dùng currentColor hoặc token decoration; focus, glow, gradient và shadow cũng phải dùng token.
