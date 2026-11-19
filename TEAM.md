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


## DoanTriHung-2A202603959

### Phần việc phụ trách

Vai **Sản phẩm và kinh doanh**: câu 1.1, 1.5, 1.6 (Phiếu A mục A1, A3, A4, A5) và `config/acceptance_criteria.json`; câu 2.3 (Phiếu B mục B3 bản đồ dữ liệu và ví dụ drift), câu 2.5 (Phiếu B mục B6 pre-mortem lăng kính kinh doanh), câu 2.9 (Phiếu B mục B7.4 và `config/operating_gates.json` mục `business`), quyết định Gate 1 v1 (Phiếu B mục B8); vòng 2 (thẻ S3): câu 3.1 mở lại bản đồ dữ liệu (Phiếu C mục C3.5), câu 3.2 specification (Phiếu C mục C5), cập nhật nhóm 9 checklist (C11), quyết định Gate 1 v2 và 3 dòng bắt buộc (Phiếu C mục C12), hoàn thiện `submission/submission.json`.

### Đóng góp cụ thể

- Thiết lập và chốt Bản tiêu chí chấp nhận (`config/acceptance_criteria.json`): `pass_rate_min = 0.9`, `pass_k_min = 0.85`, 3 ngưỡng an toàn = `0`, `escalation_rate_max = 0.25`, `cost_per_ticket_vnd_max = 8000` (so với làm tay `10.000đ`), `roi_min = 0.2`, `queue_stuck_max = 0`, kèm `stop_condition` và 4 dòng `decision_rule`.
- Lập bản đồ dữ liệu (B3) và dự đoán sớm ví dụ concept drift khi chuyển `REFUND-v3 → REFUND-v4` ngày `2026-12-01` (đúng kịch bản thẻ S3 ở vòng 2); đặt cổng `business` trong `config/operating_gates.json` (`daily_refund_cap_vnd = 2000000`, `cost_budget_per_ticket_vnd = 1500`, `pilot_scope = all 100%`, `roi_min = 0.2`).
- Viết quyết định Gate 1 **v1 = Tiếp tục** (B8) sau khi kiểm 9/9 ngưỡng đều `[ĐẠT ]`, không vượt trần.
- Vòng 2 (thẻ S3): viết specification cho `issue_refund` và `file_carrier_fault` (C5 câu 3.2), viết quyết định Gate 1 **v2 = Tiếp tục** + 3 dòng bắt buộc (C12) khớp bằng chứng ba mốc `base · prepared · after`, cập nhật `submission/submission.json`.
- Ghi chú sử dụng AI: có dùng trợ lý AI hỗ trợ đọc tài liệu lab, rà soát cấu trúc phiếu và đối chiếu số liệu từ `data/world.json` và output report; mọi ngưỡng và quyết định đều được kiểm chứng lại trên report thật.

### Bằng chứng

- Tiêu chí đã ký: commit `eacaf05` (`Sign acceptance criteria`, hash `711216fd3b4b`).
- Vòng 1: `R-base-prepared-20261119-155808-3ea198` (`pass_rate = 1.0`, `ROI = 1.38`, chi phí `4.202đ`/ticket, 9/9 `[ĐẠT ]`).
- Vòng 2 (thẻ S3): `R-S3-grade-20261119-164501-6cb01a` (`PASS-VISIBLE`, `after`: `pass_rate = 1.0`, `pass_k = 1.0`, hoàn sai `0đ`, lỗi hãng oan `0`, `ROI = 1.51`, chi phí `3.980đ`/ticket, `regression ✅`, `monitor ✅`).
- File đóng góp: `config/acceptance_criteria.json`, `config/operating_gates.json` (mục `business`), `templates/form-a-criteria.md`, `templates/form-b-evaluation-gates.md` (B3, B6, B7.4, B8), `templates/form-c-incident.md` (C3.5, C5 câu 3.2, C11 nhóm 9, C12), `submission/submission.json`.

### Exit ticket

- Học được: phải ký tiêu chí chấp nhận và định nghĩa rõ luật quyết định (`decision_rule`) *trước* khi xem số liệu đo; và concept drift khi đổi chính sách kinh doanh (`v3 → v4`) có thể làm đảo chiều hoàn toàn từ lãi (`ROI = 1.38`) thành lỗ (`ROI = -2.59`) nếu không có cổng ghim phiên bản và monitor phát hiện kịp thời.
- Còn chưa chắc: khi chạy pilot thật với lượng đơn cao điểm sau bão và hạn mức tự động giảm xuống `100.000đ` ở `v4`, tỉ lệ chuyển duyệt (`escalation_rate`) thực tế có vượt công suất 1 người trực (`6 ca/giờ`) sớm hơn dự tính trên dữ liệu mock hay không.


## NgoMinhCuong-2A202603954

### Phần việc phụ trách

Vai **Kỹ sư cổng**: câu 1.3 (Phiếu A mục A2, cột Offline metric); vòng 1: câu 2.1, 2.2 (Phiếu B mục B0, B1, B2), câu 2.6, 2.7, 2.8 (Phiếu B mục B7.1–B7.3), code 3 cổng phòng ngừa vòng 1 trong `lab10/guards.py` và chạy `lab10.checkpoint`; vòng 2 (thẻ S3): dò trace sự cố, điền C0, C2 (bảng soát lỗi), C7 (bảng sửa), C8 (chỉ số theo dõi mới), bổ sung cổng trong `lab10/guards.py`, thêm chỉ số `policy_drift_rate` trong `lab10/monitors.py`, chạy kiểm tra không hồi quy và ba mốc `base · prepared · after`.

### Đóng góp cụ thể

- Thiết kế offline metric cho bước `file_carrier_fault` (câu 1.3); chạy đánh giá mốc `base`, so tiêu chí đã ký (`lab10.gate`), dò trace và xếp loại lỗi chìm cho `T-002@55` (B1, B2).
- Code 3 cổng phòng ngừa vòng 1 trong `lab10/guards.py` (`write_gate`): kiểm tra chủ đơn `issue_refund`, đối chiếu quyền lợi hoàn tiền trực tiếp với tracking DB & chính sách hiệu lực (`H.entitlement_vnd`), và chặn ghi lỗi hãng không khớp `H.carrier_at_fault`; thiết kế 2 bước tránh rò rỉ dữ liệu (B7.2) và 2 ticket hiểm `--adhoc` cho behavioral test (B7.3).
- Vòng 2 (thẻ S3): dò trace `S3-02@11`, `S3-04@11`, `S3-42@11`, lập bảng soát 3 lỗi thuộc 2 nguồn khác nhau (C2).
- Bổ sung 3 nhánh sửa trong `lab10/guards.py` (C7): ghim `policy_id` theo `H.effective_policy(policies, ctx.as_of)` + log `guard_policy_drift` trong `pre_guard`; kiểm tra vượt `auto_limit_vnd` thiếu `approval_id` → `escalate` ở `issue_refund`; và chặn ghi lỗi hãng vượt trần `max_auto_strikes_per_carrier_per_day = 2` ở `file_carrier_fault`.
- Viết và đăng ký chỉ số theo dõi mới `policy_drift_rate` trong `lab10/monitors.py` (C8): báo `0.0` trên bộ nền và sáng đèn `1.0` trên thẻ S3.

### Bằng chứng

- Vòng 1: `R-base-before-20261119-154409-daff31` (baseline), `R-base-after-20261119-154724-daff31` (cổng vòng 1, `pass_rate = 1.0`, `pass_k = 1.0`, hoàn sai `0đ`, lỗi hãng oan `0`).
- Vòng 2 (thẻ S3): `R-S3-prepared-20261119-162501-daff31` → `R-S3-after-20261119-162542-563366` → `R-S3-after-20261119-162614-3e7ba4` (`pass_rate = 1.0`, `pass_k = 1.0`, lỗi hãng oan `35 → 15 → 0`, hoàn sai `900.000đ → 0đ`, `policy_drift_rate = 1.0`), kiểm không hồi quy `R-base-after-20261119-162614-3e7ba4` (`5 regression ✅`, `6 monitor ✅`).
- File đóng góp: `lab10/guards.py`, `lab10/monitors.py`, `templates/form-a-criteria.md` (câu 1.3), `templates/form-b-evaluation-gates.md` (B0, B1, B2, B7.1–B7.3), `templates/form-c-incident.md` (C0, C2, C7, C8).

### Exit ticket

- Học được: đặt cổng ngoài model (`pre_guard` ghim chính sách theo ngày và `write_gate` đối chiếu nguồn sự thật DB + `ops_limits`) ngăn lỗi chắc chắn hơn nhiều so với sửa prompt, đồng thời monitor không cần nhãn (`policy_drift_rate`) giúp phát hiện sớm drift trong production.
- Còn chưa chắc: với các ca chạm trần `max_auto_strikes_per_carrier_per_day`, việc trả về `deny` giúp chặn phạt oan nhưng chưa tự đẩy vào hàng chờ đối soát; cần theo dõi thêm trên bài kiểm tra ẩn xem có trường hợp biên nào nên dùng `escalate` thay vì `deny` hay không.
