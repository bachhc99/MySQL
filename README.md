# I.MySQL cơ bản
## Nội dung bài viết
- [I. MySQL là gì](#1)
- [II. MySQL hoạt dộng ntn?](#2)
- [III Storage Engine](#3)

## I.Vậy MySQL là gì ? <a name="1"></a>
MySQL là một hệ thống quản trị cơ sở dữ liệu mã nguồn mở (Relational Database Management System, viết tắt là RDBMS) hoạt động theo mô hình client-server. RDBMS là một phần mềm hay dịch vụ dùng để tạo và quản lý các cơ sở dữ liệu (Database) theo hình thức quản lý các mối liên hệ giữa chúng.
Vậy chúng ta cần phải biết RDBMS là gì . Thì ở đây chúng ta sẽ có 2 khái niệm là DBMS và RDBMS
DBMS viết tắt là Database Management System hay còn gọi là hệ thống quản trị csdl
RDBMS là viết tắt của Relational Database Management System hay còn gọi là hệ thống quản trị csdl quan hệ
Vậy DBMS và RDBMS khác nhau ntn ?
Trong DBMS, dữ liệu thường được lưu trữ ở dạng phân cấp hoặc dạng điều hướng. Điều này có nghĩa là một đơn vị dữ liệu sẽ có một nút cha và 0, một hoặc nhiều nút con. Nó thậm chí có thể được lưu trữ dưới dạng biểu đồ, có thể nhìn thấy trong mô hình mạng.
Trong RDBMS, các bảng sẽ có một mã định danh được gọi là khóa chính. Giá trị dữ liệu sẽ được lưu trữ dưới dạng bảng. Mối quan hệ giữa các giá trị dữ liệu này cũng sẽ được lưu trữ dưới dạng bảng. Mọi giá trị được lưu trữ trong cơ sở dữ liệu quan hệ đều có thể truy cập được. Giá trị này có thể được cập nhật bởi hệ thống. Dữ liệu trong hệ thống này cũng độc lập về mặt vật lý và logic.
Vậy như đã nói ở trên MySQL hoạt động theo mô hình client-server. vậy cta cần phải biết mồ hình client-server hoạt động ntn. Ở đây tôi sẽ giải thích đơn giản , Máy tính cài đặt và chạy phần mềm RDBMS được gọi là client (máy khách). Mỗi khi chúng cần truy cập dữ liệu, chúng kết nối tới máy chủ (server) RDBMS. Cách thức này chính là mô hình “client-server”.
Tiếp theo cta có khái niệm MySQL server. MySQL Server là máy tính hay một hệ các máy tính cài đặt phần mềm MySQL dành cho server để giúp bạn lưu trữ dữ liệu trên đó, để máy khách có thể truy cập vào quản lý. Dữ liệu này được đặt trong các bảng, và các bảng có mối liên hệ với nhau. MySQL server nhanh, an toàn, đáng tin cậy. Phần mềm MySQL cũng miễn phí và được phát triển, phân phối và hỗ trợ bởi Oracle Corporation.
Từ đầu tới giờ cta nhắc tới MySQL khá nhiều vậy thì SQL có nghĩa là gì? MySQL và SQL không giống nhau. Hãy nhớ, MySQL là một trong các phần mềm RDBMS, hoạt động theo mô hình client-server. Nhưng, làm thế nào clietn và server liên lạc với nhau trong môi trường của RDBMS? Chúng sử dụng ngôn ngữ truy vấn có cấu trúc chung – Structured Query Language (SQL).
## II.MySQL hoạt động ntn? <a name="2"></a>
Qua những phần tôi vừa liệt kê cta đã có cái nhìn khái quát về MySQL vậy thì bây giờ hãy cùng nhau tìm hiểu MySQL hoạt dộng ntn?
<img src="https://www.hostinger.vn/huong-dan/wp-content/uploads/sites/10/2019/05/mysql-hoat-dong-nhu-the-nao.jpg">
## 1.Cách vận hành cơ bản
Bạn có thể thấy hình ảnh trên giải thích cấu trúc cơ bản về việc giao tiếp giữa client-server model. Một máy client sẽ liên lạc với máy server trong một mạng nhất định. Mỗi client có thể gửi một request từ giao diện người dùng (Graphical user interface – GUI) trên màn hình, và server sẽ trả về kết quả như mong muốn. Miễn là cả hai hiểu nhau
Để giải thích cặn kẽ hơn MySQL hoạt động từng bước ntn hãy nhìn vào hình ảnh sau đây :
<img src="https://www.researchgate.net/profile/Nihal_Dindar/publication/228888034/figure/fig7/AS:300683292102667@1448699891986/High-level-view-of-MySQL-modules9.png">
## 2.Cụ thể từng bước hoạt dộng
Để hiểu rõ hơn về kiến trúc MySQL, hãy để chúng tôi giải thích việc thực thi một truy vấn. Bất cứ khi nào Máy chủ MySQL được khởi động, Mô-đun Khởi tạo Máy chủ sẽ thiết lập máy chủ bằng cách khởi tạo các biến và cấu trúc toàn cục, cấp phát bộ đệm bộ nhớ chung và thực hiện một số tác vụ khởi động khác. Sau khi khởi tạo xong, nó sẽ chuyển quyền điều khiển cho Trình quản lý kết nối.

1.Đầu tiên trình quản lý kết nối xử lý các tác vụ giao thức truyền thông và chờ các yêu cầu của khách hàng. Bất cứ khi nào nó nhận được yêu cầu từ khách hàng, mô-đun Trình quản lý luồng sẽ tạo một luồng mới hoặc lấy một luồng từ bộ nhớ đệm để xử lý yêu cầu. Luồng kết nối, chịu trách nhiệm cho yêu cầu, trước tiên kết nối với Mô-đun người dùng để kiểm tra xác thực của người dùng.

2.Nếu người dùng được xác minh, yêu cầu sẽ được chuyển tiếp đến bộ điều phối chỉ huy. Lúc này bộ điều phối chỉ huy sẽ thực hiện tìm kiếm trong bộ lưu trữ của nhật ký truy vấn xem có tốn tại truy vấn nào tương tự không nếu còn thì nó sẽ xem kết quả của truy vấn trong nhật ký đó và ngay lập tức trả về kết quả cho người dùng (đoạn này bạn cần phải hiểu rằng trên 1 server sẽ có rất nhiều client truy cập và thực hiện truy vấn vậy công việc tghi lại các truy vấn này nhằm phục vụ cho việc có nhiều client truy cập và cùng thực hiện 1 truy vấn giống nhau khi đó cta đã thực hiện ghi lại truy vấn đó và lưu trữ kết quả thì hệ thông sẽ có ngay kết quả trả về chứ ko cần thực hiện lại truy vấn 1 lần nữa qua đó giảm tải đc chi phí cũng như nâng cao hiệu suất hoạt dộng của hệ thông tuy nhiên các truy vấn đc ghi lại này sẽ ko tồn tại được lâu vì dữ liệu trên hệ thống thường xuyên đc cập nhật hoặc thay đổi vì vậy các kết quả đuợc lưu trên sẽ bị cũ và ko đúng hoặc ko đủ vậy nên hệ thống sẽ chỉ lưu trữ 1 tgian rồi sau đó sẽ đc down xuống và sẵn sàng ghi lại cho lần truy vấn mới) vậy khi không có kết quả được lưu trên nhật kí thì dựa trên chế độ ghi nhật ký, Commander Dispatcher yêu cầu Mô-đun ghi nhật ký ghi truy vấn trước khi xử lý.

3.Sau đó, Bộ điều phối chỉ huy chuyển tiếp các truy vấn đến Bộ phân tích cú pháp thông qua Mô-đun bộ nhớ đệm truy vấn. Trong khi phân tích cú pháp truy vấn, trình phân tích cú pháp cũng tạo cấu trúc bên trong của truy vấn và chuyển tiếp truy vấn tới các mô-đun khác nhau dựa trên loại của nó. Như có thể thấy từ Hình trên, các truy vấn SELECT được chuyển tiếp đến Trình tối ưu hóa (cập nhật, chèn, xóa, tạo bảng và thay đổi bảng được chuyển tiếp đến Mô-đun sửa đổi bảng); các truy vấn duy trì bảng như sao lưu, sửa chữa, khôi phục được chuyển tiếp đến Mô-đun bảo trì bảng; các truy vấn liên quan đến bản sao được gửi đến Mô-đun nhân bản; và các truy vấn về cấu hình máy chủ, thông tin cấu trúc bảng, v.v. được gửi đến Mô-đun Báo cáo Trạng thái.

4.Chúng tôi sẽ tập trung vào việc thực hiện truy vấn SELECT được chuyển tiếp đến mô-đun Trình tối ưu hóa. Mặc dù tên của nó là Trình tối ưu hóa, nhưng mô-đun.

5.Trình tối ưu hóa còn làm được nhiều hơn thế. Mô-đun này chịu trách nhiệm thực hiện toàn bộ các truy vấn SELECT. Mỗi mô-đun này cần truy cập vào danh sách các bảng được chuyển qua mô-đun Phân tích cú pháp.

6.Tiếp theo đó, chúng kết nối với Mô-đun Kiểm soát Truy cập. Mô-đun kiểm soát truy cập kiểm tra xem người dùng có các quyền cần thiết để truy cập vào dữ liệu cần thiết cho truy vấn hay không.

7.Nếu người dùng có các đặc quyền cần thiết, thì Mô-đun quản lý bảng sẽ mở bảng và nhận các khóa cần thiết.

8.Từ bây giờ, công cụ lưu trữ có thể được sử dụng để thực hiện các tác vụ dữ liệu cấp thấp như chèn, cập nhật, tìm nạp dữ liệu.

9.Vì mục đích này, quyền kiểm soát được chuyển đến Mô-đun Công cụ Lưu trữ Tóm tắt. Như đã nêu trước đây, MySQL hỗ trợ kiến ​​trúc công cụ lưu trữ có thể cắm được. Mô-đun công cụ lưu trữ trừu tượng gọi công cụ lưu trữ được chỉ định bằng cách sử dụng tính đa hình. Do đó, module này có thể được coi là giao diện giữa MySQL và các bộ máy lưu trữ khác. Trong khi truy vấn được xử lý, kết quả có thể được gửi đến người dùng. Khi truy vấn được thực hiện xong, điều khiển lại chuyển đến Chuỗi kết nối. Luồng kết nối thực hiện dọn dẹp và đợi các truy vấn tiếp theo từ người dùng cho đến khi người dùng thoát. Luồng thực thi của các yêu cầu khách hàng không thường xuyên như nô lệ sao chép bị bỏ qua, vì những yêu cầu này nằm ngoài phạm vi của điều này

Vậy thì các công cụ lưu trữ mà cta vừa nhắc tới bên trên có nghĩa là gì cta sẽ timg hiểu ngay sau đây qua phần Storage Engine
## III.Storage Engine <a name="3"></a>
Đầu tiên cần phải hiểu được Storage Engine là gì? Rất đơn giản Storage Engine cơ bản chỉ là cách lưu trữ dữ liệu trên hệ thống MySQL.
Hiện nay có rất nhiều loại Storage Engine nhưng cta sẽ chỉ đi vào tìm hiểu về các loại phổ biến thôi nhé!
### 1.MyISAM
Đây là một Storage Engine mặc định và được sử dụng phổ biến nhất. - Ưu điểm Engine duy nhất hỗ trợ Full Text Search lập chỉ mục toàn văn, cung cấp thuật toán tìm kiếm khá giống Google. Kiến trúc đơn giản nên có tốc độ truy suất (đọc và tìm kiếm) nhanh nhất trong các loại Storage Engine. - Nhược điểm MyISAM hoạt động theo cơ chế Table Level Locking, nên khi có hành động thực hiện (thêm/sửa/xóa) 1 bản ghi nào đó trong table thì table đó sẽ bị khóa lại, chờ tới khi hành động này được thực hiện xong thì hành động kia mới tiếp tục được thực hiện. Kiến trúc đơn giản, không ràng buộc nên loại Storage Engine này rất dễ bị crash, hỏng chỉ mục với những table có số lượng bản ghi lớn.
### 2.InnoDB
Đây là Storage Engine mới hơn có nhiều tính năng và ưu điểm vượt trội hơn so với MyISAM. - Ưu điểm Engine này kiểm tra tính toàn vẹn và ràng buộc dữ liệu rất cao, khó xảy ra tình trạng hỏng chỉ mục và crash table. Hoạt động theo cơ chế Row Level Locking, vì vậy trong lúc thực hiện các hành động (thêm/sửa/xóa) trên 1 bản ghi, thì các hoạt động ở bản ghi khác trên table vẫn diễn ra bình thường. Hỗ trợ Transaction giúp đảm bảo an toàn khi thực hiện một khối lệnh SQL đảm bảo nhất quán dữ liệu. - Nhược điểm Hoạt động cần nhiều RAM hơn, nhưng nếu so sánh với MyISAM trong trường hợp tần suất Insert/Update/Delete lớn thì có khi sẽ lớn hơn vì cơ chế Table Level Locking sẽ gây ra hàng đợi lớn, gây chậm quá trình xử lý.(Đây là loại storage engine hay được sử dụng nhất hiện nay vì nó đảm bảo tính an toàn cũng như mối liên kết giữa các dữ liệu trên hệ thống).
### 3.Memory
Đặc điểm
Còn được gọi là HEAP tables.
Lưu trữ
Tất cả dữ liệu đều nằm trên memory.

Tính năng:
Sau khi server restart, cấu trúc bảng được bảo toàn, dữ liệu bị mất hết.
Memory engine sử dụng HASH index nên rất nhanh cho query lookup.
Memory engine dùng table-level locking do vậy tính concurrency không cao.

(thường được sử dụng để lưu trữ những dữ liệu tạm thời ví dụ khi bạn cần lưu quá nhiều thứ gì đó nhưng có thể sau này bạn ko cần nữa bạn nên sử dụng storage engin này vì sau khi bạn ko dùng nữa bạn chỉ cần thực hiện restart lại dữ liệu sẽ được giải phóng mà ko cần phải xóa)

Qua những phần vừa nêu trên có lẽ các bạn cũng đã thấy đc các loại Storage Engine khác nhau ntn rồi phải ko? tới đây cũng kết thúc phần giới thiệu về MySQL rồi :)))
