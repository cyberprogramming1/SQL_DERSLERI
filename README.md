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

-- Delete command
DELETE from employees where department ='hr'
/*
delete command table olan rows one by one method ile silir . yeni funksiyalligdan istifade ederek.
*/

-- Truncate command

truncate table employees;
/*
bu command ise table olan butun rows birge silir
*/

-- Drop command
drop table employees;
drop database baslangic;

/*
drop command ise table ozu hemcinin yaratdigimiz database ozunu silmek ucun istifade olunur
*/



-- table yaratmaq , adini deyismek, silmek . 
