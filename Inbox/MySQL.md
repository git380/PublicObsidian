### ログイン
```sql
cd C:\\Program Files\\MySQL\\MySQL Server 8.0\\bin
mysql -u r4a105 -p
```
rootで以下を実行する
```sql
CREATE USER 'r4a105'@'localhost' IDENTIFIED BY 'password';
SHOW GRANTS FOR 'r4a105'@'localhost';
GRANT ALL PRIVILEGES ON *.* TO 'r4a105'@'localhost';
FLUSH PRIVILEGES;
SHOW GRANTS FOR 'r4a105'@'localhost';
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
仕入れ先表
```sql
CREATE TABLE shiiregyosha(
shiireid varchar(8) NOT NULL,
shiiremei varchar(64) NOT NULL,
shiireaddress varchar(64) NOT NULL,
shiiretel varchar(13) NOT NULL,
shihonkin int NOT NULL,
nouki int NOT NULL,
PRIMARY KEY(shiireid));
```
従業員表
```sql
CREATE TABLE employee(
empid varchar(8) NOT NULL,
empfname varchar(64) NOT NULL,
emplname varchar(64) NOT NULL,
emppasswd varchar(254) NOT NULL,
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
PRIMARY KEY(patid,medicineid,impdate),
FOREIGN KEY (patid) REFERENCES patient (patid),
FOREIGN KEY (medicineid) REFERENCES medicine (medicineid));
```

### テーブル内容追加
```sql
INSERT INTO shiiregyousha VALUES('0001','A社','A県A市A町A-A','AAA-AAA-AAA',8192,1);
INSERT INTO shiiregyousha VALUES('0002','B社','B県B市B町B-B','BBB-BBB-BBB',8192,1);
INSERT INTO shiiregyousha VALUES('0003','C社','C県C市C町C-C','CCC-CCC-CCC',8192,1);
INSERT INTO shiiregyousha VALUES('0004','D社','D県D市D町D-D','DDD-DDD-DDD',8192,1);

INSERT INTO employee VALUES('0000','亮','内海','0000',0);
INSERT INTO employee VALUES('0001','ヘウォン','オ','password',1);
INSERT INTO employee VALUES('0002','チョリョン','イ','password',1);
INSERT INTO employee VALUES('0003','ガウル','キム','password',1);
INSERT INTO employee VALUES('0004','ヘリン','カン','password',2);
INSERT INTO employee VALUES('0005','ハニ','パム','qwertyuioasdfghjklzxcvbnm',2);

INSERT INTO patient VALUES('0001','カンナ','橋本','0001','2050-08-07');
INSERT INTO patient VALUES('0002','アンナ','橋本','0002','2050-08-07');
INSERT INTO patient VALUES('0003','パンダ','橋本','0003','2050-08-07');
INSERT INTO patient VALUES('0004','ガンジャ','橋本','0004','2050-08-07');

INSERT INTO medicine VALUES('0001','オロナイン','塗り');
INSERT INTO medicine VALUES('0002','バンドエイド','枚');
INSERT INTO medicine VALUES('0003','湿布','枚');
INSERT INTO medicine VALUES('0004','目薬','滴');

INSERT INTO treatment VALUES('0001','0001',2,'2023-4-25');
INSERT INTO treatment VALUES('0001','0002',2,'2023-4-25');
INSERT INTO treatment VALUES('0001','0003',2,'2023-4-25');
INSERT INTO treatment VALUES('0002','0001',2,'2023-4-25');
```