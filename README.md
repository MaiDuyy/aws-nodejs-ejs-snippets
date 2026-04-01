# AWS & Express MVC Snippets

Bộ snippets này giúp tăng tốc độ gõ code cho các dự án sử dụng **Node.js, Express, AWS S3, và AWS DynamoDB**. Thay vì gõ toàn bộ file model hoặc controller khổng lồ, các snippets đã được chia nhỏ ra thành từng module, function cụ thể để tái sử dụng linh hoạt hơn.

## Cách Cài Đặt

1. Mở Visual Studio Code.
2. Nhấn `Ctrl + Shift + P` (hoặc `Cmd + Shift + P` trên Mac).
3. Gõ **"Snippets: Configure User Snippets"** và chọn nó.
4. Chọn file **`javascript.json`** (hoặc `javascriptreact.json` nếu bạn code React).
5. Copy toàn bộ đoạn JSON cấu hình ở trên và dán vào bên trong dấu `{ }` của file JSON.
6. Lưu lại.

## Danh Sách Các Snippets

### 1. Environment & Config
| Prefix | Mô tả |
| :--- | :--- |
| `aws-env` | Render file biến môi trường (`.env`) chứa thông tin AWS, Bucket, DynamoDB. |
| `ex-app` | Dựng nhanh file `app.js` cho Express + EJS. |
| `aws-config` | Cấu hình file kết nối `aws-sdk` cho DynamoDB và S3. |
| `ex-router` | Khởi tạo Express Router tích hợp middleware `Multer`. |

### 2. DynamoDB Model (`aws-model-*`)
| Prefix | Mô tả |
| :--- | :--- |
| `aws-model-init` | Import các biến cơ bản cho 1 file model. |
| `aws-model-getAll` | Hàm lấy toàn bộ Items (`dynamo.scan`). |
| `aws-model-getById` | Hàm lấy 1 Item (`dynamo.get`). |
| `aws-model-create` | Hàm thêm mới Item (`dynamo.put`). |
| `aws-model-update` | Cú pháp gán `update = create`. |
| `aws-model-deleteItem`| Hàm xóa 1 Item (`dynamo.delete`). |
| `aws-model-deleteAll` | Hàm lấy toàn bộ item và lặp để xóa toàn bộ. |

### 3. Express Controller (`ex-ctrl-*`)
| Prefix | Mô tả |
| :--- | :--- |
| `ex-ctrl-init` | Import các thư viện cơ bản (`fs`, `uuid`, `s3`, model). |
| `ex-ctrl-uploadfile` | Hàm xử lý đẩy file lên AWS S3 và trả về URL CDN. |
| `ex-ctrl-deletefile` | Hàm lấy key từ URL để xóa object tương ứng trên S3. |
| `ex-ctrl-validate` | Hàm validate logic đầu vào (giá, số lượng, ngày, hạng...). |
| `ex-ctrl-calculator`| Hàm tính toán giá thành dựa trên rules nghiệp vụ. |
| `ex-ctrl-buildObj` | Hàm gom data từ `req.body` và kết quả tính toán thành 1 Object chuẩn bị lưu DB. |
| `ex-ctrl-index` | Hàm trả về trang danh sách (có hỗ trợ filter tìm kiếm `q`). |
| `ex-ctrl-detail` | Hàm hiển thị chi tiết 1 đối tượng. |
| `ex-ctrl-deleteSoft` | Hàm xử lý xóa 1 phần mềm (gọi S3 xóa ảnh -> gọi DB xóa item). |
| `ex-ctrl-showAdd` | Render giao diện view thêm mới. |
| `ex-ctrl-add` | Xử lý POST lưu dữ liệu: Validate -> Upload S3 -> Dùng `buildObj` -> Tạo DB. |
| `ex-ctrl-showEdit` | Render giao diện view chỉnh sửa kèm data cũ. |
| `ex-ctrl-edit` | Xử lý POST cập nhật: Xóa ảnh cũ trên S3 -> Upload ảnh mới -> Dùng `buildObj` -> Cập nhật DB. |
| `ex-ctrl-deleteAll` | Quét toàn bộ dữ liệu DB -> Xóa đồng loạt file S3 -> Xóa đồng loạt trong DB. |

---
**💡 Tips:** Nhập chính xác `Prefix` trong file `.js` tương ứng và nhấn `Tab` hoặc `Enter` để VS Code tự động generate code. Di chuyển giữa các biến tự động (như `${1:id}`) bằng phím `Tab`.