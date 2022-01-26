## MSSQL ile veritabanı işlemleri #

- [](#Sayaç)
- [Sayaç](#Sayaç)
- [Sayaç](#Sayaç)
- [Sayaç](#Sayaç)
- [Sayaç](#Sayaç)
- [Sayaç](#Sayaç)





## Select sorgusu




```
  select * from tbl_Musteri
   
  select * from tbl_Musteri where Id = 6


```


## Create


```
      create table tbl_Kategori (
      Id int identity(1,1) primary key not null,
      Adi nvarchar(50) not null,
      Aciklama nvarchar(250) null,
      Durum bit,
      SiraNo int
      )
      
      create table tbl_AltKategori (
      Id int identity(1,1) primary key not null,
      KategoriId int,         
      Adi nvarchar(50),
      Aciklama nvarchar(250),
      Durum bit,
      SıraNo int
      )
```


## İnsert




```
      insert into tbl_Kategori(Adi,Durum,SiraNo)
      values('Telefon',1,1),
            ('Bilgisayar',1,2),
            ('Bilgisayar Parçaları',1,3)
   
      insert into tbl_AltKategori( KategoriId,Adi,Durum,SiraNo)
      values (1,'Cep Telefonları',1,1),
             (1,'Akıllı Saatler',1,2),
             (1,'Tablet',1,3),
             (2,'NeteBook',1,1),
             (2,'Masaüstü Bilgisayarları',1,2),
             (2,'Yazıcılar',1,3)



```


## Select where kullanımı ile tablo birleştirme


>>         AS             tabloadi.sütunadi as (sorgu sonucunda tablodaki sütun adını değişir.)
>>         ORDER BY       sıralama yapılır
>>         WHERE          seçilen tabloları filtreleyerek istenen sonucu verir
>>                        tablo1.değişken  =  tablo2.(tablo1deki değerin tablo2deki eşleşmesi)


>>      Kısaltma örneği   
>>
>>     .......from 	tbl_Kategori k,	tbl_AltKategori a,......
>>
>>      Tablo isimlerinin sorgu devamındaki kısaltmaları


```
    Ornek 1   -->Kategorilerin , alt kategorisini listeleyen ve sira numarasına göre sıralayan sorgu
    
  
    select tbl_Kategori.Adi as KategoriAdi, tbl_AltKAtegori.Adi as AltKAtegoriAdi 
    from tbl_AltKAtegori,tbl_Kategori
    where tbl_AltKAtegori.KategoriId = tbl_Kategori.Id 
    order by tbl_Kategori.SiraNo


    Ornek 2   --> Yazıcıların adı markası fiyatı ve durumunu listeleyen sorgu
    
    select 
    ur.Adi as UrunAdi,
    ma.Adi as MarkaAdi,
    SatisFiyat,
    ur.Durum as Durum, 
    ak.Adi as AltKategoriAdı
    
    from 
    tbl_Marka ma, tbl_Urun ur, tbl_AltKategori ak
    
    where 
    ma.Id = ur.Id and 
    ur.AltKategoriId = ak.Id and 
    ak.Adi ='Yazıcılar'



```


## Not in kullanımı




```
    Ornek 3   -->  Ürün olmayan kategorileri listeleyen sorgu
  
    select ak.Adi 
    from  tbl_AltKategori ak
    where ak.Id not in (select AltKategoriId from tbl_Urun)
    
```


## Email kontrolü

```
    Ornek 4  --> İletişim bilgisi ..@..com şeklinde olmayan müşterileri listeleyen sorgu
    
    select * 
    from tbl_Musteri
    where iletisim not like '%@%com%'
    
```


## Join kullanımı


 ![alt text](https://storage.googleapis.com/gweb-cloudblog-publish/images/joins_1.max-1600x1600.png)


>>
>> Select * from tablo1 JOİNTÜRÜ  tablo2  ON    tablo1.ozellik = tablo2.( tablo1deki ozelligin karşılığı)
>>


```

  Rigth join
  
  select * from tbl_Musteri right join tbl_Sepet 	on tbl_Musteri.Id = tbl_Sepet.MusteriId


  Çoklu join 
  
  select
  mu.Adi +' '+ mu.Soyadi as MusteriAdiSoyadi,
	ur.Adi as UrunAdi,
	se.Adet,
  se.Fiyat 
  
  from
  tbl_Musteri mu inner join tbl_Sepet se
	on mu.Id = se.MusteriId
  inner join tbl_Urun ur 
  on se.UrunId = ur.Id


```


## Sum count Group by

>> 
>>         SUM (değişken adi)            verilen değişkeni toplar
>>         GROUP BY                      gruplama yapar
>>         COUNT(*)                      adet döndürür
>> 

```
    Ornek 5  -->  Müşteri bazlı  kaç kere ve kaç defa alışveriş yapılmıştır

    select mu.Adi ,sum(se.Adet) as Toplam , COUNT(*) as Adet

    from tbl_Musteri mu , tbl_Sepet se

    where se.MusteriId = mu.Id

    group by mu.Adi           


```


## Convert 

>>
>>      Convert(Hedeflenen Tür, Değişken)
>>


```


    select Adi,SatisFiyat,
    CONVERT(money, SatisFiyat * 1.1 )as ZamliFiyat,    // integer türünü moneye çeviriyor
    Convert(money, SatisFiyat *0.1 ) as ZamMiktar
    from tbl_Urun


```


## İçiçe sorgu

>>      Tablo birleştirme yöntemleri 
>>      1- Left join , right vb join yönetmleri ile 
>>		  2- Where koşulu ile tabloları birleştirebiliriz
>>		  3- Subquery(iç içe sorgular yada alt sorgu)


```
  --İç sorgunun cevabı dış sorgunun kriteridir.
  
    select * 
    from tbl_Urun 
    where AltKategoriId in (
    
        select Id 
        from tbl_AltKategori 
        where KategoriId  in(
          
              select Id 
              from tbl_Kategori 
              where Adi ='Telefon'))



```


## İçiçe sorgu ile update




```

    update tbl_Urun set SatisFiyat = SatisFiyat * 1.1
    where Id in(
          select Id 
          from tbl_Urun 
          where AltKategoriId in (
              select Id 
              from tbl_AltKategori 
              where KategoriId  in(
              select Id from tbl_Kategori ))


```


## Case kullanımı 

>>      Veritabanındaki veriye göre sonuç tablosunun daha anlaşılır olmasını sağlar 
>> 
>>      Orneğin veritabanında 'IsAdmin'   0 ve 1 değerlerine sahip 
>> 
>>      Sorgu sonucu tabloda 
>> 
>>      '0'  -> Admin Değil  ,  '1'  ->  Admin olarak gözükmesi daha okunaklı olur
>> 




```

SELECT (case Cinsiyet 
	when 'E' then 'Erkek'
	when 'K' then 'Kadın' end )as cinsiyet,
	(case IsGozluk
	 when 0  then 'Gözlüksüz'
	 when 1 then 'Gözlüklü' end) as GozlukDurum, from ........

```




## Unıon




```

	union,
	union all

	intersect 	-> 	 iki sorgu arasındaki ortak olanı verir, 
	except(minus)	->	 iki sorgudaki farklı olanı verir (ilk sorguyu görür) */

```

## Stored Procedure

>>
>> İlk derlemeden sonra bir daha derlenmeye ihtİyaç duyulmayan kod bloğuna denir
>>Procedure ve fonksiyon farkı: fonksiyonlarda geriye değer dönmek zorundadır, procedurelerde öyle zorunluluk yoktur.

>> Procedure oluşturma

```

	create procedure usp_KategoriListesi
	as
	begin
	select * from tbl_Kategori
	end

```

>> Procedure çağırma

```
	exec usp_KategoriListesi

	--procedurede değişiklik yapmak için ALTER kullanıyoruz.

```

## Procedure orneği




```

	Ornek 6 --> Marka adına göre markanın bulunduğu kategorilerin adını procedure 


	create procedure sp_Marka
	
	@MarkaAdi nvarchar(50)
	as
	begin

	select *
	from tbl_Kategori
	where Id in(
		select KategoriId
		from tbl_AltKategori
		where Id in(	
			select AltKategoriId
			from tbl_Urun
			where MarkaId in(	
				select Id 
				from tbl_Marka
				where Adi = @MarkaAdi)))
	end

	exec sp_Marka 'Apple'
```


## Function




```

	Ornek 7 -> Ad soyadı birleştiren fonksiyon
	
	create function Fn_Birlestir(
	@Adi nvarchar(20),
	@Soyadi nvarchar(30))
	returns nvarchar(51)
	as
	begin
		return @Adi + space(1)+ @Soyadi
	end

	
	--Fonskiyon kullanımı
	
	select dbo.Fn_Birlestir('Tuncay','Tanin') as AdSoyad

```


## Function Alter




```
	Ornek 8 -> Yaş hesaplayan fonksiyon

	--Alter ile fonksiyon güncellenir.
	
	alter function Fn_YasHesapla(
	@Tarih date
	)
	returns int
	as
	begin
		  return  DateDiff(MONTH,@Tarih,getdate())	
	end


	select dbo.Fn_YasHesapla('01.07.2000')


```


## Function -- Tablo döndürme




```

	alter function Fn_KategoridekiUrunler(@KategoriId int, @KategoriAdi nvarchar(50))
	returns table
	as
		return (select ur.Adi, ur.Id as UrunId,
			ur.MarkaId,ur.Stok,
			ka.Adi as KategoriAdi, 
			ak.Adi as AtlKategoriAdi			
			
			from tbl_Kategori ka, tbl_AltKategori ak, tbl_Urun ur
			where ka.Id = ak.KategoriId and
			ak.Id = ur.AltKategoriId and
			ka.Id = @KategoriId or ka.Adi = @KategoriAdi)


	-- Fonksiyonun döndürdüğü tabloda sorgulama 
	
	select * from dbo.Fn_KategoridekiUrunler(0,'Telefon')


```


## Varolan tablolardan rastgele veri alımı

>> if else kullandığımız zamana süslü parantezler yerine begin end kullanılır
>> rand(): 0-1 arasında sayı üretir

```	
	Ornek 9 -> Personel tablosu oluşturmak için otomatik random değerler atama


	-- insert için değişkenler
	use Deneme2
	declare @Adi nvarchar(100)
	declare @Soyadi nvarchar(100)
	declare @Cinsiyet char(1)
	declare @Email nvarchar(200)
	declare @Sehir nvarchar(50)
	declare @DogumTarihi date
	declare @Tckn int
	set @Tckn = 0

	-- Geçici değişkenlerim
	declare @Id int
	declare @YeniID int 
	set @YeniID= 0
	declare @Sayac int
	set @Sayac = 0

		while @Sayac < 300000
		begin
			
			-- isimler tablosunda rastgele isim ve cinsiyet alma
			set @Id = rand()*12923+1 
			set @Adi = (select Ad from isimler where Id = @Id)
			set @Cinsiyet =(select Cinsiyet from isimler where Id = @Id)

			
			-- soy isimlerden soyadi alalım
			--select max(Id) from Soyisimler
			set @Id = rand()*1603+1
			set @Soyadi = (select Soyadi from Soyisimler where Id = @Id)

			
			-- sehiri alalım
			set @Id = rand()*81+1
			set @Sehir = (select Adi from Sehirler where Id= @Id)

			
			-- email oluşturma
			set @Email = trim(@Adi)+'.'+trim(@Soyadi)+'@aydin.edu.tr'

			
			-- Doğum Tarihi oluşturma
			set @DogumTarihi = getdate()- (rand()*50*365+(18*365)) -- 18 -68 yaş arasında bir sayı üretti

			
			set @Id =0
			--set @Id = (select count(*) from tbl_Personel where Adi = @Adi and Soyadi = @Soyadi )
			
			
			--if else  kullanımı
			
			if @Id=0			
			begin 
				set @YeniID  = @YeniID + 1 
				set @Tckn = @YeniID * 1000
				insert into tbl_Personel(Id,Adi,Soyadi,Cinsiyet,Email,Sehir,DogumTarihi,Tckn)
				values(@YeniID,@Adi,@Soyadi,@Cinsiyet,@Email,@Sehir,@DogumTarihi,@Tckn)
				set @Sayac +=1
			end
			
			else
			begin
				print(@Adi +' '+@Soyadi+' bu kayıtan dahan önce eklenmiş')
			end
			
		end

```


## Transaction


>> Daha küçük parçalara ayrılmayan en küçük işlem yığınına denir. Hepsi ayrı ayrıdır ama bütündür.
>>
>> Örneğin :  Ürün sepete eklendi ve ürün tablosundan stok 1 azaldı, 
>>	      ayrı işlemler ama bir bütün içinde. 
>>	      her biri ayrı sorgular ama bir bütünmüş gibi çalışmasını sağlar.
>>



```	
	Ornek 10 -> Havale isteğini gerçekleştiren trans

	
	-- Banka Hesap oluşturma
	
		create table tbl_Hesap(
		Id int identity(1,1) primary key,
		MusteriAdi nvarchar(100) not null,
		BankAdi nvarchar(50) not null,
		HesapNo char(5) not null,
		Bakiye money not null
		)

		select * from tbl_Hesap
		begin transaction BankaHesap
		insert into tbl_Hesap(MusteriAdi,BankAdi,HesapNo,Bakiye)
		values('Rabia','Abdioğlu','00001',5000),
			   ('Ali Sa','İş Bankası','00002',3000),
			   ('Mehmet As','Yapı Kredi','00003',1500)

		select * from tbl_Hesap
		commit tran BankaHesap




	select * from tbl_Hesap
	
	
	
	alter proc usp_HavaleYap
	@GonderenHesap char(5),
	@AlıcıHesap char(5),
	@Miktar money
	as
	begin
		declare @HesapVarmi int
		begin tran HavaleYap
			(select @HesapVarmi = COUNT(*) 
							from tbl_Hesap
							where HesapNo = @GonderenHesap
									and Bakiye >= @Miktar)
			if(@HesapVarmi > 0)
			begin
				update tbl_Hesap set Bakiye = Bakiye- @Miktar
				where HesapNo = @GonderenHesap

				select @HesapVarmi = COUNT(*) 
				from tbl_Hesap
				where HesapNo = @AlıcıHesap

				if(@HesapVarmi > 0)
				begin
					update tbl_Hesap 
					set Bakiye = Bakiye+@Miktar
					where HesapNo = @AlıcıHesap
					commit tran HavaleYap
				end
				else
				begin
					rollback tran HavaleYap
				end
			end
			else
			begin
				commit tran HavaleYap
			end
	end
	



	
```


## Rollback ve commit 

>> ROLLBACK:  Herhangi bir sorunla karşılaşılınca işlemlerin bir kısmını yapsa da en başa ger döner
>>
>> Hata alana kadar işlemleri devam ettir ve işlemleri kaydet(COMMİT), hatadan sonrasındakileri geri al.(ROLLBACK)
>> 
>> Rolback: işlemi geri alma
>> Commit: hepsi başarılıysa onaylar
>>
>>Prensip bir işlem hatalıysa herşeyi geri al
>>
>> Transaction hasara dayalı olmalıdır.
>> 


```	
	
	--Ornek 10 için 
	--Kontrol kodları 
	
		select * from tbl_Hesap
		begin tran IslemYap

			declare @Durum bit
			exec usp_HavaleYap '00001','00006',5000, @Durum output

			select * from tbl_Hesap

			if(@Durum = 1)
			begin
				commit  -- DURUM 1 BAŞARILI
			end
			else
			begin
				rollback --İŞLEMİ GERİ ALIR
			end

		select @Durum
		
		select * from tbl_Hesap
```


## İndex Konusu



>> Bir tabloda çok fazla veriler varsa ve sorgumda bu bilgileri çekerken süre çok uzarsa bunu hızlandırmak için index kullanılır.
>>
>> Fiziksel olarak sıralıysa (Id) "clustered" değilse "non-clustered", her tabloda bir adet clustered oluşturulabilir.
>> 
>> leaf: adres tutar
>> uniq: sıralı olmayan ama kişiye özel olan (tc,email). Datanın eşi benzeri yok
>> 
>> primary key LZ olunca otomotik olarak clustered index olşturulur


```
		Clustered ındex:	yapısında veri sıralı olduğu için  hemen bulunabilir.	
					önce tabloda index varmı diye bakar.
					leaflerin içerisinde data nın adresini bulundurur.

-----
		Non-cluster:		önce içinde index bulunan tabloya bakıp adresini bulur sonra veriyi bulur.
					leaflerde bilgi yok bilginin (verinin) adresi var


-----
		
		Sorgu çok kısa sürede geliyorsa data sorun yaratmıyorsa index oluşturmaya gerek kalmaz.
		Yavaşsa index yapılabilir. Zaman tasarrufu yapılır.
		
-----
-----
-----

		
		Create clustered ındex indexadi	on tabloadi(satır adi)

		Create unıque ındex indexadi on tabloadi(satır adi)

		Create non clustered ındex indexadi on tabloadi(satır adi)


		!! Eğer unıq olmayan veya sıralı olmayan tabloya clusteres yapılırsa hata verir..!
		
-----

		
		İndex ne zaman kullanılmaz ?
		

		Her index yaptığında index tablosuna kayıt atılır
		Bellek azalır ve iş yükü artar.
		Eğer sorgu çok fazla kullanılıyorsa ve çok fazla kayıt varsa yapılır.
		
-----
		İndex var mı?
		
		
		select * from sys.indexes
		where OBJECT_NAME(object_id) = 'tbl_Personel'
		

-----		
		İndex oluşturma 
		
		create unique index MusteriId on tbl_Personel(Id)
		
		
		create nonclustered index nclsMusteriEmailIndex on tbl_Personel(Email)


		Sorgu sonucu istatistikleri görmek için 
		--SET STATISTICS IO ON
		--SET STATISTICS TIME ON



```


## SQL SORGU ÖRNEKLERİ




SQL Sorguları ve SQL Örnekleri
Aşağıdaki SQL sorguları için yukarıdaki veritabanı diyagramı kullanılacaktır.
 SELECT SORGULARI
1.Öğrenci tablosundaki tüm kayıtları listeleyin.
	 
select * from öğrenci

2.Öğrenci tablosundaki öğrencinin adını ve soyadını ve sınıfını listeleyin.
	 
select ograd,ogrsoyad,sinif from ogrenci
 
3. Öğrenci tablosundaki cinsiyeti kız (K) olan kayıtları listeleyiniz.
	 
select * from ogrenci where cinsiyet='K'
 
 4.Öğrenciler tablosundaki sınıfların adını listeleyiniz.(Not her sınıf adı birkez gösterilsin.)
select distinct sinif from ogrenci
 
 5.Öğrenci tablosundaki cinsiyeti Kız ve Sınıfı 10A olan öğrencileri listeleyiniz.
select * from ogrenci where cinsiyet='K' and sinif='10A'
 
 6.Öğrenci tablosundaki 10A veya 10B sınıfındaki öğrencilerin adını, soyadını ve sınıfını listeleyiniz
	 select ograd, ogrsoyad, sinif from ogrenci 
where sinif='10A' or sinif='10B'
 
 7.Öğrenci tablosundaki öğrencinin adını, soyadını ve numarasını okul numarasıolarak listeleyiniz. (as kullanım örneği)
select ograd,ogrsoyad,ogrno as 'okul numarası' from ogrenci
 
8. Öğrenci tablosundaki öğrencinin adını ve soyadını birleştirip, adsoyad olarak listeleyiniz. (as kullanım örneği)
	 
select ograd+ogrsoyad as 'Ad Soyad' from ogrenci
 
 9. Öğrenci tablosundaki Adı ‘A’ harfi ile başlayan öğrencileri listeleyiniz.

select * from ogrenci where ograd like 'A%'
 
 
10.kitap tablosundaki sayfa sayısı 50 ile 200 arasında olan kitapların adını ve sayfa sayısını listeleyiniz.
	 
select * from kitap where sayfasayisi between 50 and 200
 
 11. Öğrenci tablosunda adı Fidan, İsmail ve Leyla olan öğrencileri listeleyiniz.
select * from ogrenci where ograd in ('Fidan','İsmail','Leyla')
 
 12. Öğrenci tablosundaki öğrencilerden adı A, D ve K ile başlayan öğrencileri listeleyiniz.
select * from ogrenci where ograd like '[ADK]%'
 
 13. Öğrenci tablosundaki sınıfı 9A olan Erkekleri veya sınıfı 9B olan kızların adını, soyadını, sınıfını ve cinsiyetini listeleyiniz.
 select ograd,ogrsoyad,sinif,cinsiyet from ogrenci 
where (sinif='9A' and cinsiyet='E') or (sinif='9B' and cinsiyet='K')
 
 14. Sınıfı 9A veya BB olan erkekleri listeleyiniz. 
select ograd,ogrsoyad,sinif,cinsiyet from ogrenci 
where (sinif='9A' or sinif='9B') and cinsiyet='E'
 
 15.Öğrenci tablosunda doğum yılı 1989 olan öğrencileri listeleyiniz.(Not: veritabanında tarihler ay/gün/yıl şeklinde sorgulanır)	 
select * from ogrenci 
where dtarih between '01/01/1989' and '12/31/1989'
 
16.Öğrenci numarası 30 ile 50 arasında olan Kız öğrencileri listeleyiniz.
	 
select * from ogrenci 
where ogrno between 30 and 70 and cinsiyet = 'K'
 
 17.Öğrencileri adına göre sıralayınız.
select * from ogrenci order by ograd
 
18. Öğrencileri adına, adı aynı olanlarıda soyadlarına göre sıralayınız.
 
select * from ogrenci order by ograd,ogrsoyad
 
19. 10A sınıfındaki öğrencileri okul numarasına göre azalan olarak sıralayınız.
 
select * from ogrenci where sinif='10A' order by ogrno desc
 
 
20. Öğrenciler tablosundaki ilk 10 kaydı listeleyiniz.
	 
select top 10 * from ogrenci
 
21. Öğrenciler tablosundaki ilk 10 kaydın ad, soyad ve doğum tarihi bilgilerini listeleyiniz.
 
select top 10 ograd,ogrsoyad,dtarih from ogrenci
 
22.Sayfa sayısı en fazla olan kitabı listeleyiniz.
	 
select top 1 * from kitap order by sayfasayisi desc
 
 23. Öğrenciler tablosundaki en genç öğrenciyi listeleyiniz.
select top 1 ograd,ogrsoyad,dtarih from ogrenci order by dtarih desc
  
24. 10A sınıfındaki en yaşlı öğrenciyi listeyin.
	 
select top 1 ograd,ogrsoyad,dtarih from ogrenci 
where sinif='10A' order by dtarih
  
25. İkinci harfi N olan kitapları listeleyiniz.
	 
select * from kitap 
where kitapadi like '_n%'
  
26. Öğrencileri sınıflarına göre gruplayarak listeleyin.
	 
select * from ogrenci order by sinif
 
27.  Öğrencileri her sorgulamada sıralaması farklı olacak şekilde  rastgele listeleyin.
 
select * from ogrenci order by newid()
 
28. Rastgele bir öğrenci seçin
	 
select top 1 * from ogrenci order by newid()
 
29. 10A sınıfından rastgele bir öğrencinin adını, soyadını, numarasını ve sınıfını getirin.
	 
select top 1 ogrno,ograd,ogrsoyad,sinif from ogrenci
where sinif= '10A' 
order by newid()
 
 


INSERT INTO SORGULARI
30. Yazar tablosunu KEMAL UYUMAZ isimli yazarı ekleyin.
	 
insert into yazar(yazarad,yazarsoyad) values('Kemal','UYUMAZ')
 
31. Biyografi türünü tür tablosuna ekleyiniz.
	 
insert into tur values('Biyografi')
 
32. 10A sınıfı olan ÇAĞLAR ÜZÜMCÜ isimli erkek,  sınıfı 9B olan LEYLA ALAGÖZ isimli kız ve  sınıfı 11C olan Ayşe Bektaş isimli kız  öğrencileri tek sorguda ekleyin.
	 
insert into ogrenci(ograd,ogrsoyad,sinif,cinsiyet)
values('Çağlar','Üzümcü','10A','E'),('Leyla','Alagöz','9B','K'),('Ayşe','Bektaş','11C','K')
 
33 Öğrenci tablosundaki rastgele bir öğrenciyi yazarlar tablosuna yazar olarak ekleyiniz.

insert into yazar(yazarad, yazarsoyad) 
select top 1 ograd,ogrsoyad from ogrenci
order by newid()
 
34.Öğrenci numarası 10 ile 30 arasındaki öğrencileri yazar olarak ekleyiniz.
	 
insert into yazar(yazarad, yazarsoyad) 
select ograd,ogrsoyad from ogrenci where ogrno between 10 and 30
 
35. Nurettin Belek isimli yazarı ekleyip yazar numarasını yazdırınız.(Not: Otomatik arttırmada son arttırılan değer @@IDENTITY değişkeni içinde tutulur.)
 
insert into yazar(yazarad, yazarsoyad) 
values('Nurettin','Belek')
select @@IDENTITY
UPDATE SORGULARI
NOT:update sorgusunda dikkat edilmesi gereken en önemli husus şart kısmıdır. şart yazılmazsa güncelleme işlemine tüm kayıtlar dahil edilir.

36. 10B sınıfındaki öğrenci numarası 3 olan öğrenciyi 10C sınıfına geçirin.
	 
update ogrenci set sinif='10C' where ogrno=3
 
--sorguyu görüntülemek için yazıldı
select * from ogrenci where ogrno=3
 
37.  9A sınıfındaki tüm öğrencileri 10A sınıfına aktarın

update ogrenci set sinif='10A' where sinif='9A'
 
--sorguyu görüntülemek için yazıldı
select * from ogrenci where sinif='10A'
 38. Tüm öğrencilerin puanını 5 puan arttırın.

 update ogrenci set puan=puan+5
 
--sorguyu görüntülemek için yazıldı
select * from ogrenci
 
DELETE SORGULARI
NOT 1: DELETE sorgusunda dikkat edilmesi gereken en önemli husus şart kısmıdır. şart yazılmazsa silme işlemine tüm kayıtlar dahil edilir.
NOT 2: TRUNCATE TABLE komutu sorgu örneklerinin sonunda verilecektir.(Tabloyu boşaltmak için kullanılır. TRUNCATE TABLE TABLOADI)

39.  25 numaralı yazarı silin.
	 
--Not: veritabanı fk ayarlarında delete,update cascade ayarlandığı için ilişkili tabloları otomatik olarak güncellenecek.
delete from yazar where yazarno=25
 
 SELECT …… IS NULL Komutu
Select sorguları içinde değeri null olan kayıtları ararken alanadı=null olarak arama yapılamaz.  Null olan alanları aramak için is null ifadesi kullanılır.
40. Doğum tarihi null olan öğrencileri listeleyin. (insert sorgusu ile girilen 3 öğrenci listelenecektir)

select * from ogrenci where dtarih  is null
 
BİRDEN ÇOK TABLODAN VERİ ÇEKME (JOIN KULLANMADAN)

41. Öğrencinin adını, soyadını ve kitap aldığı tarihleri listeleyin.
 
select ograd,ogrsoyad,atarih from ogrenci,islem
where ogrenci.ogrno=islem.ogrno
 
42. Fıkra ve hikaye türündeki kitapların adını  ve türünü listeleyin.
	 
select kitap.kitapadi, tur.turadi from kitap,tur
where kitap.turno=tur.turno 
and tur.turadi in ('Hikaye','Fıkra')
 
 43. 10B veya 10C sınıfındaki öğrencilerin numarasını, adını, soyadını ve okuduğu kitapları listeleyin.
select ogrenci.ogrno,ograd,ogrsoyad,kitapadi 
from ogrenci,islem,kitap
where (sinif='10B' or sinif='10C')
and ogrenci.ogrno=islem.ogrno
and islem.kitapno=kitap.kitapno
 
 44. Roman türündeki kitapları okuyan öğrencilerin numarasını, adını, soyadını ve okuduğu kitabın adını listeleyin
select distinct ogrenci.ogrno,ograd,ogrsoyad,kitapadi
from ogrenci,islem,kitap,tur
where ogrenci.ogrno=islem.ogrno
and islem.kitapno=kitap.kitapno
and kitap.turno=tur.turno
and tur.turadi='Roman'
 
SQL JOIN ( INNER JOIN ) KULLANIMI
45. Öğrencinin adını, soyadını ve kitap aldığı tarihleri listeleyin.
	 
select ograd,ogrsoyad,islem.atarih from ogrenci
join islem on islem.ogrno=ogrenci.ogrno
  
46. Fıkra ve hikâye türündeki kitapların adını  ve türünü listeleyin.
	 
select kitapadi,turadi from kitap
join tur on kitap.turno=tur.turno 
and tur.turadi in('Hikaye','Fıkra')
 
Ya da
select kitapadi,turadi from kitap
join tur on kitap.turno=tur.turno 
where tur.turadi in('Hikaye','Fıkra')
 
 
47. 10B veya 10C sınıfındaki öğrencilerin numarasını, adını, soyadını ve okuduğu kitapları, öğrenci adına göre  listeleyin.
	 
select ogrenci.ogrno,ograd,ogrsoyad,sinif,kitapadi
from ogrenci
join islem on ogrenci.ogrno=islem.ogrno
join kitap on islem.kitapno=kitap.kitapno
where sinif='10B' or sinif='10C'
order by ogrenci.ograd
 
 


SQL LEFT JOIN Kullanımı
 48. Kitap alan öğrencinin adı, soyadı, kitap aldığı tarih listelensin. Kitap almayan öğrencilerinde listede görünsün.
select ograd,ogrsoyad,islem.islemno from ogrenci
left join islem on islem.ogrno=ogrenci.ogrno
 
49. Kitap almayan öğrencileri listeleyin.
 
select ograd,ogrsoyad,islem.atarih from ogrenci
left join islem on islem.ogrno=ogrenci.ogrno
where islem.atarih is null
 
 50. Alınan kitapların kitap numarasını, adını ve kaç defa alındığını kitap numaralarına göre artan sırada listeleyiniz.
 select kitap.kitapno, kitap.kitapadi,count(*) from islem
left join kitap
on kitap.kitapno=islem.kitapno
group by kitap.kitapadi,kitap.kitapno
order by kitap.kitapno
 
 51. Alınan kitapların kitap numarasını, adını kaç defa alındığını (alınmayan kitapların yanında 0 olsun) listeleyin.
select kitap.kitapno, kitap.kitapadi,count(islem.islemno) as adet from kitap
left join islem on kitap.kitapno=islem.kitapno
group by kitap.kitapadi,kitap.kitapno,islem.kitapno
order by adet
  
52. Öğrencilerin adı soyadı ve aldıkları kitabın adı listelensin.
	 
Select * from ogrenci 
left join islem on islem.ogrno=ogrenci.ogrno 
left join kitap on islem.kitapno=kitap.kitapno
SQL LEFT JOIN ve RIGHT JOIN Kullanımı
53.Her öğrencinin adı, soyadı, kitabın adı, yazarın adı soyad ve kitabın türünü ve kitabın alındığı tarihi listeleyiniz.  Kitap almayan öğrenciler de listede görünsün.
	 
Select ograd,ogrsoyad yazarad,yazarsoyad,kitapadi,turadi from kitap 
join tur on tur.turno=kitap.turno
join yazar on kitap.turno=yazar.yazarno
join islem on kitap.kitapno=islem.kitapno
right join ogrenci on ogrenci.ogrno=islem.ogrno
 
 
54.Her öğrencinin adı, soyadı, kitabın adı, yazarın adı soyad ve kitabın türünü ve kitabın alındığı tarihi listeleyiniz.  Kitap almayan öğrenciler de listede görünsün.( Farklı Çözüm)
	 
Select ograd,ogrsoyad yazarad,yazarsoyad,kitapadi,turadi from islem 
join kitap on islem.kitapno=kitap.turno
right join ogrenci on ogrenci.ogrno=islem.ogrno
left join tur on kitap.turno=tur.turno
left join yazar on yazar.yazarno=kitap.yazarno
 
55. 10A veya 10B sınıfındaki öğrencilerin adı soyadı ve okuduğu kitap sayısını getirin.
	 
select sinif, ograd,ogrsoyad,count(islemno) from ogrenci
left join islem on islem.ogrno=ogrenci.ogrno
where sinif in ('10A','10B')
group by sinif,ograd,ogrsoyad
order by count(*)
İÇ İÇE SELECT SORGULARI
56.En fazla sayfa sayılı kitabın bilgilerini listeleyiniz.
Yöntem 1
	 
select top 1 * from kitap order by sayfasayisi desc --1
 
Yöntem 2( İç içe select ile)
 
select * from kitap where sayfasayisi in (select max(sayfasayisi) from kitap) --2
 
 57. Sayfa sayısı ortalama sayfa sayısından fazla olan kitapları listeleyiniz.
select * from kitap where sayfasayisi >(select avg(sayfasayisi) from kitap)
 
58.İç içe select ile dram türündeki kitapları listeleyiniz.
	 
select * from kitap where kitap.kitapno=(select (kitap.kitapno) from tur where turadi='dram')
 
59.Adı e harfi ile başlayan yazarların kitapları
	 
select * from kitap where kitap.yazarno in (select yazar.yazarno from yazar where yazarad like 'e%')
 
60.İç içe sorgu ile kitap okumayan öğrencileri listeleyiniz.
	 
select * from ogrenci where ogrenci.ogrno not in ( select distinct islem.ogrno from islem)
 
61. İç içe select ile okunmayan kitapları listeleyiniz.
 
select * from kitap where kitap.kitapno not in (select distinct islem.kitapno from islem)
62. Mayıs ayında okunmayan kitapları listeleyin.
	 
select * from kitap where kitap.kitapno not in (select distinct islem.kitapno from islem where MONTH(islem.atarih)=5)
 
 
SQL AVG Kullanımı
AVG fonksiyonu ortalama değeri döndürür.
–Tüm kitapların ortalama sayfa sayısını bulunuz.
	 
select avg(sayfasayisi) as [ortalama sayfa] from kitap
  
–Sayfa sayısı ortalama sayfanın  üzerindeki kitapları listeleyin.
	 
select kitapadi,sayfasayisi from kitap
where sayfasayisi>(select avg(sayfasayisi) from kitap)
SQL COUNT Kullanımı
COUNT fonksiyonu , belirtilen ölçütlerle eşleşen satır sayısını döndürür.

–Öğrenci tablosundaki öğrenci sayısını gösterin
	 
select count(*) from ogrenci
 
–Öğrenci tablosundaki toplam öğrenci sayısını toplam sayı takma(alias kullanımı) adı ile listeleyin.
	 
select count(*) as ogrenciSayisi from ogrenci
 
–Öğrenci tablosunda kaç farklı isimde öğrenci olduğunu listeleyiniz.
 
select count(distinct ograd) from ogrenci
SQL MAX Kullanımı
MAX fonksiyonu belirtilen ölçülerle eşleşen en yüksek kayıtı getirir.
 
–En fazla sayfa sayısı olan kitabın sayfa sayısını listeleyiniz.
	 
select max(sayfasayisi) as 'En Fazla Sayfa' from kitap
 
–En fazla sayfası olan kitabın adını ve sayfa sayısını listeleyiniz.
	 
select kitapadi,sayfasayisi from kitap
where sayfasayisi= (select max(sayfasayisi) from kitap) 







SQL MIN Kullanımı
MIN fonksiyonu belirtilen ölçülerle eşleşen en yüksek kayıtı getirir.

–En az sayfa sayısı olan kitabın sayfa sayısını listeleyiniz.	 
select min(sayfasayisi) as 'En Fazla Sayfa' from kitap
 
–En az sayfası olan kitabın adını ve sayfa sayısını listeleyiniz.
	 
select kitapadi,sayfasayisi from kitap
where sayfasayisi= (select min(sayfasayisi) from kitap)

–Dram türündeki en fazla sayfası olan kitabın sayfa sayısını bulunuz.
	 
select max(sayfasayisi) from kitap,tur 
where kitap.turno=tur.turno and tur.turadi='dram'
 
–numarası 15 olan öğrencinin okuduğu toplam sayfa sayısını bulunuz.
	 
select sum(sayfasayisi) from ogrenci,islem,kitap
where ogrenci.ogrno=islem.ogrno 
and islem.kitapno=kitap.kitapno
and ogrenci.ogrno=15
 
SQL DATE / SQL DATEDIFF Kullanımı
DATEDIFF :Belirtilen tarihler arasındaki farkı hesaplamak için kullanılır. 
GETDATE :Şuan ki tarih ve zamanı getirir. MySqlde now() fonksiyonu kullanılır.
 
–Öğrencinin adını, soyadını ve yaşını listeleyin.
SELECT ograd, ogrsoyad,DATEDIFF(year,dtarih,GETDATE()) from ogrenci
SQL GROUP BY Kullanımı
–İsme göre öğrenci sayılarının adedini bulunuz.(Örn: ali 5 tane, ahmet 8 tane )
	 
select ograd,count(*) from ogrenci group by ograd
 
–Her sınıftaki öğrenci sayısını bulunuz.
	 
select sinif, count(*) from ogrenci group by sinif
 
–Her sınıftaki erkek ve kız öğrenci sayısını bulunuz.
	 
select sinif, cinsiyet,count(*) from ogrenci group by cinsiyet,sinif
 
–Her öğrencinin adını, soyadını ve okuduğu toplam sayfa sayısını büyükten küçüğe doğru  listeleyiniz.
	 
select ograd,ogrsoyad,sum(sayfasayisi) as sayfa from ogrenci,kitap,islem
where ogrenci.ogrno=islem.ogrno and kitap.kitapno=islem.kitapno
group by ograd,ogrsoyad,ogrenci.ogrno
order by sayfa
 
–Her öğrencinin okuduğu kitap sayısını getiriniz.
	 
select ograd,ogrsoyad,count(*) as kitapsayisi from ogrenci,kitap,islem
where ogrenci.ogrno=islem.ogrno and kitap.kitapno=islem.kitapno
group by ograd,ogrsoyad,ogrenci.ogrno
order by kitapsayisi
 
 

