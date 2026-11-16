# FIT4013 · Nhóm 4 · Đề tài 13

## Dự đoán nhân viên có khả năng nghỉ việc

- Học phần Nhập môn học máy (FIT4013), Trường Đại học Đại Nam.
- Giảng viên hướng dẫn ThS. Lê Thị Thùy Trang.
- Nhóm 4, Đỗ Cao Phong.

Đề tài phân loại nhị phân theo nhãn `Attrition`. Notebook so sánh Baseline với K-NN và Cây quyết định, mỗi thuật toán dùng hai luồng tiền xử lý. Phần mở rộng lưu 68 cấu hình dò tham số, so sánh khi bỏ từng tỷ lệ thâm niên và truy vết hai dự đoán sai.

## Dữ liệu

Sử dụng bộ [IBM HR Analytics Employee Attrition & Performance](https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset) do tài liệu hướng dẫn FIT4013 chỉ định tại mục 5.2. File cần tải vào Colab là `WA_Fn-UseC_-HR-Employee-Attrition.csv`, gồm 1.470 dòng, 35 cột, với 237 dòng có `Attrition=Yes`. Nếu nhận dữ liệu trong `archive.zip`, giải nén để lấy CSV.

## Chạy lại bằng Google Colab

1. Tải `Nhom4_DeTai13.ipynb` từ repo về máy. Mở [Google Colab](https://colab.research.google.com/) và tải notebook lên trong menu **Tệp**.
2. Chạy ô đầu tiên và chọn đúng CSV nói trên khi hộp thoại tải tệp xuất hiện.
3. Chạy tiếp các ô từ 2 đến 11 theo thứ tự. Notebook chia phân tầng 80/20 và dùng 5 fold phân tầng với `random_state=42`.
4. Xem đầu ra dưới từng ô hoặc trong thanh **Tệp** của Colab. ZIP tự tải ở ô 8 có 10 tệp. Ba CSV của ô 9–11 được lưu riêng và có sẵn trong `results/` của repo.

Notebook được kiểm tra lại từ đầu với Python 3.12.14 và các phiên bản trong `requirements.txt`. Google Colab cung cấp sẵn chức năng tải CSV được gọi trong ô đầu tiên.

## Kết quả chính

| Phương án | F1 kiểm định chéo | Accuracy kiểm thử | Recall kiểm thử | F1 kiểm thử |
| --- | ---: | ---: | ---: | ---: |
| Baseline | 0,0000 | 0,8401 | 0,0000 | 0,0000 |
| K-NN A | 0,2559 | 0,8299 | 0,1915 | 0,2647 |
| K-NN B | 0,2675 | 0,8231 | 0,1277 | 0,1875 |
| Cây quyết định A | 0,3905 | 0,8095 | 0,3404 | 0,3636 |
| Cây quyết định B | 0,4068 | 0,8027 | 0,3617 | 0,3696 |

Cây quyết định B được chọn theo F1 kiểm định chéo trong thí nghiệm chính. Trên 294 dòng kiểm thử, cây phát hiện đúng 17 trong 47 ca nghỉ việc. Thí nghiệm bỏ từng tỷ lệ dùng kiểm định chéo trên tập huấn luyện và được lưu riêng với phần đánh giá kiểm thử.

## Tệp dự án

| Tệp | Nội dung |
| --- | --- |
| `Nhom4_DeTai13.ipynb` | Mã nguồn Colab gồm 11 ô đã chạy |
| `requirements.txt` | Các phiên bản thư viện của lần chạy đối chiếu |
| `results/` | Bảng kết quả, biểu đồ và ba CSV bổ sung của bước 9–11 |
| `AI_USAGE.md` | Khai báo sử dụng AI |

Báo cáo nộp bài được hoàn thiện sau khi xác định đường dẫn repo của nhóm.
