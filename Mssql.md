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


## Not in kullanımı




```

```


## Not in kullanımı




```

```


## Not in kullanımı




```

```


## Not in kullanımı




```

```


## Not in kullanımı




```
