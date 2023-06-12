### ログイン
```sql
cd C:\\Program Files\\MySQL\\MySQL Server 8.0\\bin
mysql -u r4a105 -p
password
use r4a105
```
rootで以下を実行する
```sql
CREATE USER 'r4a105'@'localhost' IDENTIFIED BY 'password';
SHOW GRANTS FOR 'r4a105'@'localhost';
GRANT ALL PRIVILEGES ON *.* TO 'r4a105'@'localhost';
FLUSH PRIVILEGES;
SHOW GRANTS FOR 'r4a105'@'localhost';
```
SQLでテーブル一覧を確認
```sql
SHOW TABLES;
```
テーブルの中身を確認
```sql
SELECT * FROM employee;
```
削除
```sql
DELETE FROM employee WHERE empid = '0001';
```
データベース作成
```sql
CREATE DATABASE r4a105;
```
### テーブル作成
他病院表
```sql
CREATE TABLE tabyouin(
tabyouinid varchar(8) NOT NULL,
tabyouinmei varchar(64) NOT NULL,
tabyouinaddres varchar(64) NOT NULL,
tabyouintel varchar(13) NOT NULL,
tabyouinshihonkin int NOT NULL,
kyukyu int NOT NULL,
PRIMARY KEY(tabyouinid));
```
従業員表
```sql
CREATE TABLE employee(
empid varchar(8) NOT NULL,
empfname varchar(64) NOT NULL,
emplname varchar(64) NOT NULL,
emppasswd varchar(256) NOT NULL,
emprole int NOT NULL,
PRIMARY KEY(empid));
```
患者表
```sql
CREATE TABLE patient(
patid varchar(8) NOT NULL,
patfname varchar(64) NOT NULL,
patlname varchar(64) NOT NULL,
hokenmei varchar(64) NOT NULL,
hokenexp date NOT NULL,
PRIMARY KEY(patid));
```
薬剤表
```sql
CREATE TABLE medicine(
medicineid varchar(8) NOT NULL,
medicinename varchar(64) NOT NULL,
unit varchar(8) NOT NULL,
PRIMARY KEY(medicineid));
```
処置表
```sql
CREATE TABLE treatment(
patid varchar(8) NOT NULL,
medicineid varchar(8) NOT NULL,
quantity int NOT NULL,
impdate date NOT NULL,
FOREIGN KEY (patid) REFERENCES patient (patid),
FOREIGN KEY (medicineid) REFERENCES medicine (medicineid));
```

### テーブル内容追加
```sql
INSERT INTO employee VALUES('0000','亮','内海','3332b49af1871df18abf9c3616c4cea2b8953f1565a7e257fe06403f7d2ff573',0);
INSERT INTO employee VALUES('0000','亮','内海','0000',0);

INSERT INTO medicine VALUES('0001','オロナイン','塗り');
INSERT INTO medicine VALUES('0002','バンドエイド','枚');
INSERT INTO medicine VALUES('0003','湿布','枚');
```