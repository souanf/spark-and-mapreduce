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
### Tổng quan
- MapReduce là mô hình được thiết kế độc quyền bởi Google, nó có khả năng lập trình xử lý các tập dữ liệu lớn song song và phân tán thuật toán trên 1 cụm máy tính. MapReduce trở thành một trong những thành ngữ tổng quát hóa trong thời gian gần đây. 
- MapReduce sẽ  bao gồm những thủ tục sau: thủ tục 1 Map() và 1 Reduce(). Thủ tục Map() bao gồm lọc (filter) và phân loại (sort) trên dữ liệu khi thủ tục khi thủ tục Reduce() thực hiện quá trình tổng hợp dữ liệu. Đây là mô hình dựa vào các khái niệm biển đối của bản đồ và reduce những chức năng lập trình theo hướng chức năng. Thư viện của thủ tục Map() và Reduce() sẽ được viết bằng nhiều loại ngôn ngữ khác nhau. Thủ tục được cài đặt miễn phí và được sử dụng phổ biến nhất là là Apache Hadoop.
  - **Hàm Map()**: có nhiệm vụ nhận Input cho các cặp giá trị/  khóa và output chính là tập những cặp giá trị/khóa trung gian. Sau đó, chỉ cần ghi xuống đĩa cứng và tiến hành thông báo cho các hàm Reduce() để trực tiếp nhận dữ liệu. 
  - **Hàm Reduce()**: có nhiệm vụ tiếp nhận từ khóa trung gian và những giá trị tương ứng với lượng từ khóa đó. Sau đó, tiến hành ghép chúng lại để có thể tạo thành một tập khóa khác nhau. Các cặp khóa/giá trị này thường sẽ thông qua một con trỏ vị trí để đưa vào các hàm reduce. Quá trình này sẽ giúp cho lập trình viên quản lý dễ dàng hơn một lượng danh sách cũng như  phân bổ giá trị sao cho  phù hợp nhất với bộ nhớ hệ thống. 
  - Ở giữa Map và Reduce thì còn 1 bước trung gian đó chính là **Shuffle**. Sau khi Map hoàn thành  xong công việc của mình thì Shuffle sẽ làm nhiệm vụ chính là thu thập cũng như tổng hợp từ khóa/giá trị trung gian đã được map sinh ra trước đó rồi chuyển qua cho Reduce tiếp tục xử lý.
 ### Nguyên tắc hoạt động 
Mapreduce hoạt động dựa vào nguyên tắc chính là “Chia để trị”, như sau:
```
- Phân chia các dữ liệu cần xử lý thành nhiều phần nhỏ trước khi thực hiện. 
- Xử lý các vấn đề nhỏ theo phương thức song song trên các máy tính rồi phântán hoạt động theo hướng độc lập.
- Tiến hành tổng hợp những kết quả thu được để đề ra được kết quả sau cùng. 
```
### Các bước hoạt động của MapReduce
1. Tiến hành chuẩn bị các dữ liệu đầu vào để cho Map() có thể xử lý.
2. Lập trình viên thực thi các mã Map() để xử  lý. 
3. Tiến hành trộn lẫn các dữ liệu được xuất ra bởi Map() vào trong Reduce Processor
4. Tiến hành thực thi tiếp mã Reduce() để có thể xử lý tiếp các dữ liệu cần thiết.  
5. Thực hiện tạo các dữ liệu xuất ra cuối cùng. 
### Ví dụ sử dụng MapReduce
Bài toán đếm tần suất từ (word count)
- Yêu cầu: đếm và trả về 10 từ có tần suất xuất hiện nhiều nhất trong file
- Khai báo thư viện, đọc file, chuẩn hóa file (lower case, bỏ các dấu câu), xem dòng đầu tiên:
- Tách file text thành list chứa các từ
- **map** : Mỗi từ là một cặp khóa (word, 1)
- **reduce** : hàm reduceByKey duyệt các key có giá trị giống nhau và cộng value của chúng lại
- xuất kết quả bằng cách dùng **map** đổi vị trí key và value, sau đó sắp xếp giảm dần theo key(tần suất từ) và xuất ra 10 từ có tần suất xuất hiện nhiều nhất
