1. Giới thiệu
Nghiên cứu này tập trung vào bài toán phân loại lưu lượng mạng nhằm:
  Phát hiện VPN / Non-VPN (binary classification)
  Phân loại ứng dụng mạng (multi-class classification)
Nghiên cứu sử dụng dataset ISCXVPN2016 và triển khai nhiều mô hình:
  Machine Learning: KNN, Decision Tree (C4.5)
  Deep Learning: MLP, CNN, LSTM
Mục tiêu:
  So sánh hiệu năng giữa ML và DL
  Đánh giá khả năng tổng quát hóa theo kích thước dữ liệu (500K, 800K, 1.1M mẫu)
  Phân tích ảnh hưởng của VPN tới đặc trưng lưu lượng

2. Dataset
2.1 Dataset sử dụng
Tên dataset: ISCXVPN2016
Nguồn: https://www.unb.ca/cic/datasets/vpn.html
Loại dữ liệu: Network traffic flow features
Số lớp:
  Binary: VPN, Non-VPN
  Multi-class:  BROWSING, CHAT, FT, MAIL, P2P, STREAMING, VOIP và các lớp tương ứng qua VPN (VPN-BROWSING, …)

2.2 Cấu trúc dữ liệu
Mỗi dòng biểu diễn một flow mạng, gồm:
  Đặc trưng thống kê (packet size, inter-arrival time, duration, …)
  Nhãn lớp (binary hoặc multi-class)

2.3 Tiền xử lý dữ liệu
Các bước tiền xử lý chính:
  Loại bỏ lưu lượng trùng lặp
  Xử lý missing values
  Chuẩn hóa dữ liệu bằng StandardScaler
  Shuffle dữ liệu
  Mã hóa nhãn
    Binary: {0: Non-VPN, 1: VPN}
    Multi-class: Label Encoding
  Cân bằng dữ liệu đa lớp
  Sinh dữ liệu synthetic bằng CTGAN
  Tạo các tập con: 500k, 800k, 1M1

3. Môi trường và thư viện
3.1 Yêu cầu hệ thống
Python >= 3.8
RAM ≥ 16GB

3.2 Cài đặt thư viện
Các thư viện chính:
  numpy
  pandas
  scikit-learn
  matplotlib
  seaborn
  tensorflow/keras
  ctgan

4. Huấn luyện mô hình
Các mô hình hỗ trợ: knn, c45, mlp, cnn, lstm
Phân loại nhị phân (VPN/Non-VPN) và đa lớp

5. Đánh giá mô hình
Các chỉ số đánh giá:
  Precision
  Recall
  F1-score
  Confusion Matrix
  Train time/Test time
6. Trực quan hóa kết quả
Sinh các biểu đồ:
  Precision/Recall/F1-score theo từng lớp
  Ma trận nhầm lẫn
  Train/Validation Loss & Accuracy
  So sánh thời gian train/test
  Trực quan hóa kết quả

7. Nhận xét chính
  KNN: train nhanh, test chậm
  C4.5: train chậm, test nhanh
  MLP & CNN: hội tụ tốt, phù hợp phân loại traffic
  LSTM: cho kết quả tốt nhất, ổn định khi dữ liệu lớn
  VPN làm mờ đặc trưng ứng dụng, gây nhầm lẫn giữa các lớp VPN

8. Hướng phát triển
  Áp dụng Transformer cho chuỗi traffic
  Học liên miền
  Phát hiện VPN chưa biết 
  Triển khai real-time IDS

9. Tác giả
  Sinh viên: Phạm Thái Khiêm
  Giảng viên hướng dẫn: Nguyễn Hữu Vân Long
  Trường: Đại học Cần Thơ
