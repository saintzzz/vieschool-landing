# Feature Map - vieschool-landing

> Static landing hub for the VieSchool product family. Mined 2026-11-24 (intake brownfield rule).

## Landing: product hub page
- **Purpose:** visitor sees the VieSchool product family and navigates to the right subdomain app
- **Route:** `/` (`index.html`)
- **Preconditions:** none (public, static)
- **Baseline:** hero + product links + footer policy links
- **Navigation:** index.html -> outbound product links
- **Controls:** outbound links `https://congcuso.vieschool.com`, `https://ea.vieschool.com`, `https://fasttrack.vieschool.com`, `https://sochunhiem.vieschool.com`; policy links `/chinh-sach-ban-hang`, `/chinh-sach-bao-mat`, `/dieu-khoan`
- **Expected:** every product link lands on the live subdomain; policy links render their static pages
- **Code entry:** `index.html`
- **State owner:** none (static site)
- **Evidence:** `git ls-files` route inventory + href extraction
- **Updated:** 2026-11-24 | by intake FM mining

## Policy pages (3): ban-hang / bao-mat / dieu-khoan
- **Purpose:** legal/policy content for customers
- **Route:** `/chinh-sach-ban-hang`, `/chinh-sach-bao-mat`, `/dieu-khoan`
- **Preconditions:** none (public, static)
- **Baseline:** policy text renders
- **Code entry:** `chinh-sach-ban-hang/index.html`, `chinh-sach-bao-mat/index.html`, `dieu-khoan/index.html`
- **State owner:** none
- **Updated:** 2026-11-24 | by intake FM mining
