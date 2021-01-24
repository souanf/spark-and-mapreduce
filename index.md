# HKII_2020_504048_Xử lý dữ liệu lớn_N18
## Bài tập 1: Spark và Đếm tần suất của từ - 51800585 Nguyễn Hữu nghĩa
## Spark
### Tổng quan về Spark
- Apache Spark là một open source cluster computing framework được phát triển sơ khởi vào năm 2009 bởi AMPLab tại đại học California, Berkeley. Sau này, Spark đã được trao cho Apache Software Foundation vào năm 2013 và được phát triển cho đến nay.

- Spark cho phép xây dựng và phân tích nhanh các mô hình dự đoán. Hơn nữa, nó còn cung cấp khả năng truy xuất toàn bộ dữ liệu cùng lúc, nhờ vậy ta không cần phải lấy mẫu dữ liệu – đòi hỏi bởi các ngôn ngữ lập trình như R. Thêm vào đó, Spark còn cung cấp tính năng streaming, được dùng để xây dựng các mô hình real-time bằng cách nạp toàn bộ dữ liệu vào bộ nhớ.

- Khi ta có một tác vụ nào đó qúa lớn mà không thể xử lý trên một laptop hay một server, Spark cho phép ta phân chia tác vụ này thành những phần dễ quản lý hơn. Sau đó, Spark sẽ chạy các tác vụ này trong bộ nhớ, trên các cluster của nhiều server khác nhau để khai thác tốc độ truy xuất nhanh từ RAM. Spark sử dụng API Resilient Distributed Dataset (RDD) để xử lý dữ liệu.

- Spark nhận được nhiều sự hưởng ứng từ cộng đồng Big data trên thế giới do cung cấp khả năng tính toán nhanh và nhiều thư viện đi kèm hữu ích như Spark SQL (với kiểu dữ liệu DataFrames), Spark Streaming, MLlib (machine learning: classification, regression, clustering, collaborative filtering, và dimensionality reduction) và GraphX (biểu diễn đồ thị nhờ kết qủa tính toán song song).

- **Đối với các nhà cung cấp gỉai pháp, Apache Spark là một lá bài quan trọng trong việc sử dụng các công nghệ cốt lõi để xây dựng những data warehouses hiện đại. Đây là một phân khúc lớn trong ngành IT có khả năng thu về hàng tỉ đô doanh thu hằng năm.**

- **Spark đưa ra một khái niệm mới mang nhiều hứa hẹn trong tương lai đó là data lakes. Đây là một nơi lưu trữ một lượng dữ liệu khổng lồ với nhiều định dạng khác nhau và được truy vấn để xử lý khi cần thiết. Data lakes đưa ra một framework thương mại có thể tạo ra một môi trường lưu trữ vô hạn bất kỳ loại dữ liệu nào.**
## Mapreduce
- MapReduce là mô hình được thiết kế độc quyền bởi Google, nó có khả năng lập trình xử lý các tập dữ liệu lớn song song và phân tán thuật toán trên 1 cụm máy tính. MapReduce trở thành một trong những thành ngữ tổng quát hóa trong thời gian gần đây. 
- MapReduce sẽ  bao gồm những thủ tục sau: thủ tục 1 Map() và 1 Reduce(). Thủ tục Map() bao gồm lọc (filter) và phân loại (sort) trên dữ liệu khi thủ tục khi thủ tục Reduce() thực hiện quá trình tổng hợp dữ liệu. Đây là mô hình dựa vào các khái niệm biển đối của bản đồ và reduce những chức năng lập trình theo hướng chức năng. Thư viện của thủ tục Map() và Reduce() sẽ được viết bằng nhiều loại ngôn ngữ khác nhau. Thủ tục được cài đặt miễn phí và được sử dụng phổ biến nhất là là Apache Hadoop.
