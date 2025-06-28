\#2.1.1. Phương pháp Otsu

\*\*Công nghệ sử dụng:\*\*

\- PIL: Đọc và chuyển đổi ảnh sang grayscale

\- NumPy: Xử lý mảng ảnh

\- skimage: Áp dụng ngưỡng Otsu

\- matplotlib: Hiển thị ảnh



\*\*Thuật toán:\*\*

\- Đọc ảnh dalat.jpg và chuyển sang ảnh xám

\- Áp dụng phương pháp Otsu để tìm ngưỡng tự động

\- Tạo ảnh nhị phân bằng cách so sánh từng pixel với ngưỡng

\- Hiển thị ảnh kết quả



\*\*Cách thức hoạt động:\*\*

\- Otsu tự động tính ngưỡng phân tách foreground/background

\- Pixel > ngưỡng → trắng (1), ngược lại → đen (0)

\- Kết quả là ảnh nhị phân đen trắng



\#2.1.2. Phương pháp Adaptive Thresholding

\# Giải thích code Adaptive Thresholding



\*\*Công nghệ sử dụng:\*\*

\- PIL: Đọc và chuyển đổi ảnh sang grayscale

\- NumPy: Xử lý mảng ảnh

\- skimage: Áp dụng ngưỡng Adaptive Threshold

\- matplotlib: Hiển thị ảnh



\*\*Thuật toán:\*\*

1\. Đọc ảnh dalat.jpg và chuyển sang ảnh xám

2\. Áp dụng Adaptive Thresholding với:

&nbsp;  - Kích thước khối 39x39 pixel

&nbsp;  - Giá trị offset=10

3\. Hiển thị ảnh kết quả



\*\*Cách thức hoạt động:\*\*

\- Tính ngưỡng riêng cho từng vùng ảnh nhỏ (39x39 pixel)

\- Điều chỉnh ngưỡng bằng giá trị offset

\- Phù hợp với ảnh có ánh sáng không đồng đều



\#2.2. Phân vùng theo region

\# Giải thích code Watershed Segmentation



\*\*Công nghệ sử dụng:\*\*

\- OpenCV: Đọc ảnh, chuyển đổi màu và xử lý ảnh

\- NumPy: Xử lý mảng ảnh

\- scipy.ndimage: Gán nhãn và xử lý ảnh

\- matplotlib: Hiển thị ảnh



\*\*Thuật toán:\*\*

1\. Đọc ảnh và chuyển sang ảnh xám

2\. Áp dụng Otsu thresholding đảo ngược

3\. Thực hiện erosion (2 lần)

4\. Tính Distance Transform

5\. Áp dụng threshold lên Distance Transform

6\. Gán nhãn các vùng

7\. Áp dụng thuật toán Watershed

8\. Hiển thị kết quả



\*\*Cách thức hoạt động:\*\*

\- Phân tách các đối tượng chạm nhau bằng Watershed

\- Sử dụng Distance Transform để xác định tâm các đối tượng

\- Kết hợp threshold và morphological operations để chuẩn bị ảnh

\- Kết quả là ảnh với các vùng được phân tách rõ ràng



\#2.3.1. Sử dụng binary\_dilation

\*\*Công nghệ sử dụng:\*\*

\- PIL: Đọc và chuyển đổi ảnh sang grayscale

\- scipy.ndimage: Thực hiện phép giãn nhị phân (binary dilation)

\- matplotlib: Hiển thị ảnh kết quả



\*\*Thuật toán:\*\*

1\. Đọc ảnh dalat.jpg và chuyển sang ảnh xám

2\. Áp dụng phép giãn nhị phân (dilation) với:

&nbsp;  - Số lần lặp: 50 iterations

3\. Hiển thị ảnh kết quả



\*\*Cách thức hoạt động:\*\*

\- Phép giãn làm "phình to" các vùng trắng (foreground)

\- Mỗi pixel trắng sẽ mở rộng ra các pixel lân cận

\- Số lần lặp càng lớn thì hiệu ứng càng mạnh

\- Kết quả làm tăng kích thước các đối tượng trong ảnh nhị phân



\#2.3.2. Sử dụng binary\_opening

\# Giải thích code Binary Opening



\*\*Công nghệ sử dụng:\*\*

\- PIL: Đọc và chuyển đổi ảnh sang grayscale

\- scipy.ndimage: Thực hiện phép mở nhị phân (binary opening)

\- matplotlib: Hiển thị ảnh kết quả



\*\*Thuật toán:\*\*

1\. Đọc ảnh dalat.jpg và chuyển sang ảnh xám

2\. Định nghĩa phần tử cấu trúc (structuring element)

3\. Áp dụng phép mở nhị phân (opening) với:

&nbsp;  - Phần tử cấu trúc hình chữ thập (cross-shaped)

&nbsp;  - Số lần lặp: 25 iterations

4\. Hiển thị ảnh kết quả



\*\*Cách thức hoạt động:\*\*

\- Phép mở = erosion (co) sau dilation (giãn)

\- Loại bỏ nhiễu trắng nhỏ (small white noise)

\- Làm mịn đường viền đối tượng

\- Giữ nguyên kích thước tổng thể các đối tượng lớn

\- Phần tử cấu trúc dạng chữ thập giúp bảo toàn hình dạng đối tượng



\#2.3.3. Sử dụng binary\_erosion

\*\*Công nghệ sử dụng:\*\*

\- PIL: Đọc và chuyển đổi ảnh sang grayscale

\- scipy.ndimage: Thực hiện phép co nhị phân (binary erosion)

\- matplotlib: Hiển thị ảnh kết quả



\*\*Thuật toán:\*\*

1\. Đọc ảnh dalat.jpg và chuyển sang ảnh xám

2\. Định nghĩa phần tử cấu trúc dạng chữ thập

3\. Áp dụng phép co nhị phân với:

&nbsp;  - Phần tử cấu trúc 3x3

&nbsp;  - Số lần lặp: 50 iterations

4\. Hiển thị ảnh kết quả



\*\*Cách thức hoạt động:\*\*

\- Phép co làm "thu nhỏ" các vùng trắng (foreground)

\- Loại bỏ pixel ở biên đối tượng

\- Hiệu ứng mạnh khi tăng số lần lặp

\- Phần tử cấu trúc dạng chữ thập giúp bảo toàn hình dạng cơ bản

\- Lưu ý: Code có lỗi 'plt.imshow(k)' nên sửa thành 'plt.imshow(c)'



\#2.3.4. Sử dụng binary\_closing

\*\*Công nghệ sử dụng:\*\*

\- PIL: Đọc và chuyển đổi ảnh sang grayscale

\- scipy.ndimage: Thực hiện phép đóng nhị phân (binary closing)

\- matplotlib: Hiển thị ảnh kết quả



\*\*Thuật toán:\*\*

1\. Đọc ảnh dalat.jpg và chuyển sang ảnh xám

2\. Định nghĩa phần tử cấu trúc dạng chữ thập

3\. Áp dụng phép đóng nhị phân với:

&nbsp;  - Phần tử cấu trúc 3x3

&nbsp;  - Số lần lặp: 50 iterations

4\. Hiển thị ảnh kết quả



\*\*Cách thức hoạt động:\*\*

\- Phép đóng = dilation (giãn) sau erosion (co)

\- Lấp đầy các lỗ nhỏ bên trong đối tượng

\- Kết nối các vùng gần nhau

\- Làm mịn đường viền đối tượng

\- Phần tử cấu trúc dạng chữ thập giúp bảo toàn hình dạng cơ bản



\#bai1

\*\*Công nghệ sử dụng:\*\*

\- OpenCV (cv2): Đọc ảnh và xử lý ảnh

\- NumPy: Thao tác với mảng dữ liệu ảnh

\- scikit-image: Áp dụng ngưỡng Otsu

\- matplotlib: Hiển thị ảnh kết quả



\*\*Thuật toán:\*\*

1\. Đọc ảnh dalat.jpg ở chế độ grayscale

2\. Cắt vùng ảnh LangBiang (tọa độ \[0:400, 0:500])

3\. Áp dụng ngưỡng Otsu và điều chỉnh hệ số 0.3

4\. Dịch ảnh sang phải 100 pixel

5\. Lưu và hiển thị ảnh kết quả



\*\*Cách thức hoạt động:\*\*

\- `threshold\_otsu()` tự động tính ngưỡng phân tách foreground/background

\- Nhân ngưỡng với 0.3 để điều chỉnh độ nhạy

\- Tạo ảnh nhị phân (đen trắng) từ ngưỡng

\- Dịch ảnh bằng cách thao tác trực tiếp trên mảng NumPy



\#bai2

\*\*Công nghệ sử dụng:\*\*

\- OpenCV (cv2): Đọc ảnh, xoay ảnh và adaptive thresholding

\- NumPy: Thao tác với mảng dữ liệu ảnh

\- matplotlib: Hiển thị ảnh kết quả



\*\*Thuật toán:\*\*

1\. Đọc ảnh dalat.jpg ở chế độ grayscale (có lỗi cần sửa)

2\. Cắt vùng ảnh Hồ Xuân Hương (tọa độ \[0:700, 500:1000])

3\. Xoay ảnh 45 độ quanh tâm

4\. Áp dụng adaptive thresholding với:

&nbsp;  - Phương pháp: GAUSSIAN

&nbsp;  - Kích thước khối: 11x11

&nbsp;  - Ngưỡng C: 60

5\. Lưu và hiển thị ảnh kết quả



\*\*Cách thức hoạt động:\*\*

\- `getRotationMatrix2D()` tạo ma trận biến đổi xoay

\- `warpAffine()` thực hiện phép xoay ảnh

\- `adaptiveThreshold()` tính ngưỡng cục bộ cho từng vùng ảnh

\- Kết quả là ảnh nhị phân (đen trắng) với các vùng được phân tách rõ



\#bai3

\*\*Công nghệ sử dụng:\*\*

\- OpenCV: Đọc ảnh

\- NumPy: Tạo mask và xử lý mảng

\- SciPy: Áp dụng binary closing

\- matplotlib: Hiển thị ảnh



\*\*Thuật toán:\*\*

1\. Đọc ảnh grayscale (lỗi `IWREAD\_GRAYSCALE` cần sửa thành `IMREAD\_GRAYSCALE`)

2\. Cắt vùng Quảng trường \[0:400, 1000:1500]

3\. Tạo mask hình chữ nhật \[50:450, 50:550]

4\. Áp dụng binary closing với kernel 5x5

5\. Lưu và hiển thị ảnh



\*\*Thuật toán::\*\*

\- Đóng các lỗ nhỏ trong đối tượng

\- Kết nối các vùng gần nhau

\- Kernel 5x5 quyết định mức độ ảnh hưởng



\#bai4

Công nghệ sử dụng:



OpenCV: Xử lý ảnh và biến đổi hình học



NumPy: Thao tác với mảng dữ liệu ảnh



SciPy: Các phép toán hình thái học (dilation/erosion)



scikit-image: Phương pháp Otsu thresholding



Thuật toán chính:



Biến đổi hình học:



Xoay ảnh (rotation matrix)



Scaling (tỉ lệ 1.5x)



Dịch chuyển (translation)



Phân vùng ảnh:



Adaptive thresholding (Gaussian)



Binary dilation/erosion (kernel 5x5)



Otsu automatic thresholding



Menu lựa chọn:



Tương tác qua input terminal



Kết hợp nhiều phép biến đổi

Thuật toán chính:



Biến đổi ảnh: Xoay, phóng to, dịch chuyển



Phân vùng ảnh:



Ngưỡng thích ứng (adaptive thresholding)



Giãn nở (dilation)/bào mòn (erosion) nhị phân



Tự động chọn ngưỡng Otsu





