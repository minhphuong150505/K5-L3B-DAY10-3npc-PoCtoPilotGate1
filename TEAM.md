# Team

## Thông tin nhóm

- Tên nhóm (`TenNhom`, không dấu, không khoảng trắng): 3npc
- Lớp: `L3B`
- Repo của bàn: `K5-L3B-DAY10-3npc-PoCtoPilotGate1`
- Thẻ sự cố đã bốc (S1–S8):

## Thành viên

Họ tên đầy đủ và MSSV của **mọi** thành viên; bàn 3 người thì để trống dòng 4. Vai: Kỹ sư cổng · Sản phẩm và kinh doanh · Vận hành và pháp lý (README mục 3, phút 0–15).

| STT | Họ và tên | MSSV | Vai | Trưởng nhóm |
| --: | --------- | ---- | --- | :---------: |
|   1 | Nguyễn Minh Phương | 2A202603997 | Vận hành và pháp lý | x |
|   2 | Đoàn Trí Hùng | 2A202603959 | Sản phẩm và kinh doanh |             |
|   3 | Ngô Minh Cương | 2A202603954 | Kỹ sư cổng |             |
|   4 |           |      |     |             |

Ghi `members` trong `submission/submission.json` theo dạng `"HoVaTen-MSSV"`, khớp bảng trên.

## Cá nhân

Mỗi thành viên tự viết một mục bên dưới (chép mẫu, đổi tiêu đề thành họ tên không dấu và MSSV, ví dụ `## NguyenVanAn-20241234`).

## HoVaTen-MSSV

### Phần việc phụ trách

Vai trong bàn; câu nào của đề, mục nào của phiếu A/B/C, file nào (`lab10/guards.py`, `config/operating_gates.json`, …).

### Đóng góp cụ thể

...

### Bằng chứng

Mã commit, mã lần chạy (`runs/<mã>`), dòng trong phiếu.

### Exit ticket

Một điều học được, một điều còn chưa chắc.

## NguyenMinhPhuong-2A202603997

### Phần việc phụ trách

Vai **Vận hành và pháp lý**: câu 1.2 (Phiếu A mục A1), câu 1.4 (Phiếu A mục A2, cột Telemetry production), câu 2.4 (Phiếu B mục B4 HAZOP vòng 1, B5 checklist 9 nhóm), câu 2.10 (Phiếu B mục B7.5 runbook phần 1–3, B7.6 giờ cao điểm), `config/operating_gates.json` mục `operations` và `legal`; vòng 2: Phiếu C mục C11 (checklist, runbook phần 4–5); `submission/submission.json`.

### Đóng góp cụ thể

- Mục tiêu nhìn từ chị Oanh (kế toán đối soát) và chị Hạnh (trưởng ca CSKH); telemetry production đếm lệnh ghi ra hãng không khớp tracking hoặc lộ dữ liệu người nhận, cửa sổ 24 giờ / 7 ngày, ĐỎ khi ≥ 1.
- HAZOP vòng 1 trên `file_carrier_fault` (5 dòng kỹ thuật, 4 dòng ngoài kỹ thuật: người duyệt, dữ liệu gửi bên thứ ba, hãng nhỏ, ngân sách).
- Đặt cổng con người/vận hành/pháp lý: PIC `NV-TUNG`, người duyệt `NV-HANH`, 1 người trực, 6 ca/giờ, chờ tối đa 45 phút, 6 điều kiện dừng, kênh `#logix-refund-pilot-alerts`; chặn `recipient_contact`, `customer_note` gửi hãng; bắt buộc có nguyên nhân trong tracking mới ghi lỗi hãng.
- Viết runbook 1–3 và mục Giờ cao điểm khớp các con số trên.

### Bằng chứng

_(mã commit, mã lần chạy `base · after` có lộ PII = 0, lỗi hãng oan = 0)_

### Exit ticket

_(một điều học được, một điều còn chưa chắc)_
