
#####Mysql
===================
##HƯỚNG DẪN CÀI ĐẶT VÀ SỬ DỤNG MYSQL

### 1. HƯỚNG  DẪN CÀI ĐẶT :



- B1: chuyển sang quyền root :
```
sudo su
```
- B2: Cập nhật các Repository:
```
apt-get update -y
```
- B3: Cài đặt mysql-server bằng lệnh:
```
apt-get install mysql-server -y
```
- B4 : Quá trình cài đặt sẽ diễn ra trong ít phút. Trong quá trình cài đặt MySql sẽ yêu cầu nhập mật khẩu cho tài khoản mặc định root, đây là mật khẩu để kết nối đến MySql - See more at:

Kết thúc quá trình cài đặt.

###2.Các lệnh  cơ bản trong Mysql

####I.Các câu lệnh liên quan đên Database
1. Tao database: 
```
CREATE DATABASE <ten database>;
```
2.Chọn 1 database để sử dụng:
```
USE DATABASE;
```
3.Xóa một database: 
```
DROP DATABASE <tên database>;
```
4.Hiển thị các database:
```
SHOW DATABASE;
```
####II. Các lệnh liên quan đến bảng:

1.Hiển thị thông tin các bảng trong database: 
```
   SHOW TABLES;
```
2.Tạo 1 bảng:
```
CREATE TABLE <tên bảng>;
```
3.Nhập data vào table: 
```
INSERT INTO [TEN TABLE](cột 1, cột 2,...) VALUES (gicột 1,gi côt 2...);
```
4.Lấy thông tin từ bảng: 
```
SELECT {Tên cột muốn hiển thị} FROM {Tên bảng} [WHERE {Điều kiện}];
```
5.Cập nhật thông tin cho các bảng: 
 ````
 UPDATE [Tên TABLE] SET [cột muốn sửa] [Where {Điều kiện}];
```
6.Xóa TABLE :
```
DROP Table <Tên table>;
```
#### III.Các lệnh về User: 
1.Tạo user:
```
  CREATE USER <tên user>;
```
2. Đặt password cho user: 
```
SET PASSWORD FOR <Tên user>=PASSWORD('password');
```
3.Gán quyền cho user:
```
  GRANT [quyền] ON [tên database].[tên table] TO '[user]'@'localhost';
```
- các  quyền  hạn trong mysql:
```
    ALL PRIVILEGES- tất cả quyền trên hệ thống
    CREATE- cho phép tạo database và table
    DROP- cho phép xóa database hoặc table
    DELETE- cho phép xóa các record trong table
    INSERT- cho phép thêm record trong table
    SELECT-cho phép thực hiện lệnh SELECT để query dữ liệu
    UPDATE- cho phép cập nhật record trong table
    GRANT OPTION- cho phép thực hiện tác vụ phân quyền cho user khác
```
- Để quyền có hiệu lực cần thực hiện lệnh sau:
```
FLUSH PRIVILEGES;
```
-Xóa  quyền :

```
  REVOKE [quyền] ON [tên database].[tên table] TO '[user]'@'localhost';
````

3. Ví dụ:


BAI 1:
```
mysql> CREATE DATABASE KTX;

mysql> USE KTX;

mysql> SHOW TABLE;
mysql> CREATE TABLE KHUVUC(
-> IDKHUVUC VARCHAR(20)
-> TENKHUVUC VARCHAR(30)
-> PhongQL VARCHAR(10);
-> PRIMARY KEY (IDKHUCVUC)
->);

mysql> CREATE TABLE DAY(
-> STTDay int ,
-> IDKHUVUC VARCHAR(20),
-> TEN VARCHAR(30),
-> PHONGbv VARCHAR(10),
-> PRIMARY KEY (STTDay),
-> FOREIGN KEY (IDKHUVUC) REFERENCE KHUVUC(IDKHUVUC)
->)
->;
mysql> CREATE TABLE PHONG
-> (
-> IDKHUVUC VARCHAR(20),
-> IDPHONG VARCHAR(10),
-> STTDay INT,
-> SucChua INT,
-> PHONGtb VARCHAR(10),
-> PRIMARY KEY (IDPHONG),
-> CONSTRAINT KEY_1 FOREIGN KEY (IDKHUVUC) REFERENCES KHUVUC(IDKHUVUC),
-> CONSTRAINT KEY_2 FOREIGN KEY (STTDay) REFERENCES DAY(STTDay)
-> )
-> ;
Query OK, 0 rows affected (0.08 sec)

mysql> SHOW TABLES;
+---------------+
| Tables_in_KTX |
+---------------+
| DAY |
| KHUVUC |
| PHONG |
+---------------+
3 rows in set (0.00 sec)

mysql> INSERT INTO KHUVUC VALUES ('2','KHU_VUC_2','PHONG2');
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO KHUVUC VALUES ('3','KHU_VUC_3','PHONG3');
Query OK, 1 row affected (0.11 sec)

mysql> INSERT INTO DAY VALUES ('1','1','DAY_1','1');
Query OK, 1 row affected (0.03 sec)

mysql> INSERT INTO DAY VALUES ('2','2','DAY_2','2');
Query OK, 1 row affected (0.01 sec)

mysql> INSERT INTO DAY VALUES ('3','3','DAY_3','3');
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO PHONG VALUES ('1','1','1','10','PHONG_1');
Query OK, 1 row affected (0.06 sec)

mysql> INSERT INTO PHONG VALUES ('2','2','2','10','PHONG_2');
Query OK, 1 row affected (0.05 sec)
````
