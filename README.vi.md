# ScopeWeaver — bản Việt hóa của Base27-CVNSS

**ScopeWeaver** là bảng điều khiển tự lưu trữ giúp tổ chức việc nghiên cứu bảo mật bằng nhiều tác tử AI trong **phòng thí nghiệm cách ly**. Mã nguồn ứng dụng kết hợp **Go**, **Next.js** và **PostgreSQL**.

> **Phạm vi sử dụng:** Phong cách giao diện “Red Team” chỉ là thẩm mỹ. Điều khoản kế thừa từ ARTEX không cho phép quét, dò tìm, khai thác hay tấn công bất kỳ website/dịch vụ trực tuyến nào; không cho phép sử dụng cho pentest thực tế, nhiệm vụ Red/Blue Team hoặc môi trường sản xuất. Chỉ nghiên cứu, học tập và xác minh phi phá hoại trên hệ thống tự dựng trong môi trường cách ly. Đọc toàn bộ LICENSE và các điều khoản hiển thị khi đăng nhập.

## Giao diện tiếng Việt

- [Trang giới thiệu tiếng Việt](https://base27-cvnss.github.io/scopeweaver/vi/) — HTML/CSS/JavaScript tĩnh; giao diện tối đen–đỏ, biểu đồ tác tử và các tab minh họa có thể tương tác; không có khả năng quét.
- [Trang tiếng Anh](https://base27-cvnss.github.io/scopeweaver/?lang=en) và [trang tiếng Hàn](https://base27-cvnss.github.io/scopeweaver/ko/) được giữ lại.
- Ứng dụng Next.js thêm lựa chọn `Tiếng Việt`, là ngôn ngữ giao diện mặc định trong nhánh Việt hóa. Có thể đổi sang English hoặc 한국어; lựa chọn được lưu vào trình duyệt.
- Bảng màu mặc định: nền `#08090D`, bề mặt `#12141B`, điểm nhấn `#EF4444`, văn bản `#F1F2F5`. Chế độ sáng vẫn có thể được người dùng chọn.
- Các nhãn, lệnh và màn hình thường dùng đã có bản dịch tiếng Việt được duyệt thủ công. Các câu chưa được duyệt, nhất là điều khoản pháp lý và thông báo backend, **cố ý hiển thị tiếng Anh** để tránh hiểu sai; đây là giai đoạn Việt hóa nền tảng, **chưa phải bản dịch hoàn toàn**.
- Bằng chứng kỹ thuật, yêu cầu HTTP, tham số API, tên tài sản, lệnh, đường dẫn và nội dung do người dùng nhập **không bị dịch**.

## Cài đặt từ mã nguồn

```bash
git clone https://github.com/Base27-CVNSS/scopeweaver.git
cd scopeweaver
./install.sh
```

Hoặc dùng Docker Compose:

```bash
cp .env.example .env
# Mở .env và tự đặt POSTGRES_PASSWORD
docker compose up -d --build
```

Sau khi máy chủ hoạt động, mở `http://localhost:8787` để thiết lập tài khoản quản trị. Bạn cần cơ sở dữ liệu PostgreSQL và một nhà cung cấp LLM do chính bạn cấu hình. Khóa API không được lưu trong trang giới thiệu công khai.

### Chạy thử giao diện nhà phát triển

```bash
cd web
npm ci
NEXT_PUBLIC_MOCK=1 npm run dev
```

Các dữ liệu mô phỏng không thể dùng làm bằng chứng quét hệ thống thực.

## Kiểm thử được khuyến nghị

```bash
cd web && npm test && npm run build && cd ..
go test ./...
node tools/validate-landing.mjs
```

Mã giao diện Next.js có hơn 3.000 thông điệp. Cơ chế tiếng Việt dùng toàn bộ bộ khóa tiếng Anh rồi thay những chuỗi đã Việt hóa; kiểm thử đối chiếu placeholder và thẻ định dạng giữa các ngôn ngữ. Ngôn ngữ của backend hỗ trợ thẻ `vi`, còn nhiều chuỗi phía Go tạm dùng nội dung tiếng Anh để giữ đúng ngữ nghĩa. Cần thêm kiểm thử tích hợp trước khi phát hành.

## Giấy phép, đóng góp và ghi công

Dự án phái sinh từ [ARTEX](https://github.com/Autumn-27/ARTEX) thông qua [ScopeWeaver của cskwork](https://github.com/cskwork/scopeweaver). Giữ ghi công, các thông báo và giấy phép **AGPL-3.0**. Mọi dịch vụ được cung cấp qua mạng dựa trên bản sửa đổi phải tuân thủ nghĩa vụ cung cấp mã nguồn tương ứng.

Xem [README gốc](README.md), [tình trạng kiểm chứng](docs/VERIFICATION.md) và [nguồn gốc](docs/PROVENANCE.md).
