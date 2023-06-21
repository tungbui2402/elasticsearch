# Elastic search
## I. Khái niệm
Elasticsearch là một hệ thống tìm kiếm và phân tích dữ liệu phân tán mã nguồn mở. Nó được thiết kế để tìm kiếm, lưu trữ và phân tích các tập dữ liệu lớn một cách hiệu quả và nhanh chóng. Elasticsearch được xây dựng trên nền tảng Apache Lucene, một thư viện tìm kiếm thông tin mạnh mẽ.

Elasticsearch có khả năng xử lý dữ liệu phân tán trên nhiều nút trong một cụm máy chủ, cho phép tăng khả năng mở rộng và đảm bảo sẵn sàng cao. Nó hỗ trợ nhiều tính năng như tìm kiếm full-text, tìm kiếm địa lý, phân tích dữ liệu và thống kê, khám phá dữ liệu, và xử lý dữ liệu theo thời gian thực.

Elasticsearch cung cấp một API RESTful để tương tác với hệ thống, cho phép người dùng truy vấn dữ liệu, lưu trữ và cập nhật thông qua HTTP. Nó cũng tích hợp tốt với các công cụ và framework phổ biến như Logstash và Kibana, tạo thành một bộ công cụ đầy đủ cho việc thu thập, xử lý và hiển thị dữ liệu.

Elasticsearch thường được sử dụng trong các ứng dụng web, hệ thống log và giám sát, các ứng dụng phân tích dữ liệu, và nhiều lĩnh vực khác đòi hỏi xử lý và tìm kiếm dữ liệu nhanh chóng và mở rộng.

## II. Elastic clutcher
### 1. Khái niệm
Elasticsearch Cluster là một tập hợp các nút Elasticsearch hoạt động cùng nhau để cung cấp khả năng lưu trữ, xử lý và tìm kiếm dữ liệu phân tán. Cluster Elasticsearch giúp nâng cao khả năng mở rộng, đáng tin cậy và hiệu suất của hệ thống.

Một Elasticsearch Cluster bao gồm ít nhất một nút master và một hoặc nhiều nút dữ liệu. Nút master được chọn để quản lý và điều phối các hoạt động trong cluster, trong khi nút dữ liệu chịu trách nhiệm lưu trữ và xử lý dữ liệu. Các nút dữ liệu chia sẻ dữ liệu và công việc xử lý, cho phép tìm kiếm và truy vấn dữ liệu phân tán.

Các nút trong cluster Elasticsearch giao tiếp với nhau thông qua giao thức phân tán, thường là thông qua giao thức TCP/IP. Các nút trao đổi thông tin về trạng thái, dữ liệu và các hoạt động tìm kiếm, đồng bộ hóa dữ liệu và phối hợp công việc. Việc phân phối dữ liệu và công việc trên các nút trong cluster giúp cải thiện hiệu suất và đảm bảo tính sẵn sàng.

### 2. Lợi ích của Elasticsearch Cluster
- Mở rộng: Bạn có thể thêm mới các nút dữ liệu vào cluster để mở rộng khả năng lưu trữ và xử lý dữ liệu. Elasticsearch tự động phân phối dữ liệu trên các nút để tận dụng tối đa khả năng mở rộng.
- Đáng tin cậy: Dữ liệu trong cluster Elasticsearch được sao chép và phân tán trên các nút, đảm bảo tính sẵn sàng và bảo vệ dữ liệu khỏi mất mát khi có sự cố xảy ra.
- Hiệu suất: Với việc phân phối công việc và dữ liệu, Elasticsearch Cluster cung cấp khả năng xử lý và tìm kiếm dữ liệu nhanh chóng. Tìm kiếm trên toàn bộ cluster cho phép phân tán công việc và giảm thời gian đáp ứng.
- Quản lý tập trung: Các công cụ và giao diện quản lý Elasticsearch cho phép bạn giám sát và quản lý toàn bộ cluster từ một vị trí tập trung. Bạn có thể theo dõi trạng thái, thống kê và xử lý sự cố trong cluster một cách thuận tiện.

### 3. Mô hình cluster
Elasticsearch hỗ trợ một số mô hình cluster khác nhau để tổ chức và quản lý các nút máy chủ Elasticsearch trong một cụm.
- Single-Node Cluster: Đây là một mô hình đơn giản với một nút Elasticsearch duy nhất trong cluster. Mô hình này thích hợp cho các môi trường phát triển hoặc thử nghiệm nhỏ, tuy nhiên, không cung cấp khả năng mở rộng và đáng tin cậy.
- Multi-Node Cluster: Mô hình này bao gồm nhiều nút Elasticsearch hoạt động cùng nhau trong một cluster. Các nút trong cluster có thể có vai trò khác nhau, bao gồm nút master và nút dữ liệu. Nút master chịu trách nhiệm quản lý cluster, trong khi nút dữ liệu lưu trữ và xử lý dữ liệu. Mô hình này cung cấp khả năng mở rộng và đáng tin cậy.
- Master-Node Cluster: Mô hình này tách riêng nút master và nút dữ liệu thành hai loại nút riêng biệt. Các nút master chỉ chịu trách nhiệm quản lý cluster và không lưu trữ dữ liệu. Các nút dữ liệu chịu trách nhiệm lưu trữ và xử lý dữ liệu. Mô hình này giúp tách biệt trách nhiệm và cải thiện tính sẵn sàng của cluster.
- Dedicated Master Nodes: Trong mô hình này, các nút master được chọn đặc biệt chỉ để làm nút master và không tham gia lưu trữ dữ liệu. Điều này giúp tăng khả năng xử lý và đáng tin cậy của cluster.
- Coordinating-Only Nodes: Mô hình này tách riêng nút chỉ chịu trách nhiệm điều phối hoạt động truy vấn và không lưu trữ dữ liệu. Các nút này được sử dụng để giảm tải và cải thiện hiệu suất cho các hoạt động truy vấn.
## III. Setup
Cập nhật các gói hệ thống
`sudo apt update`

Cài đặt gói apt-transport-https để truy cập kho lưu trữ qua HTTPS
` sudo apt install apt-transport-https`

Cài đặt OpenJDK 11 trên Ubuntu
`sudo apt install openjdk-11-jdk`

Kiểm tra phiên bản java
`java --version`

Để xác định biến môi trường, hãy mở tệp bên dưới:
`sudo nano /etc/environment`

Dán biến dưới đây vào tệp:
`Java_HOME="/usr/lib/jvm/java-11-openjdk-amd64"`

Tải biến môi trường bằng lệnh bên dưới
`source /etc/environment`

Xác minh biến Java_HOME
`echo $JAVA_HOME`

Tải xuống và cài đặt khóa ký công khai
```
wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo gpg --dearmor -o /usr/share/keyrings/elasticsearch-keyring.gpg
```

Lưu định nghĩa kho lưu trữ vào /etc/apt/sources.list.d/elastic-8.x.list:
```
echo "deb [signed-by=/usr/share/keyrings/elasticsearch-keyring.gpg] https://artifacts.elastic.co/packages/8.x/apt stable main" | sudo tee /etc/apt/sources.list.d/elastic-8.x.list
```

Cài đặt Elaticsearch bằng lệnh bên dưới:
```
sudo apt-get update
sudo apt-get install elasticsearch
```

Chạy, bắt đầu trạng thái elasticsearch
```
sudo systemctl start elasticsearch
sudo systemctl enable elasticsearch
sudo systemctl status elasticsearch
```

Thực hiện các thay đổi trong tệp cấu hình `sudo nano /etc/elasticsearch/elasticsearch.yml`

Chuyển đến phần Mạng và bỏ ghi chú network.host và thay thế IP hệ thống bằng
```
network.host: 0.0.0.0
discovery.seed_hosts: [ ]
```
Sau đó, bước thứ hai là đi tới BEGIN SECURITY AUTO CONFIGURATION và ở đây cần thay thế true bằng false như hiển thị bên dưới: 

`Error: elasticsearch “curl: (52) Empty reply from server” on port 9200`

Kéo xuống dưới và tìm đến dòng `xpack.security.enabled` và đổi từ true về thành false

Kiểm tra Elaticsearch bằng lệnh curl bằng cách gửi yêu cầu HTTP: 
`curl -X GET "localhost:9200"`

Truy cập bằng trình duyệt: `ip:9200`
