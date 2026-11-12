# Báo cáo thực hành Day 3 — 2A202604049 Nguyễn Đức Anh

**Trạng thái:** Đã kiểm tra cấu trúc các ZIP trong `submissions/`: ba tier và `cp1_holes`, `cp2_slice`, `cp3_thin` đều đạt hợp đồng ảnh/class/format. Kiểm tra cấu trúc không xác nhận mask đúng; các mục trải nghiệm cá nhân dưới đây chỉ ghi điều có thể xác nhận, không suy đoán. Không tự điền điểm hoặc đưa ground truth lên fork.

- Mã học viên theo lớp: **2A202604049**
- Ngày / CVAT local: **11/11/2026 / CVAT local**
- Công cụ đã dùng: **CVAT**

Chỉ ghi công cụ thật sự đã dùng; không có SAM vẫn làm bài bình thường.

## 1. Bài đã nộp

Ghi tên ZIP đúng như file trong `submissions/` và số ảnh đã vẽ, Save. Chưa làm hoặc export lỗi thì ghi `chưa có`, không tạo ZIP rỗng. Cột điểm là điểm tối đa của task, **không phải điểm tự chấm**.

| Task | File ZIP đúng tên | Hoàn thành mấy ảnh | Điểm tối đa (coach chấm sau) |
| --- | --- | ---: | ---: |
| easy_semantic | `easy_semantic.zip` | 3 / 3 | 20 |
| medium_instance | `medium_instance.zip` | 3 / 3 | 32 |
| hard_panoptic | `hard_panoptic.zip` | 2 / 2 | 30 |
| cp1_holes | `cp1_holes.zip` | 1 / 1 | 3 |
| cp2_slice | `cp2_slice.zip` | 1 / 1 | 3 |
| cp5_occlusion | chưa làm, chưa có ZIP | 0 / 1 | 3 |
| cp3_thin | `cp3_thin.zip` | 1 / 1 | 3 |
| cp4_curb | chưa làm, chưa có ZIP | 0 / 1 | 3 |
| cp6_coverage | chưa làm, chưa có ZIP | 0 / 1 | 3 |
| **Tổng tối đa** | | | **100** |

Nếu export lỗi, ghi task, dữ liệu đã Save đến đâu và lỗi đã báo coach.

Đã kiểm tra ba checkpoint ZIP: `cp1_holes.zip` có 1 ảnh và 6 annotation RLE; `cp2_slice.zip` có 1 ảnh và 10 annotation RLE; `cp3_thin.zip` có 1 mask và labelmap gồm bốn class. Cả ba không có lỗi cấu trúc. Số annotation không chứng minh số vật đúng hoặc chất lượng biên. Self-check local của ba tier chỉ dùng để tìm vùng cần xem lại; không ghi điểm tự đánh giá vào báo cáo.

## 2. Một quyết định trước khi dùng gợi ý

Chọn object đầu tiên bạn tự vẽ ở `medium_instance`, trước khi xem bất kỳ đề xuất tự động nào cho object đó. Ghi ảnh/vị trí đủ để tìm lại; “quy tắc biên” là lý do bạn chọn hoặc dừng mask ở ranh đó.

- Ảnh, vị trí và object Medium đầu tiên tự vẽ: Tôi không nhớ tên ảnh/vị trí/object cụ thể; ZIP export không lưu thứ tự thao tác để xác minh lại.
- Class và quy tắc tôi dùng để chọn biên: Tôi không nhớ class cụ thể; không thể xác nhận chi tiết hơn từ ZIP.
- Nếu dùng gợi ý sau đó: Tôi nhớ đã sửa khi thấy gợi ý không đúng, nhưng không nhớ ví dụ Medium cụ thể. Ảnh Easy đầu tiên lúc mới bắt đầu còn chưa quen thao tác; không dùng ảnh đó làm ví dụ Medium.
- Nếu không dùng gợi ý: không áp dụng.

## 3. Một lỗi tôi tìm thấy và sửa

Lỗi xác nhận được trong gói nộp là tên/vị trí file checkpoint, không phải lỗi nhãn. Không có lỗi mask cụ thể nào được xác nhận đã sửa bằng ground truth.

- Task/ảnh/vùng: `cp1.zip`, `cp2.zip`, `cp3.zip` nằm ở thư mục gốc thay vì `submissions/` và chưa theo tên task yêu cầu.
- Lỗi thuộc loại: Sai tên/vị trí gói nộp; không phải lỗi annotation.
- Bằng chứng tôi nhìn thấy: các ZIP gốc có tên ngắn; script kiểm tra yêu cầu lần lượt `cp1_holes.zip`, `cp2_slice.zip`, `cp3_thin.zip` trong `submissions/`.
- Quy tắc và hành động sửa: Đã sao chép thành `submissions/cp1_holes.zip`, `submissions/cp2_slice.zip`, `submissions/cp3_thin.zip`; chạy lại kiểm tra và cả ba đạt hợp đồng cấu trúc.
- Sau sửa đã Save và export lại chưa? Không áp dụng: đã sao chép các ZIP export hiện có, không sửa nhãn hoặc export lại từ CVAT. Độ đúng trực quan vẫn cần tự rà trong CVAT.

Self-check local đã báo hiệu cần rà soát thêm các instance Medium bị bỏ sót và một số class/vùng trong Hard; đây là phản hồi để kiểm tra, chưa phải lỗi đã sửa. Không ghi điểm vào báo cáo. Scorecard ba tier tối đa **82**, không phải điểm cuối trên 100. Không tự ghi PASS/top 3/bonus; người phụ trách xác nhận theo tiêu chí lớp. Không đưa file ground truth vào fork.

## 4. Ba ca chưa chắc hoặc đã cân nhắc

Ba ca dưới đây lấy từ các checkpoint đã nộp. Quyết định nêu theo quy tắc task; việc đạt cấu trúc ZIP không xác nhận mask thực tế đã vẽ đúng.

| Ảnh/vị trí | Hai cách hiểu có thể | Quy tắc/chứng cứ | Quyết định hoặc câu hỏi cho coach |
| --- | --- | --- | --- |
| 1 — `cp1_holes`, ảnh `000000144300.jpg`, vùng kính/khe trong vật thể | Giữ vùng kính/khe trong mask vật thể hay khoét thành lỗ? | Quy tắc CP1 yêu cầu giữ kính/chi tiết trong mask; chỉ khoét nền nếu là lỗ thật theo task. | Giữ chi tiết bên trong mask; không khoét tùy tiện. |
| 2 — `cp2_slice`, ảnh `000000017627.jpg`, vùng hai xe sát nhau | Gộp hai xe cùng class thành một mask hay tách thành hai instance? | Quy tắc CP2 yêu cầu hai xe sát nhau vẫn là hai instance. | Tách riêng từng xe, không gộp chỉ vì cùng class. |
| 3 — `cp3_thin`, ảnh `839f7736-abe28069.jpg`, vùng cột/biển mảnh | Dùng brush dày để vẽ nhanh hay brush nhỏ theo bề rộng vật thể? | Hướng dẫn checkpoint yêu cầu zoom lớn và brush 2–3 px cho cấu trúc mảnh. | Dùng brush nhỏ, kiểm lại ở zoom lớn để tránh tô tràn. |
