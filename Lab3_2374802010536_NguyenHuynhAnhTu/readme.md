#1.1
-Công nghệ sử dụng
ImageIO: đọc và lưu ảnh
NumPy: cắt ảnh bằng slicing

-Thuật toán
Đọc ảnh gốc fruit.jpg
Cắt vùng ảnh bằng chỉ số hàng và cột để lấy quả cam
Ghi ảnh kết quả ra file mới
-Cách thức hoạt động

Dùng slicing data[y1:y2, x1:x2] để lấy vùng mong muốn.
Có thể thay đổi chỉ số để chọn vùng khác.

#1.2
-Công nghệ sử dụng
SciPy (ndimage): shift()

-Thuật toán
Dịch ảnh xuống 100 pixel và sang phải 25 pixel bằng nd.shift()

-Cách thức hoạt động
Tịnh tiến dịch toàn bộ ảnh theo vector (dy, dx).
Giá trị ngoài biên được nội suy hoặc điền mặc định.

#1.3
-Công nghệ sử dụng
SciPy (ndimage): zoom()

-Thuật toán
Dùng zoom(data, factor) để phóng to hoặc thu nhỏ ảnh.
Có thể zoom theo từng chiều: (zoom_y, zoom_x, kênh màu)

-Cách thức hoạt động
Nội suy để tạo ra ảnh có kích thước mới.
Nếu phóng to: thêm chi tiết bằng nội suy.
Nếu thu nhỏ: loại bớt điểm ảnh.

#1.4
-Công nghệ sử dụng
SciPy (ndimage): rotate()

-Thuật toán
Dùng rotate(data, angle) để xoay ảnh theo góc cho trước.

-Cách thức hoạt động
Nếu reshape=True: ảnh mở rộng để không cắt nội dung.
Nếu reshape=False: giữ kích thước, phần bị quay ra ngoài sẽ bị cắt.

#1.5
-Công nghệ sử dụng
SciPy (ndimage): binary_dilation()

-Thuật toán
Dùng phép toán morphological để mở rộng vùng trắng (1 pixel).
Có thể lặp nhiều lần bằng tham số iterations.

-Cách thức hoạt động
Mỗi điểm trắng lan rộng ra các pixel lân cận.
Dùng để làm mờ hoặc làm to vật thể trong ảnh nhị phân.

#1.6
-Công nghệ sử dụng
NumPy: tạo toạ độ bị nhiễu
SciPy (ndimage): map_coordinates()

-Thuật toán
Sinh lưới toạ độ gốc của ảnh
Thêm nhiễu nhỏ có biên độ d vào toạ độ
Ánh xạ ảnh theo toạ độ bị biến dạng bằng map_coordinates

-Cách thức hoạt động
Mỗi pixel bị dịch nhẹ theo hướng ngẫu nhiên.
Tạo hiệu ứng rung nhẹ hoặc gợn sóng không đều.

#1.7
-Công nghệ sử dụng
OpenCV: blur, medianBlur, GaussianBlur, bilateralFilter
Matplotlib: hiển thị ảnh

-Thuật toán
Đọc ảnh mức xám
Áp dụng lần lượt các bộ lọc làm mượt:
Trung bình (mean)
Trung vị (median)
Gauss
Bilateral (giữ biên)

-Cách thức hoạt động
Bộ lọc trung bình (mean): thay mỗi điểm ảnh bằng giá trị trung bình của vùng lân cận, giúp làm mờ nhẹ toàn ảnh.
Bộ lọc trung vị (median): chọn giá trị trung vị từ vùng lân cận, hiệu quả trong việc loại bỏ nhiễu muối tiêu.
Các bộ lọc như Gaussian và bilateral giữ cạnh tốt hơn, phù hợp cho ảnh có nhiều chi tiết.
Giúp giảm nhiễu hoặc làm mềm ảnh chuẩn bị cho bước xử lý tiếp theo.

#1
-Công nghệ sử dụng
NumPy: tạo lưới toạ độ và tính toán sóng sin
SciPy (ndimage): dịch chuyển ảnh (shift) và biến đổi toạ độ (map_coordinates)
ImageIO: đọc và ghi ảnh
Matplotlib: hiển thị ảnh

-Thuật toán
Dùng shift() để tịnh tiến ảnh kiwi xuống 30px và sang phải 50px.
Tạo hiệu ứng sóng bằng cách biến đổi toạ độ x theo hàm sin.
Ánh xạ lại ảnh theo toạ độ mới bằng map_coordinates() trên từng kênh màu.

-Cách thức hoạt động
Mỗi pixel được ánh xạ sang vị trí mới theo dạng lượn sóng ngang.
Nội suy để lấy giá trị pixel tại vị trí mới.
Gắn ảnh đã biến dạng vào nền và lưu kết quả.

#2
-Công nghệ sử dụng
PIL: xử lý ảnh RGBA, dán ảnh lên nền
NumPy: tạo và áp dụng gradient màu
ImageIO: đọc và ghi ảnh PNG

-Thuật toán
Đọc ảnh đu đủ và dưa hấu có nền trong suốt.
Tạo gradient tuyến tính giữa hai màu (theo chiều dọc ảnh).
Thay đổi màu mỗi dòng ảnh theo giá trị gradient.
Dán hai quả vào ảnh nền trong suốt bằng mặt nạ alpha.

-Cách thức hoạt động
Ảnh giữ nguyên hình dạng gốc nhờ lớp alpha (trong suốt).
Gradient được áp dụng từ trên xuống dưới.
Hai ảnh được ghép lại trên một ảnh nền và lưu dưới dạng PNG.

#3
-Công nghệ sử dụng
NumPy: tạo dải màu chuyển tiếp
ImageIO: đọc ảnh đầu vào, ghi ảnh kết quả

-Thuật toán
Tạo ảnh đơn sắc hoặc ảnh RGB bất kỳ.
Dùng np.linspace() để tạo gradient chuyển màu từ trái sang phải.
Áp dụng màu mới cho từng dòng của ảnh theo dải gradient.

-Cách thức hoạt động
Mỗi dòng ảnh được tô theo màu chuyển dần từ màu đầu đến màu cuối.
Tạo hiệu ứng ánh sáng hoặc màu nền mượt hơn cho ảnh.

#4
-Công nghệ sử dụng
NumPy: sinh nhiễu ngẫu nhiên trong phạm vi nhỏ
SciPy (ndimage): dùng map_coordinates() để biến dạng ảnh

-Thuật toán
Tạo lưới toạ độ gốc bằng np.indices().
Thêm nhiễu nhỏ vào lưới này để làm biến dạng nhẹ
Dùng map_coordinates() để ánh xạ ảnh gốc sang vị trí mới bị nhiễu

-Cách thức hoạt động
Toạ độ mỗi pixel bị lệch ngẫu nhiên tạo hiệu ứng biến dạng nhẹ như gợn nước.
Giúp tạo hiệu ứng nghệ thuật hoặc che giấu chi tiết nhỏ trong ảnh

#5
-Công nghệ sử dụng
Python cơ bản: input() để tạo menu tương tác
SciPy (ndimage): thực hiện các phép biến đổi (xoay, phóng to, tịnh tiến...)
ImageIO: đọc ảnh từ thư mục
Matplotlib: hiển thị kết quả ảnh sau biến đổi

-Thuật toán
Người dùng nhập tên ảnh và chọn phép biến đổi bằng phím tắt: T (tịnh tiến), X (xoay), P (phóng to), H (thu nhỏ), C (biến dạng).
Áp dụng hàm tương ứng như shift, rotate, zoom, hoặc map_coordinates tuỳ theo lựa chọn.

-Cách thức hoạt động
Ảnh được xử lý tùy theo lựa chọn của người dùng.
Hiệu ứng được áp dụng trực tiếp và hiển thị ngay sau khi chọn.
Đây là ví dụ về giao diện dòng lệnh đơn giản giúp luyện kỹ năng thao tác ảnh.