#  SQL Dersleri :


SQL (Structured Query Language) — Verilənlər bazasında saxlanan məlumatlarla 
işləmək üçün istifadə olunan xüsusi bir dildir.
Məsələn, sən bir cədvəldə adlar, telefon nömrələri və ünvanlar saxlayırsansa, SQL vasitəsilə bunları:
•	Əlavə edə bilərsən
•	Seçə bilərsən
•	Dəyişə bilərsən
•	Silə bilərsən




# SQL Server Download :
https://go.microsoft.com/fwlink/p/?linkid=2215158&clcid=0x409&culture=en-us&country=us

/*
Download steps : 
1. File explore hissesinde download kecid edirik , yuklenen .exe file’nin uzerine 2 defe click edirik . 
2. Acilan pencerede BASIC hissesine click edib license accept edirik. 
3. Install edirik.
*/

# SQL server management studio yuklemek :
/*
Note : bu yuklediyimiz , senin sql codes, yeni database qurulmasi ucun istifade edeceyin enviroment’dir (yeni muhit)
*/

https://go.microsoft.com/fwlink/?linkid=2257624&clcid=0x409  (bu versiya 19)
<br>
https://go.microsoft.com/fwlink/?linkid=2313753&clcid=0x409  (bu versiya 20)




# Database yaratmaq
```bash 
create DATABASE ILK_ders;
```

# Database silmek 
```bash
drop database ILK_ders;
```


# Note :
eger biz database sildiyimiz zaman onun daxilinde islek veziyyetde oluruqsa onda bize error mesaj cixardacaq
onu hell elemek ucun biz master database kecid elemeliyik.
```bash
use master ;
go ;
drop database ILK_ders;
```

# database adini deyismek .
```bash
exec sp_renamedb 'ILK_ders', 'baslangic';
```
# note :
neticede database adini baslangic olaraq deyisdirdik

# Comment nedir:
Sql 'de 2 cur comment var. 
1. --  (ancaq 1 setirlik informasiya yada qeyd elave etmek ucun istifade olunur)
2. /**/  (daha cox informasiya elave etmek ucun istifade olunur)


# silmek commands ve ferqleri .

1. Delete command
```bash
DELETE from employees where department ='hr'
```
delete command table olan rows(yeni setirleri) one by one method ile silir . yeni funksiyalligdan istifade ederek.

2. Truncate command
```bash
truncate table employees;
```
bu command ise table olan butun rows birge silir

3. Drop command
```bash
drop table employees;
drop database baslangic;
```
drop command ise table ozu hemcinin yaratdigimiz database ozunu silmek ucun istifade olunur

#  table yaratmaq , adini deyismek, silmek . 
```bash
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    column3 datatype,
   ....
);
```
1. Note : datatype ne demekdir ?
table ( cedvel) yaradarken her bir columns(sutunlar) oz daxilinde hansi nov datas(melumatlari) saxlayacaq. onlarin
novlerini ( yeni types) teyin etmek ucun istifade olunur.

✅ 1. INT
Tam ədəd (−2 milyarddan +2 milyarda qədər).
Nümunə: yaş, say.
```bash
CREATE TABLE Users (
    UserID INT,
    Age INT
);

INSERT INTO Users (UserID, Age)
VALUES (1, 25);
```
✅ 2. BIGINT
Çox böyük tam ədəd (64-bit).
Nümunə: əhali, böyük ID-lər.
```bash
CREATE TABLE PopulationStats (
    Country VARCHAR(50),
    Population BIGINT
);

INSERT INTO PopulationStats (Country, Population)
VALUES ('India', 1400000000);

```
✅ 3. DECIMAL(p, s) / NUMERIC(p, s)
Dəqiq onluq ədəd. p – ümumi rəqəm, s – onluq hissə.
Nümunə: qiymət, pul.
```bash
CREATE TABLE Products (
    ProductName VARCHAR(50),
    Price DECIMAL(10, 2)
);

INSERT INTO Products (ProductName, Price)
VALUES ('Laptop', 1299.99);

```
✅ 4. FLOAT
Təxmini onluq ədəd (real ədəd).
Nümunə: temperatur, faiz.
```bash
CREATE TABLE Sensors (
    SensorID INT,
    Temperature FLOAT
);

INSERT INTO Sensors (SensorID, Temperature)
VALUES (1, 36.75);

```
✅ 5. BIT
Boolean – 0 və ya 1.
Nümunə: aktiv/passiv, doğru/səhv.
```bash
CREATE TABLE Accounts (
    Username VARCHAR(50),
    IsActive BIT
);

INSERT INTO Accounts (Username, IsActive)
VALUES ('Raul', 1);

```
✅ 6. CHAR(n)
Sabit uzunluqlu mətn.
Nümunə: ISO kodu, bərabər uzunluqlu dəyərlər.
```bash
CREATE TABLE Countries (
    CountryCode CHAR(2),
    Name VARCHAR(50)
);

INSERT INTO Countries (CountryCode, Name)
VALUES ('AZ', 'Azerbaijan');

```
✅ 7. VARCHAR(n)
Dəyişən uzunluqlu mətn.
Nümunə: ad, email, ünvan.
```bash
CREATE TABLE Emails (
    UserID INT,
    Email VARCHAR(100)
);

INSERT INTO Emails (UserID, Email)
VALUES (1, 'raul@example.com');
```
✅ 8. TEXT (köhnə)  
Çox uzun mətn (2GB-a qədər).
Nümunə: məqalə, təsvir.<br>
Amma yenilərdə VARCHAR(MAX) daha çox tövsiyə olunur.
```bash
CREATE TABLE BlogPosts (
    Title VARCHAR(100),
    Content TEXT
);

INSERT INTO BlogPosts (Title, Content)
VALUES ('MSSQL Nümunələri', 'Bu gün SQL data typelərini öyrəndik...');

```

✅ 9. DATE
Yalnız tarix (YYYY-MM-DD).
Nümunə: doğum tarixi.
```bash
CREATE TABLE Employees (
    Name VARCHAR(50),
    BirthDate DATE
);

INSERT INTO Employees (Name, BirthDate)
VALUES ('Aynura', '1998-04-15');
```
✅ 10. DATETIME
Tarix və vaxt birlikdə (YYYY-MM-DD hh:mm:ss).
Nümunə: qeydiyyat tarixi.
```bash
CREATE TABLE Logins (
    Username VARCHAR(50),
    LoginTime DATETIME
);

INSERT INTO Logins (Username, LoginTime)
VALUES ('Raul', '2025-07-17 20:30:00');

```

# SQL alter table statement 

1. ALTER TABLE => mövcud cədvəldə sütunları əlavə etmək, silmək və ya dəyişdirmək üçün istifadə olunur.<br>
2. ALTER TABLE => həmçinin mövcud cədvələ müxtəlif məhdudiyyətlər əlavə etmək və buraxmaq üçün istifadə olunur.
```bash
ALTER TABLE table_name
ADD column_name datatype;
```
table'dan her hansi bir column'u(sutunu) silmek ucun . 
```bash
ALTER TABLE table_name
DROP COLUMN column_name;
```
Cədvəldəki sütunun adını dəyişmək üçün.
```bash
ALTER TABLE table_name
RENAME COLUMN old_name to new_name;
```
SQL Serverdə cədvəldəki sütunun adını dəyişmək üçün aşağıdakı sintaksisdən istifadə edin:
```bash
EXEC sp_rename 'table_name.old_name',  'new_name', 'COLUMN';
```
Cədvəldəki sütunun məlumat növünü (data type) dəyişdirmək üçün
```bash
ALTER TABLE table_name
ALTER COLUMN column_name datatype;
```

# Cedvele nece data'lari elave etmek lazimdir.
``` bash
insert into table_name values ('','','');
```
1. Note : eyni anda daha cox melumat elave ede bilersen.
```bash 
insert into table_name values ('','',''),('','',''),('','',''),('','',''),('','','')
```
# Cedveldeki melumatlarin redakte edilmesi .
Update - movcud datanin yeniden redakte edilmesidir. update method esasen 'Identity' ye gore aparilir.
```bash
CREATE TABLE Users (
    UserID INT,
    Name VARCHAR(50),
    Age INT
);

INSERT INTO Users (UserID, Name, Age)
VALUES (1, 'Raul', 25);
```
İndi adını və yaşını dəyişmək istəyirsənsə:
```bash
UPDATE Users
SET Name = 'Raul Yarmemmedov', Age = 26
WHERE UserID = 1;
```

# Primary Key nedir ve identity(1,1) nedir ?
primary key - cedvel yaradanda bize lazim olan ID'lerin (tek) yeni unique olmasidir. bu prosesi sql'de 
tesdiq eden primary key sayilir. 

*Note : Primary Key - null (bos) ola bilmez. ve deyeri tek (unikal) olmalidir.

IDENTITY(1,1) — ise bizim qeyd etdiyimiz ID'lerin deyerlerini ardicillgini berpa etmesi ucundur. 
bu o deməkdir ki, UserID avtomatik olaraq 1-dən başlayacaq və hər yeni sətrə 1 artırılacaq şəkildə təyin olunacaq.
yazilis qaydasi asagidaki kimidir.

``` bash
UserID int identity(1,1) primary key ;
```


# char(n) ve varchar(n) ferqi nedir ?
char(n) = qeyd olunan character sayini sql'in yaddasinda yer ayrir , ve daxil etdiyimiz melumatin character sayini
nezere almadan eyni qeder yaddas saxlamis olur. onun ucun biz deqiq deyerleri olan melumat saxlamaliyiq.
meselen : FIN kod kimi . cunki hamida 7 character'den ibaretdir.

varchar(n) = ise char(n) ferqli olaraq daxil etdiyimiz melumatin character sayina gore hereket edir. artiq qalan hisseni oz yaddasindan silir. 
meselen : ad , soyad , email , olke adlari ve.s daxil etmek olar bu data type uzre.

# not null ve null ifadesi
* NULL – Boş dəyərdir, yəni məlumat verilməyib.
* NOT NULL – Mütləq məlumat verilməlidir, boş qala bilməz.
Misal:
```bash
Ad VARCHAR(50) NOT NULL → Ad yazmaq məcburidir.
Soyad VARCHAR(50) NULL → Soyad boş qala bilər.
```
# Default deyeri ne demekdir .
DEFAULT – Sütun üçün əvvəlcədən təyin olunmuş dəyərdir. İstifadəçi dəyər yazmasa, bu dəyər avtomatik yazılır.
Misal:
```bash
PageSize int default 50
```
Izah: yeni eger men pagesize her hansi bir deyer vermesem , onda automatik olaraq deyeri 50 qebul edecek.

# Table'dan melumatlari nece oxumaq olar.
Melumatlari oxumaq ucun select emrinden istifade etmek lazimdir, indi size butun alternativ variantlari gosterecem.

1. Bütün məlumatları oxumaq: Cədvəldəki bütün sətirləri və sütunları göstərir.
```bash
SELECT * FROM table_adi;
```
2. Yalnız istədiyin sütunları göstərir (məsələn: ad, soyad).
```bash
SELECT column1, column2 FROM table_adi;
```
3. Şərt ilə məlumatları oxumaq (WHERE)
```bash
SELECT * FROM table_adi WHERE column1 = 'deyer';
```
Məsələn: SELECT * FROM users WHERE city = 'Baku';

4. Sıralamaq (ORDER BY)
```bash
SELECT * FROM table_adi ORDER BY column1 ASC;  -- artan sıra
SELECT * FROM table_adi ORDER BY column1 DESC; -- azalan sıra
```
5. Məhdud sayda sətir göstərmək (LIMIT) = İlk 10 sətiri göstərir.
```bash
SELECT * FROM table_adi LIMIT 10;
```
6. Unikal dəyərləri almaq (DISTINCT) = Eyni olanları təkrarlamadan göstərir.
```bash
SELECT DISTINCT column1 FROM table_adi;
```
7. Şərtləri birləşdirmək (AND, OR)
```bash
SELECT * FROM table_adi WHERE column1 = 'x' AND column2 = 'y';
SELECT * FROM table_adi WHERE column1 = 'x' OR column2 = 'y';
```
8. Axtarış etmək (LIKE) = % – istənilən simvol sayı üçün istifadə olunur (wildcard).
```bash
SELECT * FROM table_adi WHERE column1 LIKE '%text%';
```
9. Aralıqda olan məlumatları seçmək (BETWEEN) 
Bu BETWEEN ifadəsi sətirləri müəyyən bir aralıqda olan dəyərlərə görə seçmək üçündür.
```bash
SELECT * FROM table_adi WHERE column1 BETWEEN 10 AND 50;
```
Gəlin bir real nümunəyə baxaq:
```bash
CREATE TABLE telebeler (
    ad VARCHAR(50),
    yas INT
);

-- Nümunə məlumatlar:
INSERT INTO telebeler (ad, yas) VALUES
('Murad', 18),
('Nihat', 22),
('Nurlan', 25),
('Cavid', 30),
('Raul', 35);

-- select sorgusu vasitesile ile istifade edeceyik
SELECT * FROM telebeler WHERE yas BETWEEN 20 AND 30;
```
*Note : burada yaratdigimiz cedvelden yalniz yasi 20-30 arasi olanlari gosterecek. (Nihat, Nurlan, Cavid)

