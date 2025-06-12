---
##  Công Nghệ Sử Dụng

Dự án này được xây dựng trên nền tảng **Python**, tận dụng sức mạnh của các thư viện hàng đầu trong lĩnh vực thị giác máy tính và phân tích dữ liệu:

* **Python:** Ngôn ngữ lập trình chủ đạo, là xương sống của toàn bộ ứng dụng.
* **OpenCV (`cv2`):** Thư viện thị giác máy tính mã nguồn mở mạnh mẽ, đóng vai trò quan trọng trong việc đọc, ghi và biến đổi hình ảnh.
* **NumPy:** Cung cấp các công cụ toán học hiệu quả cho phép xử lý dữ liệu dưới dạng mảng và ma trận, là nền tảng cho các thao tác trên pixel.
* **Matplotlib:** Thư viện linh hoạt để tạo ra các biểu đồ và hiển thị trực quan các kết quả xử lý ảnh.
* **PIL (Pillow):** Hỗ trợ xử lý ảnh toàn diện, đặc biệt dùng để mở và trình chiếu ảnh trong các cửa sổ độc lập, giúp dễ dàng so sánh giữa ảnh gốc và ảnh đã xử lý.

---

##  Các Thuật Toán Nâng Cao Chất Lượng Ảnh

Ứng dụng của chúng tôi tích hợp **5 thuật toán xử lý ảnh cơ bản** nhằm cải thiện đáng kể chất lượng hình ảnh thang độ xám:

1.  **Đảo Ngược Ảnh (Inverse):** Biến đổi giá trị mỗi pixel thành giá trị đối nghịch của nó (ví dụ: đen thành trắng, trắng thành đen), tạo ra hiệu ứng âm bản.
2.  **Hiệu Chỉnh Gamma (Gamma Correction):** Điều chỉnh độ sáng và độ tương phản chung của ảnh thông qua một phép biến đổi phi tuyến tính, giúp cân bằng lại sắc thái hình ảnh.
3.  **Biến Đổi Logarit (Log Transform):** Nén dải động của ảnh, đặc biệt hữu ích trong việc làm nổi bật các chi tiết ẩn trong các vùng tối, làm cho chúng rõ ràng hơn.
4.  **Cân Bằng Biểu Đồ (Histogram Equalization):** Tự động cải thiện độ tương phản của ảnh bằng cách phân phối lại đều các giá trị cường độ pixel trên toàn bộ dải động.
5.  **Kéo Giãn Độ Tương Phản (Contrast Stretching):** Tăng cường độ tương phản bằng cách mở rộng dải giá trị pixel hiện có để bao phủ toàn bộ phạm vi thang độ xám từ 0 đến 255.

---

##  Cách Thức Hoạt Động Của Chương Trình

Ứng dụng được thiết kế để vận hành một cách trực quan theo các bước sau:

1.  **Lựa Chọn Phương Pháp Xử Lý:**
    * Khi chạy chương trình, bạn sẽ được nhắc nhập một ký tự để chọn thuật toán mong muốn:
        * `I`: Inverse (Đảo ngược ảnh)
        * `G`: Gamma Correction (Hiệu chỉnh Gamma)
        * `L`: Log Transform (Biến đổi Logarit)
        * `H`: Histogram Equalization (Cân bằng biểu đồ)
        * `C`: Contrast Stretching (Kéo giãn độ tương phản)
2.  **Xử Lý Ảnh Hàng Loạt Tự Động:**
* Chương trình sẽ tự động quét và duyệt qua tất cả các tệp ảnh (hỗ trợ định dạng `.png`, `.jpg`, `.jpeg`) có trong thư mục đầu vào (`exercise`).
    * Mỗi ảnh sẽ được đọc dưới dạng thang độ xám (`cv2.IMREAD_GRAYSCALE`).
    * Phương pháp xử lý đã chọn sẽ được áp dụng lên ảnh gốc.
    * Ảnh kết quả sau xử lý sẽ được lưu vào thư mục `output_menu`, với tên tệp được đặt theo quy ước `ten_file_goc_KY_TU_PHUONG_PHAP.png` (ví dụ: `image01_I.png`).
3.  **Trực Quan Hóa Kết Quả Ngay Lập Tức:**
    * Để tiện so sánh, ảnh gốc và ảnh đã xử lý sẽ được hiển thị trong **hai cửa sổ riêng biệt** thông qua thư viện `PIL`.
    * Đồng thời, ảnh đã xử lý cũng được trình chiếu trong một cửa sổ đồ họa riêng biệt sử dụng `matplotlib.pyplot`, giúp bạn dễ dàng đánh giá sự thay đổi.

---

###  Chi Tiết Kỹ Thuật Các Hàm Xử Lý Ảnh

Mỗi hàm dưới đây là trái tim của các thuật toán, thực hiện các phép biến đổi pixel một cách chính xác:

* `**inverse(img)`**
    ```python
    def inverse(img): return 255 - img
    ```
    Hàm này đơn giản là đảo ngược cường độ sáng của mỗi pixel, biến pixel có giá trị $X$ thành $255 - X$.

* `**gamma_correction(img, gamma=2.2)`**
    ```python
    def gamma_correction(img, gamma=2.2):
        return np.power(img / 255.0, gamma) * 255
    ```
    Hàm này áp dụng phép hiệu chỉnh Gamma bằng cách chuẩn hóa giá trị pixel về khoảng $[0, 1]$, lũy thừa với hệ số `gamma` (mặc định là $2.2$), sau đó mở rộng lại về khoảng $[0, 255]$. `gamma < 1` làm ảnh sáng hơn, `gamma > 1` làm ảnh tối hơn.

* `**log_transform(img)`**
    ```python
    def log_transform(img): return np.log1p(img) / np.log(256) * 255
    ```
    Hàm này thực hiện biến đổi logarit, nén các giá trị pixel cao và mở rộng các giá trị pixel thấp. Điều này đặc biệt hữu ích để làm rõ các chi tiết trong vùng tối. `np.log1p(img)` được sử dụng để xử lý an toàn giá trị pixel bằng 0.

* `**hist_equalization(img)`**
    ```python
    def hist_equalization(img): return cv2.equalizeHist(img)
    ```
    Sử dụng hàm `cv2.equalizeHist()` của OpenCV, hàm này tự động điều chỉnh phân bố cường độ pixel của ảnh để làm phẳng biểu đồ xám, từ đó tăng cường độ tương phản tổng thể.

* `**contrast_stretch(img)`**
    ```python
    def contrast_stretch(img): return ((img - img.min()) / (img.max() - img.min()) * 255).astype(np.uint8)
    ```