
# Yêu cầu đầu ra


## 1/ Cấu trúc Folder

```
GreenTech-SmartFarm/
├── sensors/    ← Dev: code cảm biến, làm trên Local rồi đồng bộ lên Cloud (Hybrid)
├── reports/    ← Trưởng dự án tải lên; nhà đầu tư chỉ xem
├── specs/      ← tài liệu thiết bị; đối tác chỉ bình luận
└── secrets/    ← chứa .env (mật khẩu cảm biến); không chia sẻ ra ngoài
```

## 2/ Cấu trúc Channel

| Channel | Thành viên | Mục đích |
|---|---|---|
| `#dev-team` | Trưởng dự án, Dev | Trao đổi code hằng ngày |
| `#sensor-bugs` | Trưởng dự án, Dev | Thảo luận lỗi cảm biến → chuyển thành Task có Deadline |
| `#partner-devices` | Trưởng dự án, Dev lead, Đối tác | Góp ý về thiết bị |

Nhà đầu tư không tham gia Channel nào.

**Quy tắc chuyển lỗi thành Task:** Task đặt tên `[Sensor-ID] mô tả lỗi`, có người phụ trách và Deadline. Deadline theo mức độ (đề xuất): Nghiêm trọng 24 giờ, Cao 3 ngày, Thường 7 ngày.

## 3/ Quy định phân quyền

**Chú thích:** M = Owner/Manager (toàn quyền) · E = Edit · C = Comment · V = View · – = không truy cập

| Vai trò | `sensors/` | `reports/` | `specs/` | `secrets/` (`.env`) |
|---|---|---|---|---|
| Trưởng dự án | M | M | M | M |
| Dev lead | E | V | E | V |
| Dev | E | V | E | – |
| Nhà đầu tư | – | **V** | – | – |
| Đối tác thiết bị | – | – | **C** | – |

**Quy định:**
1. Chia sẻ theo từng tài khoản. Không dùng link "ai có link cũng xem".
2. Chỉ Trưởng dự án được xóa vĩnh viễn và chia sẻ ra ngoài; Editor không được chia sẻ thêm.
3. `.env` chỉ nằm trong `secrets/`, ghi vào `.gitignore`; repo chỉ giữ `.env.example` không có mật khẩu thật.
4. Kiểm tra định kỳ: xem thử bằng tài khoản nhà đầu tư và đối tác, phải không thấy `secrets/`.
5. **Transfer Ownership** khi bài tập nhóm kết thúc:
   - Chốt bản cuối và sao lưu Local + Cloud.
   - Chuyển quyền Owner folder gốc cho người nhận đã xác nhận.
   - Đổi mật khẩu trong `.env`.
   - Gỡ quyền các thành viên không còn cần thiết.

## 4/ Kiểm thử: lỡ xóa sạch folder `sensors`

- Trash: Vào Trash → tìm sensors → Restore. Cả folder quay lại trong một thao tác.
- Version history: Sau khi folder đã về, nếu nội dung file nào còn sai thì mở file đó → Version history → chọn bản cũ đúng → Restor