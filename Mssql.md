## MSSQL ile veritabanı işlemleri #

- [Create](#Create)
- [İnsert](#İnsert)
- [Select where kullanımı ile tablo birleştirme](#Select-where-kullanımı-ile-tablo-birleştirme)
- [Not in kullanımı](#Not-in-kullanımı)
- [Email kontrolü](#Email-kontrolü)
- [Join kullanımı](#Join-kullanımı)
- [Sum count Group by](#Sum-count-Group-by)
- [Convert](#Convert)
- [İçiçe sorgu](#İçiçe-sorgu)
- [İçiçe sorgu ile update](#İçiçe-sorgu-ile-update)
- [Case kullanımı](#Case-kullanımı)
- [Unıon](#Unıon)
- [Stored Procedure](#Stored-Procedure)
- [Procedure çağırma](#Procedure-çağırma)
- [Procedure orneği](#Procedure-orneği)
- [Function](#Function)
- [Function Alter](#Function-Alter)
- [Function Tablo döndürme](#Function-Tablo-döndürme)
- [Varolan tablolardan rastgele veri alımı](#Varolan-tablolardan-rastgele-veri-alımı)
- [Transaction](#Transaction)
- [Rollback ve commit](#Rollback-ve-commit)
- [İndex Konusu](#İndex-Konusu)







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


