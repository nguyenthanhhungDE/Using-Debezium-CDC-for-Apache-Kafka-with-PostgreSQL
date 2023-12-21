# Using Debezium, CDC for Apache Kafka, with PostgreSQL
- What is CDC and Debezium?
- Kafka, Kafka Connect và Kafka Connector
Kafka: Kafka là một công nghệ truyền dữ liệu phân tán (distributed messaging system) theo mô hình truyền thông public-subscribe, bên truyền dữ liệu được gọi là producer bên subscribe nhận dữ liệu theo các topic được gọi là consumer. Kafka có khả năng truyền một lượng lớn dữ liệu tuy nhiên trong trường hợp khi consumer chưa nhận, dữ liệu vẫn được lưu trữ sao lưu trên queue và cả trên ổ đĩa bảo đảm an toàn.
Kafka Connect: Kafka Connect là một thành phần của Kafka, dùng để kết nối Kafka với các hệ thống khác như các database, file system, key-value store... Kafka Connect Cluster sẽ tách biệt với Kafka cluster với mục đích để có thể scale các connector bên trong nó.
![image](https://github.com/nguyenthanhhungDE/Kafka-Spark-on-Docker/assets/134383281/824f0308-454b-4cf7-91f3-d71242ebd654)
Kafka Connector: Kafka Connector được thiết kế để chạy trong Kafka Connect Cluster, thành phần này sẽ được sử dụng để đọc dữ liệu từ các nguồn khác vào kafka topic hoặc đọc dữ liệu từ kafka topic gửi đến các nguồn khác.
- Debezium
Debezium: là một source connector của Kafka Connect có chức năng ghi nhận các sự thay đổi của database (Change Data Capture CDC). Với MySQL database, Debezium sẽ đọc được các sự thay đổi này thông qua binlog từ đó giảm thiểu tải lên server.
Debezium architecture:
DBMS (as a data source) → Kafka Connect connector → Apache Kafka → consumer
![image](https://github.com/nguyenthanhhungDE/Kafka-Spark-on-Docker/assets/134383281/830b1014-7f97-45fc-aa81-2a2c4bc3ef7e)

