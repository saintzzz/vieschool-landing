# VieSchool

Landing page for [VieSchool](https://vieschool.com) - digital ecosystem for Vietnamese primary schools.

## Products

Two separate product lines:

### Sản phẩm cho người Việt (tiếng Việt)

- **English Arena** - Luyện thi tiếng Anh cho học sinh tiểu học: [ea.vieschool.com](https://ea.vieschool.com)
- **Sổ Chủ Nhiệm Số** - Sổ chủ nhiệm điện tử cho giáo viên: [sochunhiem.vieschool.com](https://sochunhiem.vieschool.com)

### Vietnam travel guides for foreigners (English)

- **AAL Fast Track Guide** - Vietnam airport fast-track and meet-and-greet info: [fasttrack.vieschool.com](https://fasttrack.vieschool.com)

## Hướng dẫn tiếng Việt

### English Arena (cho phụ huynh và học sinh)

- [Luyện thi tiếng Anh trực tuyến tiểu học](https://ea.vieschool.com/guides/luyen-thi-tieng-anh-truc-tuyen-tieu-hoc)
- [Phonics cho học sinh tiểu học](https://ea.vieschool.com/guides/phonics-hoc-sinh-tieu-hoc)
- [Học tiếng Anh theo SGK](https://ea.vieschool.com/guides/hoc-tieng-anh-theo-sgk)
- [Mua gói EA](https://ea.vieschool.com/mua)

### Sổ Chủ Nhiệm Số (cho giáo viên chủ nhiệm)

- [Sổ chủ nhiệm điện tử là gì?](https://sochunhiem.vieschool.com/guides/so-chu-nhiem-dien-tu-la-gi)
- [Mẫu nhận xét chủ nhiệm](https://sochunhiem.vieschool.com/guides/mau-nhan-xet-chu-nhiem)
- [Đánh giá hạnh kiểm theo TT22](https://sochunhiem.vieschool.com/guides/danh-gia-hanh-kiem-tt22)
- [Mua SCN](https://sochunhiem.vieschool.com/mua)

## Vietnam airport fast track (English)

- [Is Vietnam airport fast track worth it?](https://fasttrack.vieschool.com/vietnam-airport-fast-track-worth-it.html)
- [Vietnam immigration wait times](https://fasttrack.vieschool.com/vietnam-immigration-wait-times.html)
- [Vietnam e-visa + fast track guide](https://fasttrack.vieschool.com/vietnam-evisa-fast-track-guide.html)

## Deploy (quan trọng)

`vieschool.com` KHÔNG serve trực tiếp từ Vercel. Kiến trúc:

- Cloudflare Worker `vieschool-landing-proxy` (zone vieschool.com) fetch
  HTML từ jsDelivr CDN pin theo commit SHA của repo này:
  `https://cdn.jsdelivr.net/gh/saintzzz/vieschool-landing@<SHA>/...`
- Route: file có extension -> upstream file; path dạng thư mục -> thử
  `<path>/index.html`, fallback về `/index.html` gốc (SPA behavior).
- Mỗi lần push main: Vercel project deploy (mirror) nhưng domain thật chỉ
  đổi khi bump `REPO` sha trong worker và redeploy qua Cloudflare API
  (PUT /accounts/{id}/workers/scripts/vieschool-landing-proxy).
- jsDelivr @commit URL là immutable; commit mới có thể mất vài giây để
  materialize - worker cache upstream 86400s cho 2xx, 60s cho lỗi.
