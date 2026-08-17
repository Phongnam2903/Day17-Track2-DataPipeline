# Báo cáo LAB 17 — Data Pipeline Engineering

**Họ tên:** Nguyễn Nam Phong  **Lớp:** AICB-P2T2  **Ngày:** 17/08/2026

---

## 0 · Kết quả `make verify`

<details>
<summary>Dán nguyên output ba lần chạy vào đây</summary>

```
PS D:\CODE\AITHUCCHIEN\Track_2\Day17-Track2-DataPipeline> make verify

  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  LAB 17 · make verify
  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  run 1/3 … 33.1s
  run 2/3 … 33.2s
  run 3/3 … 33.1s

  BẢNG                  ỔN ĐỊNH          SỐ HÀNG     KỲ VỌNG   GHI CHÚ
  ──────────────────────────────────────────────────────────────────────────
  gold_training_set     ✓ ok              12,480      12,480   ✓
  gold_feature_daily    ✓ ok               9,100       9,100   ✓
  gold_doc_chunks       ✓ ok              31,200      31,200   ✓
  quarantine_tickets    ✓ ok                 312         312   ✓

  CHECKSUM từng lượt
  ──────────────────────────────────────────────────────────────────────────
  gold_training_set     8dd7c98653    8dd7c98653    8dd7c98653   ✓
  gold_feature_daily    3db448685c    3db448685c    3db448685c   ✓
  gold_doc_chunks       92d8e50131    92d8e50131    92d8e50131   ✓
  quarantine_tickets    ebb89036fb    ebb89036fb    ebb89036fb   ✓

  KIỂM TRA KHÁC
  ──────────────────────────────────────────────────────────────────────────
  dbt test                                    ✓ 11/11 pass
  silver_tickets.priority ∈ 1..4, không NULL  ✓ sạch
  quarantine_tickets đúng số bản ghi lỗi      ✓ 312 / 312
  gold_training_set: 1 hàng / 1 ticket        ✓ không lặp
  bài mở rộng (EXTRA.md)                      — chưa chạy `make seed-extra`
  DAG: catchup / max_active_runs              ✓ False / 1

  TỔNG KẾT
  ──────────────────────────────────────────────────────────────────────────
  ✓  1 · gold_training_set idempotent & đúng số hàng
  ✓  2 · gold_feature_daily đủ hàng (dữ liệu về muộn)
  ✓  3 · contract + quarantine + dbt test
  ✓  4 · gold_doc_chunks vẫn ổn định (đối chứng)
  ──────────────────────────────────────────────────────────────────────────
  4/4 tiêu chí đạt

PS D:\CODE\AITHUCCHIEN\Track_2\Day17-Track2-DataPipeline> make verify

  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  LAB 17 · make verify
  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  run 1/3 … 33.5s
  run 2/3 … 33.5s
  run 3/3 … 32.4s

  BẢNG                  ỔN ĐỊNH          SỐ HÀNG     KỲ VỌNG   GHI CHÚ
  ──────────────────────────────────────────────────────────────────────────
  gold_training_set     ✓ ok              12,480      12,480   ✓
  gold_feature_daily    ✓ ok               9,100       9,100   ✓
  gold_doc_chunks       ✓ ok              31,200      31,200   ✓
  quarantine_tickets    ✓ ok                 312         312   ✓

  CHECKSUM từng lượt
  ──────────────────────────────────────────────────────────────────────────
  gold_training_set     8dd7c98653    8dd7c98653    8dd7c98653   ✓
  gold_feature_daily    3db448685c    3db448685c    3db448685c   ✓
  gold_doc_chunks       92d8e50131    92d8e50131    92d8e50131   ✓
  quarantine_tickets    ebb89036fb    ebb89036fb    ebb89036fb   ✓

  KIỂM TRA KHÁC
  ──────────────────────────────────────────────────────────────────────────
  dbt test                                    ✓ 11/11 pass
  silver_tickets.priority ∈ 1..4, không NULL  ✓ sạch
  quarantine_tickets đúng số bản ghi lỗi      ✓ 312 / 312
  gold_training_set: 1 hàng / 1 ticket        ✓ không lặp
  bài mở rộng (EXTRA.md)                      — chưa chạy `make seed-extra`
  DAG: catchup / max_active_runs              ✓ False / 1

  TỔNG KẾT
  ──────────────────────────────────────────────────────────────────────────
  ✓  1 · gold_training_set idempotent & đúng số hàng
  ✓  2 · gold_feature_daily đủ hàng (dữ liệu về muộn)
  ✓  3 · contract + quarantine + dbt test
  ✓  4 · gold_doc_chunks vẫn ổn định (đối chứng)
  ──────────────────────────────────────────────────────────────────────────
  4/4 tiêu chí đạt

PS D:\CODE\AITHUCCHIEN\Track_2\Day17-Track2-DataPipeline> make verify

  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  LAB 17 · make verify
  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  run 1/3 … 32.1s
  run 2/3 … 33.1s
  run 3/3 … 34.3s

  BẢNG                  ỔN ĐỊNH          SỐ HÀNG     KỲ VỌNG   GHI CHÚ
  ──────────────────────────────────────────────────────────────────────────
  gold_training_set     ✓ ok              12,480      12,480   ✓
  gold_feature_daily    ✓ ok               9,100       9,100   ✓
  gold_doc_chunks       ✓ ok              31,200      31,200   ✓
  quarantine_tickets    ✓ ok                 312         312   ✓

  CHECKSUM từng lượt
  ──────────────────────────────────────────────────────────────────────────
  gold_training_set     8dd7c98653    8dd7c98653    8dd7c98653   ✓
  gold_feature_daily    3db448685c    3db448685c    3db448685c   ✓
  gold_doc_chunks       92d8e50131    92d8e50131    92d8e50131   ✓
  quarantine_tickets    ebb89036fb    ebb89036fb    ebb89036fb   ✓

  KIỂM TRA KHÁC
  ──────────────────────────────────────────────────────────────────────────
  dbt test                                    ✓ 11/11 pass
  silver_tickets.priority ∈ 1..4, không NULL  ✓ sạch
  quarantine_tickets đúng số bản ghi lỗi      ✓ 312 / 312
  gold_training_set: 1 hàng / 1 ticket        ✓ không lặp
  bài mở rộng (EXTRA.md)                      — chưa chạy `make seed-extra`
  DAG: catchup / max_active_runs              ✓ False / 1

  TỔNG KẾT
  ──────────────────────────────────────────────────────────────────────────
  ✓  1 · gold_training_set idempotent & đúng số hàng
  ✓  2 · gold_feature_daily đủ hàng (dữ liệu về muộn)
  ✓  3 · contract + quarantine + dbt test
  ✓  4 · gold_doc_chunks vẫn ổn định (đối chứng)
  ──────────────────────────────────────────────────────────────────────────
  4/4 tiêu chí đạt
```

</details>

Tổng kết: **4/4 tiêu chí đạt**

---

## 1 · Kích thước bảng training tăng sau mỗi lần chạy

|                             |                                                                                                                                                                                                                                                                                                                                                                                                  |
| --------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Triệu chứng**     | Sau ba lượt chạy,`gold_training_set` tăng lên 38.750 hàng thay vì 12.480; cả 12.480 `ticket_id` đều xuất hiện lặp lại và checksum thay đổi giữa các lượt.                                                                                                                                                                                                               |
| **Nguyên nhân**     | Model incremental không khai báo`unique_key`, nên dbt sinh phép ghi thêm. Khi Airflow retry hoặc người trực Clear Task, cùng partition được xử lý lại và các ticket đã tồn tại bị `INSERT` thêm thay vì cập nhật. `catchup=True` và không giới hạn số DAG run đồng thời làm tăng khả năng kích hoạt lỗi, nhưng không phải nguyên nhân gốc. |
| **Cách khắc phục** | Trong`dbt/models/gold/gold_training_set.sql`, khai báo `unique_key='ticket_id'` và `incremental_strategy='merge'`; giữ nguyên bộ lọc `run_date`. Trong `dags/ai_training_pipeline.py`, đặt `catchup=False` và `max_active_runs=1`.                                                                                                                                        |
| **Bằng chứng**      | Trước: 38.750 hàng, 12.480 ticket bị lặp · sau: 12.480 hàng, không lặp · checksum ba lượt đều là`8dd7c98653…`.                                                                                                                                                                                                                                                                 |

---

## 2 · Bảng đặc trưng theo ngày thiếu hàng ở các ngày quá khứ

|                                     |                                                                                                                                                                                                              |
| ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Triệu chứng**             | `gold_feature_daily` chỉ có 8.645/9.100 hàng kỳ vọng; dữ liệu về muộn hơn một ngày chiếm 5,05%.                                                                                               |
| **P99 độ trễ đo được** | **2,73 ngày**                                                                                                                                                                                        |
| **Lookback đã chọn**       | 3 ngày — làm tròn lên từ P99 = 2,7258 ngày để bao phủ 99% độ trễ quan sát được.                                                                                                             |
| **Nguyên nhân**             | Watermark dựa trên`max(event_date)` của bảng đích chỉ nhận ngày mới hơn. Event xảy ra ở ngày cũ nhưng đến warehouse muộn bị nằm sau watermark và không bao giờ được tổng hợp. |
| **Cách khắc phục**         | Trong`dbt/models/gold/gold_feature_daily.sql`, dùng composite key `['event_date', 'customer_id']`, chiến lược `merge` và tính lại lookback 3 ngày.                                             |
| **Bằng chứng**              | Trước: 8.645 hàng · sau: 9.100 hàng · checksum ba lượt`3db448685c…` giống nhau.                                                                                                                  |

Vì sao chọn P99 làm căn cứ thay vì `max`? Chi phí của mỗi lựa chọn là gì?

> Chọn P99 vì đây là ngưỡng ổn định bao phủ 99% độ trễ mà không để một ngoại lệ
> cực đoan làm cửa sổ tăng vô hạn; làm tròn 2,7258 lên 3 ngày cũng bao phủ mức
> `max` 2,9447 ngày hiện tại. Mỗi ngày lookback tăng thêm làm tăng lượng dữ liệu
> phải quét, tổng hợp và merge ở mọi lượt chạy; phần đuôi ngoài cửa sổ cần được
> giám sát và xử lý bằng backfill khi xuất hiện.

---

## 3 · Kiểu dữ liệu cột priority thay đổi giữa chu kỳ

|                                                                         |                                                                                                                                                                                                                                                                      |
| ----------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Triệu chứng**                                                 | Sau khi nguồn đổi từ nhãn số sang nhãn chữ, Silver có 6.606 giá trị`priority` NULL hoặc ngoài miền 1..4 nhưng pipeline không cảnh báo.                                                                                                           |
| **Nguyên nhân**                                                 | Nguồn đã tiến hóa schema từ nhãn số sang nhãn chữ nhưng transform vẫn chỉ`try_cast`. Cách xử lý này vừa loại nhầm nhãn chữ hợp lệ, vừa chấp nhận số ngoài miền; contract lại đang tắt nên pipeline không phát hiện sai lệch. |
| **Ba nhóm giá trị `priority` và cách xử lý từng nhóm** | `'1'`, `'2'`, `'3'`, `'4'` → số tương ứng; `urgent`, `high`, `medium`, `low` → 1, 2, 3, 4; `0`, `5`, `-1`, `P1`, `P2`, `unknown`, chuỗi rỗng và NULL → quarantine.                                                             |
| **Cách khắc phục**                                             | Dùng một macro`CASE` chung; Silver lọc bản ghi lỗi trước khi `row_number`; quarantine giữ từng bản ghi CDC lỗi; bật contract và test `not_null`/`accepted_values`.                                                                              |
| **Bằng chứng**                                                  | `quarantine_tickets` = 312 hàng · `dbt test` 11/11 pass · Silver đủ 12.480 ticket và `priority` sạch                                                                                                                                                    |

Câu hỏi thiết kế: nên chặn ở tầng Bronze hay Silver? Vì sao **không** để
pipeline dừng khi gặp bản ghi lỗi?

> Không chặn ở Bronze: tầng này nên lưu nguyên trạng dữ liệu nguồn để có thể
> điều tra và phát lại khi schema thay đổi. Việc chuẩn hóa và áp contract đầu ra
> thuộc Silver. Lỗi chỉ nằm trên một số bản ghi nên chúng được tách vào
> quarantine để người trực xử lý; dừng cả pipeline sẽ giữ lại cả dữ liệu hợp lệ
> của event và transcript mà không cải thiện khả năng phục hồi bản ghi lỗi.

---

## 4 · *(mở rộng, không bắt buộc)* Bài trong EXTRA.md

|                             |                                                                                                                                 |
| --------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| **Bài đã làm**    | Bài A — tối ưu query dashboard chậm. |
| **Nguyên nhân**     | Dataset gồm 5.000 file Parquet rất nhỏ, không partition nên DuckDB phải mở và quét toàn bộ file. Điều kiện `strftime(event_time, ...)` bọc cột trong hàm nên không thể tận dụng partition pruning hoặc min/max statistics. |
| **Cách khắc phục** | Trong `tools/compact.py`, compact dữ liệu thành 14 partition theo `event_date`, sắp theo `customer_name, event_time` và đặt row group 2.048 hàng. Trong `queries/dashboard.sql`, đọc dataset mới với `hive_partitioning=true` và lọc trực tiếp bằng `event_date = DATE '2026-08-09'`. |
| **Bằng chứng**      | `rows scanned`: 5.000.000 → 9.324, giảm **536,3×** · file: 5.000 → 14 · số hàng: 130.683 → 130.683 · result hash giữ nguyên `4379e4c5d9f3` · `make verify` vẫn đạt 4/4. |

---

## 5 · Tổng kết

| Nhiệm vụ | Khi tiếp nhận một hệ thống chưa quen, tôi sẽ kiểm tra điều này trước tiên                                                     |
| ---------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| 1          | Xác định grain, khóa tự nhiên, chiến lược materialization và hành vi khi scheduler retry hoặc chạy đồng thời.                |
| 2          | So sánh`event_time` với `_ingested_at`, đo phân bố độ trễ và kiểm tra watermark có bỏ sót dữ liệu đến muộn hay không. |
| 3          | Kiểm tra phân bố dữ liệu thô, lịch sử thay đổi schema, trạng thái data contract và luồng xử lý bản ghi không hợp lệ.     |
