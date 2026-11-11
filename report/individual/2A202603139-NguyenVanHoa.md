# Báo cáo thực hành Day 3 — điền trực tiếp trong fork của bạn

**Cách dùng:** Thay mọi dấu `…` bằng bài làm thật của bạn trước khi nộp link fork trên [LMS](https://aithucchien.vinuni.edu.vn). Giữ nguyên bốn mục và bảng để coach đọc nhanh. Viết ngắn, cụ thể theo ảnh/vùng; không cần thuật ngữ chuyên sâu. Ví dụ trong [hướng dẫn mẫu](../../reports/REPORT_TEMPLATE.md) chỉ giúp hiểu cách điền, không phải câu trả lời để chép lại.

- Mã học viên theo lớp: 2A202603139
- Ngày / CVAT local: 11–12/11/2026
- Công cụ đã dùng: CVAT local; SAM 2.1 Tiny hỗ trợ gợi ý mask.

Mã học viên là mã lớp cấp; không cần ghi họ tên trong report nếu kênh [LMS](https://aithucchien.vinuni.edu.vn) đã nhận diện bạn. Chỉ ghi công cụ thật sự đã dùng; không có SAM vẫn làm bài bình thường.

## 1. Bài đã nộp

Ghi tên ZIP đúng như file trong `submissions/` và số ảnh đã vẽ, Save. Chưa làm hoặc export lỗi thì ghi `chưa có`, không tạo ZIP rỗng. Cột điểm là điểm tối đa của task, **không phải điểm tự chấm**.

| Task | File ZIP đúng tên | Hoàn thành mấy ảnh | Điểm tối đa (coach chấm sau) |
| --- | --- | ---: | ---: |
| easy_semantic | easy_semantic.zip | 3 / 3 | 20 |
| medium_instance | medium_instance.zip | 3 / 3 ảnh có trong export | 32 |
| hard_panoptic | hard_panoptic.zip | 2 / 2 ảnh có trong export; cần kiểm tra lỗi | 30 |
| cp1_holes | chưa có | 0 / 1 | 3 |
| cp2_slice | chưa có | 0 / 1 | 3 |
| cp5_occlusion | chưa có | 0 / 1 | 3 |
| cp3_thin | chưa có | 0 / 1 | 3 |
| cp4_curb | chưa có | 0 / 1 | 3 |
| cp6_coverage | chưa có | 0 / 1 | 3 |
| **Tổng tối đa** | | | **100** |

Kiểm tra cấu trúc ZIP: Easy và Medium báo OK. Hard báo bốn annotation thiếu polygon/RLE hợp lệ, cần kiểm tra và export lại. Số ảnh có trong export không chứng minh mọi vùng đã được gán nhãn đầy đủ; kiểm tra cấu trúc cũng không phải điểm chấm.

## 2. Một quyết định trước khi dùng gợi ý

Chọn object đầu tiên bạn tự vẽ ở `medium_instance`, trước khi xem bất kỳ đề xuất tự động nào cho object đó. Ghi ảnh/vị trí đủ để tìm lại; “quy tắc biên” là lý do bạn chọn hoặc dừng mask ở ranh đó.

- Ảnh, vị trí và object Medium đầu tiên tự vẽ: chưa có thông tin để ghi; cần học viên bổ sung.
- Quy tắc chung: các vật cùng lớp vẫn được tách thành từng object; chỉ gán phần nhìn thấy.
- SAM hỗ trợ gợi ý mask; cần tự kiểm class, số object và đường biên. Quyết định sửa/giữ cụ thể: cần học viên bổ sung.

## 3. Một lỗi tôi tìm thấy và sửa

Chọn một lỗi **có thật** trong bài. Nếu công cụ lỗi khiến bạn chưa sửa được, ghi rõ đã thử gì và cần coach hỗ trợ gì; không ghi “đã sửa” khi chưa sửa.

- Task/ảnh/vùng: hard_panoptic, ảnh `000000350023.jpg` và `000000460147.jpg`, vùng road/sky.
- Lỗi kiểm tra export: bốn annotation 1, 2, 16 và 17 có segmentation rỗng, thiếu polygon/RLE hợp lệ.
- Hướng xử lý: kiểm tra loại hình dạng trong CVAT, Save và export lại COCO 1.0, sau đó chạy lại lệnh kiểm tra. Nếu vẫn lỗi, hỏi coach.
- Trạng thái: chưa xác nhận đã sửa hoặc export lại.

Nếu bạn **đã xem Summary tự đánh giá trên GitHub Actions hoặc tự chạy script**, ghi ngắn một kết quả liên quan lỗi vừa sửa (ví dụ task, metric trước/sau nếu có): … / chưa có điểm. Scorecard ba tier tối đa **82**, không phải điểm cuối trên 100. Không tự ghi PASS/top 3/bonus; người phụ trách xác nhận theo tiêu chí lớp. Không đưa file ground truth vào fork.

## 4. Ba ca chưa chắc hoặc đã cân nhắc

Mỗi ca là một **vùng cụ thể** khiến bạn phải cân nhắc hai cách hiểu. Ghi dấu hiệu nhìn thấy hoặc quy tắc đã dùng, rồi nêu quyết định hoặc câu hỏi cho coach. Không cần ba lỗi; ca đã quyết định được cũng hợp lệ.

| Ảnh/vị trí | Hai cách hiểu có thể | Quy tắc/chứng cứ | Quyết định hoặc câu hỏi cho coach |
| --- | --- | --- | --- |
| Hai ảnh Hard, vùng road/sky | Bốn annotation trong export chưa có segmentation hợp lệ | Kết quả kiểm tra cấu trúc ZIP | Kiểm tra trong CVAT và export lại |
| Medium, các vật sát nhau | Có thể gộp hai vật cùng class thành một object | Mỗi vật nhìn thấy cần một instance | Kiểm tra số object trong CVAT |
| Hard, vật thể chồng nền | Có thể khó xác định ranh giữa vật và nền | Chỉ gán phần nhìn thấy | Kiểm tra trực quan; hỏi coach nếu chưa rõ |

Hai dòng cuối là các điểm cần kiểm tra chung, chưa khẳng định đã tìm thấy lỗi tại vị trí cụ thể. Cần bổ sung các ca thực tế nếu đề bài yêu cầu.
