# Team

## Thông tin nhóm

- Tên nhóm (`TenNhom`, không dấu, không khoảng trắng): 3npc
- Lớp: `L3B`
- Repo của bàn: `K5-L3B-DAY10-3npc-PoCtoPilotGate1`
- Thẻ sự cố đã bốc (S1–S8): S3

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

Vai **Vận hành và pháp lý**: câu 1.2 (Phiếu A mục A1), câu 1.4 (Phiếu A mục A2, cột Telemetry production), câu 2.4 (Phiếu B mục B4 HAZOP vòng 1, B5 checklist 9 nhóm), câu 2.10 (Phiếu B mục B7.5 runbook phần 1–3, B7.6 giờ cao điểm), `config/operating_gates.json` mục `operations` và `legal`; vòng 2 (thẻ S3): câu 3.1 phần riêng của thẻ (Phiếu C mục C1 đối chiếu pre-mortem, C3.5 bản đồ dữ liệu `policies` / `delay_cause`), HAZOP của thẻ (C4), câu 3.3 (C5 giả định môi trường), fault tree trước/sau (C6, C9), câu 3.7 (C10 risk register, C11 checklist và runbook phần 4–5), `operations.stop_conditions` vòng 2, `submission/submission.json` và gom bài nộp.

### Đóng góp cụ thể

- Mục tiêu nhìn từ chị Oanh (kế toán đối soát) và chị Hạnh (trưởng ca CSKH); telemetry production đếm lệnh ghi ra hãng không khớp tracking hoặc lộ dữ liệu người nhận, cửa sổ 24 giờ / 7 ngày, ĐỎ khi ≥ 1.
- HAZOP vòng 1 trên `file_carrier_fault` (5 dòng kỹ thuật, 4 dòng ngoài kỹ thuật: người duyệt, dữ liệu gửi bên thứ ba, hãng nhỏ, ngân sách).
- Đặt cổng con người/vận hành/pháp lý: PIC `NV-TUNG`, người duyệt `NV-HANH`, 1 người trực, 6 ca/giờ, chờ tối đa 45 phút, 6 điều kiện dừng, kênh `#logix-refund-pilot-alerts`; chặn `recipient_contact`, `customer_note` gửi hãng; bắt buộc có nguyên nhân trong tracking mới ghi lỗi hãng.
- Viết runbook 1–3 và mục Giờ cao điểm khớp các con số trên.
- Vòng 2 (thẻ S3): đối chiếu pre-mortem (sự cố có ở dòng 1 và 5 của B6 nhưng dòng 5 chỉ vào Risk register, không thành cổng) và thêm 4 lý do còn thiếu; mở lại bản đồ dữ liệu: `effective_from/to` là nguồn sự thật, `index_active` là bản sao cũ, `delay_cause = null` bị agent mặc định thành `CARRIER`.
- HAZOP của thẻ trên `file_carrier_fault` (4 dòng, có một nhánh INVALID chưa thấy trên trace: bảng `policies` thiếu phụ lục mới); fault tree trước/sau với hai nhánh còn hở; 2 dòng Risk register (drift chính sách, lỗi hãng bị chặn không vào hàng chờ).
- Thêm điều kiện dừng `policy_drift_rate > 0` và sửa điều kiện trần 2 lỗi/hãng/ngày cho khớp cổng code; runbook 4 (báo MKD, huỷ lỗi oan trong 24 giờ) và runbook 5 (tải gấp 3, LLM lỗi 15 phút, người duyệt không tin).
- Phát hiện và sửa lỗi bản chốt vòng 1 bị báo "ĐÃ BỊ SỬA": file chốt được tạo trên máy Windows (CRLF) nhưng git lưu thành LF, hash lệch `round1.lock`; thêm `.gitattributes` giữ nguyên byte, mốc prepared lại "còn nguyên".

### Bằng chứng

- Thẻ S3: base `R-S3-before-20261119-162501-daff31` · prepared `R-S3-prepared-20261119-162501-daff31` · after `R-S3-after-20261119-162614-3e7ba4` (lỗi hãng oan `35 → 15 → 0`, lộ PII `0` cả ba mốc, hoàn sai `900.000đ → 0đ`).
- Kiểm lại sau khi đổi `stop_conditions`: `R-S3-after-20261119-164502-faaf71` (pass_k 1.0), `R-base-after-20261119-164502-faaf71` (pass_k 1.0), grade `R-S3-grade-20261119-164507-faaf71` (prepared "đã chốt `e2e62e64`, còn nguyên").
- Phiếu C mục C1, C3.5, C4, C5 (câu 3.3), C6, C9, C10, C11; `config/operating_gates.json` mục `operations`; nhánh `ops-legal-round2`.

### Exit ticket

- Học được: một cổng viết bằng chữ trong runbook (trần 2 lỗi/hãng/ngày) không chặn được gì nếu không thành code hoặc con số máy đọc được; và trường trống (`delay_cause = null`) luôn nghiêng về phía một ai đó chịu thiệt, phải chọn rõ phía nào.
- Còn chưa chắc: khi bảng `policies` tự nó thiếu phụ lục mới thì cả cổng lẫn `policy_drift_rate` đều xanh; quy trình "người ký phụ lục báo trước 3 ngày" có thật sự được tuân thủ ngoài thực tế không.
