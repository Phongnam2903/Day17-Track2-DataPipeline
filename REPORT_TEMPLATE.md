  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  LAB 17 · make verify
  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  run 1/1 … 32.5s

  BẢNG                  ỔN ĐỊNH          SỐ HÀNG     KỲ VỌNG   GHI CHÚ
  ──────────────────────────────────────────────────────────────────────────
  gold_training_set     ✓ ok              12,480      12,480   ✓
  gold_feature_daily    ✓ ok               9,100       9,100   ✓
  gold_doc_chunks       ✓ ok              31,200      31,200   ✓
  quarantine_tickets    ✓ ok                   0         312   ✗ thiếu 312 hàng

  KIỂM TRA KHÁC
  ──────────────────────────────────────────────────────────────────────────
  dbt test                                    ✓ 9/9 pass
  silver_tickets.priority ∈ 1..4, không NULL  ✗ 6,606 hàng sai
  quarantine_tickets đúng số bản ghi lỗi      ✗ 0 / 312
  gold_training_set: 1 hàng / 1 ticket        ✓ không lặp
  bài mở rộng (EXTRA.md)                      — chưa chạy `make seed-extra`
  DAG: catchup / max_active_runs              ✓ False / 1

  TỔNG KẾT
  ──────────────────────────────────────────────────────────────────────────
  ✓  1 · gold_training_set idempotent & đúng số hàng
  ✓  2 · gold_feature_daily đủ hàng (dữ liệu về muộn)
  ✗  3 · contract + quarantine + dbt test
  ✓  4 · gold_doc_chunks vẫn ổn định (đối chứng)
  ──────────────────────────────────────────────────────────────────────────
  3/4 tiêu chí đạt

# Báo cáo LAB 17 — Data Pipeline Engineering

**Họ tên:** …  **Lớp:** AICB-P2T2  **Ngày:** …

---

## 0 · Kết quả `make verify`

<details>
<summary>Dán nguyên output ba lần chạy vào đây</summary>

```
  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  LAB 17 · make verify
  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  run 1/1 … 34.5s

  BẢNG                  ỔN ĐỊNH          SỐ HÀNG     KỲ VỌNG   GHI CHÚ
  ──────────────────────────────────────────────────────────────────────────
  gold_training_set     ✓ ok              12,480      12,480   ✓
  gold_feature_daily    ✓ ok               8,645       9,100   ✗ thiếu 455 hàng
  gold_doc_chunks       ✓ ok              31,200      31,200   ✓
  quarantine_tickets    ✓ ok                   0         312   ✗ thiếu 312 hàng

  KIỂM TRA KHÁC
  ──────────────────────────────────────────────────────────────────────────
  dbt test                                    ✓ 9/9 pass
  silver_tickets.priority ∈ 1..4, không NULL  ✗ 6,606 hàng sai
  quarantine_tickets đúng số bản ghi lỗi      ✗ 0 / 312
  gold_training_set: 1 hàng / 1 ticket        ✓ không lặp
  bài mở rộng (EXTRA.md)                      — chưa chạy `make seed-extra`
  DAG: catchup / max_active_runs              ✓ False / 1

  TỔNG KẾT
  ──────────────────────────────────────────────────────────────────────────
  ✓  1 · gold_training_set idempotent & đúng số hàng
  ✗  2 · gold_feature_daily đủ hàng (dữ liệu về muộn)
  ✗  3 · contract + quarantine + dbt test
  ✓  4 · gold_doc_chunks vẫn ổn định (đối chứng)
  ──────────────────────────────────────────────────────────────────────────
  2/4 tiêu chí đạt

  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  LAB 17 · make verify
  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  run 1/1 … 32.5s

  BẢNG                  ỔN ĐỊNH          SỐ HÀNG     KỲ VỌNG   GHI CHÚ
  ──────────────────────────────────────────────────────────────────────────
  gold_training_set     ✓ ok              12,480      12,480   ✓
  gold_feature_daily    ✓ ok               9,100       9,100   ✓
  gold_doc_chunks       ✓ ok              31,200      31,200   ✓
  quarantine_tickets    ✓ ok                   0         312   ✗ thiếu 312 hàng

  KIỂM TRA KHÁC
  ──────────────────────────────────────────────────────────────────────────
  dbt test                                    ✓ 9/9 pass
  silver_tickets.priority ∈ 1..4, không NULL  ✗ 6,606 hàng sai
  quarantine_tickets đúng số bản ghi lỗi      ✗ 0 / 312
  gold_training_set: 1 hàng / 1 ticket        ✓ không lặp
  bài mở rộng (EXTRA.md)                      — chưa chạy `make seed-extra`
  DAG: catchup / max_active_runs              ✓ False / 1

  TỔNG KẾT
  ──────────────────────────────────────────────────────────────────────────
  ✓  1 · gold_training_set idempotent & đúng số hàng
  ✓  2 · gold_feature_daily đủ hàng (dữ liệu về muộn)
  ✗  3 · contract + quarantine + dbt test
  ✓  4 · gold_doc_chunks vẫn ổn định (đối chứng)
  ──────────────────────────────────────────────────────────────────────────
  3/4 tiêu chí đạt
  
```

</details>

Tổng kết: **… / 4 tiêu chí đạt**

---

## 1 · Kích thước bảng training tăng sau mỗi lần chạy

|                             |                                                             |
| --------------------------- | ----------------------------------------------------------- |
| **Triệu chứng**     |                                                             |
| **Nguyên nhân**     |                                                             |
| **Cách khắc phục** | *(file + thay đổi)*                                     |
| **Bằng chứng**      | trước: … hàng · sau: … hàng · checksum 3 lượt: … |

---

## 2 · Bảng đặc trưng theo ngày thiếu hàng ở các ngày quá khứ

|                                     |                                                                                                                                                                                                              |
| ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Triệu chứng**             | `gold_feature_daily` chỉ có 8.645/9.100 hàng kỳ vọng; dữ liệu về muộn hơn một ngày chiếm 5,05%.                                                                                               |
| **P99 độ trễ đo được** | **2,73 ngày** *(bắt buộc)*                                                                                                                                                                        |
| **Lookback đã chọn**       | 3 ngày — làm tròn lên từ P99 = 2,7258 ngày để bao phủ 99% độ trễ quan sát được.                                                                                                             |
| **Nguyên nhân**             | Watermark dựa trên`max(event_date)` của bảng đích chỉ nhận ngày mới hơn. Event xảy ra ở ngày cũ nhưng đến warehouse muộn bị nằm sau watermark và không bao giờ được tổng hợp. |
| **Cách khắc phục**         | Trong`dbt/models/gold/gold_feature_daily.sql`, dùng composite key `['event_date', 'customer_id']`, chiến lược `merge` và tính lại lookback 3 ngày.                                             |
| **Bằng chứng**              | trước: 8.645 hàng · sau: 9.100 hàng · checksum 3 lượt:`3db448685c…` giống nhau                                                                                                                   |

Vì sao chọn P99 làm căn cứ thay vì `max`? Chi phí của mỗi lựa chọn là gì?

> Chọn P99 vì đây là ngưỡng ổn định bao phủ 99% độ trễ mà không để một ngoại lệ
> cực đoan làm cửa sổ tăng vô hạn; làm tròn 2,7258 lên 3 ngày cũng bao phủ mức
> `max` 2,9447 ngày hiện tại. Mỗi ngày lookback tăng thêm làm tăng lượng dữ liệu
> phải quét, tổng hợp và merge ở mọi lượt chạy; phần đuôi ngoài cửa sổ cần được
> giám sát và xử lý bằng backfill khi xuất hiện.

---

## 3 · Kiểu dữ liệu cột priority thay đổi giữa chu kỳ

|                                                                         |                                                           |
| ----------------------------------------------------------------------- | --------------------------------------------------------- |
| **Triệu chứng**                                                 |                                                           |
| **Nguyên nhân**                                                 |                                                           |
| **Ba nhóm giá trị `priority` và cách xử lý từng nhóm** |                                                           |
| **Cách khắc phục**                                             |                                                           |
| **Bằng chứng**                                                  | `quarantine_tickets` = … hàng · `dbt test` … pass |

Câu hỏi thiết kế: nên chặn ở tầng Bronze hay Silver? Vì sao **không** để
pipeline dừng khi gặp bản ghi lỗi?

> …

---

## 4 · *(mở rộng, không bắt buộc)* Bài trong EXTRA.md

|                             |                     |
| --------------------------- | ------------------- |
| **Bài đã làm**    | A / B / không làm |
| **Nguyên nhân**     |                     |
| **Cách khắc phục** |                     |
| **Bằng chứng**      |                     |

---

## 5 · Tổng kết

| Nhiệm vụ | Khi tiếp nhận một hệ thống chưa quen, tôi sẽ kiểm tra điều này trước tiên |
| ---------- | ---------------------------------------------------------------------------------------- |
| 1          |                                                                                          |
| 2          |                                                                                          |
| 3          |                                                                                          |
