
## Java Ornekleri


- [Kullanıcıdan alınan 5 sayi pozitif mii negatif mi ](#Kullanıcıdan-alınan-5-sayi-pozitif-mi-negatif mi )
- [Kullanıcıdan alınan 3 sayiyi büyükten küçüğe sırala](#Kullanıcıdan-alınan-3-sayiyi-büyükten-küçüğe-sırala)
- [Yukarıdaki örneğin yer değiştirme mantığıyla yapılışı](#Yukarıdaki-örneğin-yer-değiştirme-mantığıyla-yapılışı)
- [Faktöriyel bulma](#Faktöriyel-bulma)
- [Kenar uzunlukları verilen üçgenin çeşidini bulma](#Kenar-uzunlukları-verilen-üçgenin-çeşidini-bulma)
- [String sınıfı](#String-sınıfı-metodları)
- [Math sınıfı](#Sayi)
- [Rastgele seçilen sayiyi tahmin etme](#Rastgele-seçilen-sayiyi-tahmin-etme)
- [İnheritance](#İnheritance)
- [Constructor](#Constructor)
- [This ve Super](#This-ve-Super)
- [Araba constructor](#Araba-constructor)
- [OOB örnek](#OOB-örnek)




## Kullanıcıdan alınan 5 sayi pozitif mii negatif mi 

```java

    public static void main(String[]args){
		int a;
		
		Scanner yaz=new Scanner(System.in);
	
	
		
		for(int i=0;i<5;i++){
			a=yaz.nextInt();
			if (a<0){System.out.println(i+1+". sayi negatiftir.");}
			else if(a>0){System.out.println(i+1+"= sayi pozitiftir.");}
			else {System.out.println(i+1+"= sayi sifirdir.");}


		}
```
    
    
## Kullanıcıdan alınan 3 sayiyi büyükten küçüğe sırala 

```java

	public static void main(String[]args){
		int a,b,c;
		
		Scanner yaz=new Scanner(System.in);
	
		a=yaz.nextInt();
		b=yaz.nextInt();
		c=yaz.nextInt();

		int buyuk = 0,kucuk=0,orta=0;
	
			if(a>=b && a>=c ){
				buyuk=a;
				if(b>=c){orta=b;kucuk=c;}
				else if(c>=b){orta=c; kucuk=b;	}	}
			
			if(b>=a && b>=c ){
				buyuk=b;
				if(a>=c){orta=a;kucuk=c;	}
				else if(c>=a){orta=c; kucuk=a;	}
			}
			if(c>=a && c>=b ){
				buyuk=c;
				if(b>=a){orta=b;kucuk=a;}
				else if(a>=b){orta=a; kucuk=b;	}
			}
			
			System.out.println(buyuk+" ---> BUYUK");
			System.out.println(orta+" ---> ORTA");
			System.out.println(kucuk+" ---> KUCUK");


		
}
```
    
    
## Yukarıdaki örneğin yer değiştirme mantığıyla yapılışı

```java	


		int a,b,c,d;
			
		Scanner yaz=new Scanner(System.in);
		
		a=yaz.nextInt();
		b=yaz.nextInt();
		c=yaz.nextInt();
		//d ye en buyuk olan atanır

		
		if(a<=b){
		d=a;
		a=b;
		b=d;}
		
		if(a<=c){
		d=a;
		a=c;
		c=d;
		}
		
		if(b<=c){
		d=b;
		b=c;
		c=d;
		}	
			
		
		System.out.println(a+">"+b+">"+c);

```
# Faktöriyel bulma

```java
		int a;
		int sonuc=1;
		Scanner yaz=new Scanner(System.in);
		a=yaz.nextInt();
		
		for(int i=a;i>=1;i--){	sonuc*=i;}
		
		System.out.print(a+"! = "+sonuc);
```
## Kenar uzunlukları verilen üçgenin çeşidini bulma

```java
		int a,b,c;
		Scanner yaz=new Scanner(System.in);
		a=yaz.nextInt();
		b=yaz.nextInt();
		c=yaz.nextInt();
		
		if(a>0 &&b>0 &&c>0){
		
			if((a==b && c!=b )||(a==c && c!=b ) ||(c==b && c!=a )){
			System.out.println("Ucgen ikizkenardir");

			}
			else if(a==b && c==b){
				System.out.println("Ucgen eşkenardir");
			}
			else if(a!=b && c!=b &&a!=c){
				System.out.println("Ucgen cesitkenardir");
				}
			else{System.out.println("Hatali");
				}}
		else{
		System.out.println("Ucgenin kenarlari negatif deger veya 0 olamaz.");}
		
```
    
    
## String sınıfı metodları 

> .toLowerCase()
> 
> Methodu cağıran metin ifadesinin(dizgi) nesnesinin tamamen
> 
> küçük harfe çevrilmiş halini geri verir.
> 

```java	 
		string kelime="MERHABA";
		string kkelime=kelime.toLowerCase();
```
> .toUpperCase();
> 
> Methodu çağıran dizgi nesnesini tamamen büyük harfe çevrilmiş
> 
> olan dizgi verir.

```java	 		
		string kelime="merhaba";
		string bkelime=kelime.to.UpperCase();
```
	
> .substring(Başlangıç)
> 
> Methodu çağıran dizgi nesnesinin başlangıç numaralı karekterinden
> 
> dizginin sonuna kadar olan bölümünü bir dizgi olarak geri verir.
> 

```java

		string kelime="merhaba";
		string parçala=kelime.substring(4);
```
				
> .substring(Başlangıç,son)
> 
> Methodu çağıran başlangıç numaraları karakterinden son numaralı
> 
> karakterine kadar olan bölümünü bir dizgi olarak geri verir.
> 
```java

		string kelime="merhaba";
		string oarçala=kelime.substring(1,4); 
		string kelime="bilgisayar";
		string oarçala=kelime.substring(1,4);
		string kelime="rabia abdioglu";
		string oarçala=kelime.substring(2,7); 
```
				
> .indexOf(bir dizi)
> 
> String üzerinde bir dizgin ile kayıtlı ilk görüldüğü noktayı bulur.
> 
> Eğer bir dizgi dizgisinin içinde yoksa -1 değerini verir.
> 


```java

		string kelime="rabia rabia rabia";
		int a = kelime.indexOf("rabia"); 0
		int a = kelime.indexOf("r"); 2
		System.out.println(a);
```

> .indexOf(dizgi,başlangıç)
> 
> Bir dizgi üzerinde başlangıç numaralı karekterden sonra başka bir
> 
> dizginin ilk görüldüğü noktayı bulur,yoksada -1 döndürür.
> 


```java
		string kelime="rabia rabia rabia";
		int a = kelime.indexOf("rabia",5); 8
```
		
> .lastindexOf(dizgi)
> 
> Dizgi üzerinde bir dizgi ile tanımlı başka bir dizginin son 
> 
> görüldüğü noktayı bulur.Eğer dizgi içinde yoksa sonuç olarak -1 
> 
> değerini verir.
> 
				
```java

		string kelime="rabia rabia rabia";
		int a = kelime.lastIndexOf("rabia"); 
```
				
> .length()
> 
> Dizgi nesnesinin içinde bulunan karekter sayısını verir.
> 

```java

		String kelime = "rabia rabia";
		int a = kelime.length();
		System.out.printIn(a);
```

> .trim()
> 
> Dizginin başındaki ve sondaki boşlukları silindiği bir dizgi
> 
> geri verir.
> 
```java

		string kelime = " rabia abdioglu ";
		string at = kelime.trim();
 ```
 
> .charAt(konum)
> 
> Dizginin üzerinde yer alan konum numaralı karekteri geri verir.
> 

```java
				
		string kelime="merhaba";
		char a = kelime.CharAt(3); 
```
> .compareTo(dizgi)
> 
> Methodu çağıran nesne ile dizgi nesnesini alfabetik olarak
> 
> karşılaştırır.Eğer methodu çağıran nesne daha kuçuk ise method
> 
> sıfırdan daha küçük bir değer verir.eğer iki dizgi eşitse sıfır
> 
> verir.Eğer methodu çağıran nesne büyükse 0 dan büyük değer verir.
> 
```java

		 String kelime="merhaba";
		 int a = kelime.compareTo("merhaba"); 
		 System.out.println(a);
```

> .equals()             eşit mi true false döndürür.
> 
> .equalsIgnoreCase()   büyük küçük önemli değil eşit ise true.
> 
    
```java
		String kelime1="Rabia";
		String kelime2="KELİME";
		String kelime3="kelime";

		System.out.println(kelime1.equals(kelime1));              //true
		System.out.println(kelime1.equals(kelime2));              //false
		System.out.println(kelime2.equalsIgnoreCase(kelime3));    //true
		System.out.println(kelime2.equals(kelime3));              //false
		System.out.println(kelime2.equals(kelime3.toUpperCase()); //true
				
			
				
```

## Math sınıfı

> Bazı metodlar ve kullanımları
>

| Yöntem         |     Açıklama      |          Ornek |
| :---         |     :---      |          :--- |
| abs(x)         |     x in mutlak degeri      |          math.abs(-237) |
| ceil(x)	         |     xi büyük olan tamsayıya çevirir      |          math.ceil(9.2) -> 10.0 |
| floor(x)         |     xi küçük olan tamsayıya çevirir      |          math.flooar(9.2) -> 9 |
| round(X)         |     yakın olan tam sayiya yuvarlar      |          math.round(9.2) -> 9 |
| max(x,y)         |     büyük olan verir      |          math.max(5.0,6.0) -> 6 |
| min(x,y)         |     kücük olan verir      |          math.min(5.0,6.0) -> 5 |
| pow(x,y)         |     xin yninci kuvveti      |          math.pow(2,3) -> 8.0 |
| sqrt(x)         |     xin kare kökü      |          math.sqrt(9) -> 3 |
| random()         |     0,1 arası rastgele sayi üretir      |          math.random(); |

	

>> Random örnek kullanımı
>> 
>> int a=15+(int)(Math.random()*55);   //15 - 75 arası rastegele sayi üretir
>> 

 
    
## Rastgele seçilen sayiyi tahmin etme
```java

int a=1+(int)(Math.random()*99);
		int tahmin;
		System.out.println(a);
		Scanner scanner=new Scanner(System.in);
		System.out.println("Sayi giriniz");
		tahmin=scanner.nextInt();
		
		
		do{
			if(tahmin<a){
				System.out.println("Daha büyük bir sayi giriniz");
				tahmin=scanner.nextInt();
			}
			else{	System.out.println("Daha kücük bir sayi giriniz");
			tahmin=scanner.nextInt();}
		}while (a!=tahmin);
		System.out.println("DOĞRU");

```
    
    
## İnheritance

>> miras alma - kalıtım 
>> 
>> eğer bir sınıf  bir üst sınıftan türetilirse , yeni sınıf bu üst sınıfın özelliklerini alır ve metodlarına sahip olur
>> 
>> bu durumda miras alınan sınıfa üst sınıf superclass 
>> 
>> miras alan sınıfa subclass denir.
>> 



```java

//super
public class araba{	

	String renk ;
	String model;
	int hız;
	int kapisayisi;
	
	public void yaz(){
		System.out.println("renk....:"+renk);
		System.out.println("model....:"+model);
		System.out.println("hız....:"+hız);
		System.out.println("kapisayisi....:"+kapisayisi);

		}}
//sub
public class tramvay  extends otomobil{
	int vagonsayisi;
	
	public static void main(String[] args) {		
		tramvay t=new tramvay();
		t.vagonsayisi=8;
		t.kapisayisi=16;
		t.model="t456";
		t.renk="kırmızı";
		t.hız=123;
		t.yaz();
		}}
//sub
public class otomobil extends araba{
	String plaka;
	public static void main(String[] args) {

		otomobil o=new otomobil();	//nesne oluşturma
		o.plaka="34RR1998";		//sub classa ait özellik
		o.hız=180;			//superclasstan miras alınan özellik
		o.kapisayisi=4;
		o.model="Beetle";
		o.renk="siyah";
		o.yaz();			//superclasstan miras alınan fonksiyon
		}}


```
    
    
## Constructor

>> Nesne Kurucular:
>> 
>> Bir nesne yaratıldığında nesnenin parametrelerine otomatik olarak veya kullanıcı vasıtasıyla çeşitli değerler atanabilir. 
>> 
>> Bu nesne kurucular tarafından gerçekleştirilir.
>> 
>> Programınızda yeni bir nesne oluştururken bu nesnenin bazı özelliklerini oluşma anında belirlemek isteyebilirsiniz. 
>> 
>> Burada yapıcılar (constructor) devreye girer. 
>> 
>> Sınıfların oluşturulmasını sağlayan ana metotlar bulunur bunlar sınıf örneklendirip 
>> nesne yapıldığında nasıl davranacağını tanımlar. 
>> 
>> Bu metotlara ise yapıcı-kurucu-constractor adı verilir. 
>> 

>> Özellikler
>> 
>> Bir sınıf yapıcısının adı sınıfın adıyla aynıdır.
>> 
>> Bir yapıcı her zaman new kelimesiyle çağırılır.
>> 
>> Bir yapıcı geriye değer döndürmez.
>> 
>> Yapıcılar parametreli ve parametresiz kullanılabilirler.
>> 


```java
	Class sınıfım{
	Int x;
	Sınıfım(int i)
	{
		x=i;
	}
	}
```
    
    
## This ve Super

>> this: sınıf içindeki özelliğe erişmek için kullanılır
>> super: alt sınıf veya üst sınıftakilerden erişmek isteniliyorsa

# Daire constructor 

```java	
	public class Daire {
		int yari_cap;
		double pi = 3.14;

		public Daire(int yc)
			{
			this.yari_cap = yc;
			}

		public void alan_hesapla()
			{
			System.out.println("alan: "+pi * Math.pow(this.yari_cap, 2));
			}

		public void cevre_hesaplar()
			{
			System.out.println("cevre: "+2 * pi * this.yari_cap);
			}

		public static void main(String[] args) {
			Daire d = new Daire(3);
			d.alan_hesapla();
			d.cevre_hesaplar();
			}
	}

```
    
    
## Araba constructor

```java	
	public class Araba {
		String renk;
		int hiz;
		int beygir_gucu;

		public Araba(String r, int h, int bg)	//CONSTRUCTOR
		{
			this.renk = r;
			this.hiz = h;
			this.beygir_gucu = bg;
		}

		public void yaz()
		{		
			System.out.println("arabanin hizi: "+this.hiz);
			System.out.println("arabanin rengi: "+this.renk);
			System.out.println("arabanin hizi: "+this.beygir_gucu);
		}


		public static void main(String[] args) {
			Araba a1 = new Araba("kirmizi",50,500);		
			a1.yaz();
			System.out.println("-----------------");
			Araba a2 = new Araba("siyah",100,700);	
			a2.yaz();
		}

	}

```
    
    
## OOB örnek 

>> Canlılar super class
```java	
	public class canlilar {

		int boyu;
		int agirlik;
		String ad;

		public canlilar(int b,int a,String isim){

			this.boyu=b;
			this.agirlik=a;
			this.ad=isim;
		}

		public void yazdir(){

			System.out.println("boyu...: "+boyu);
			System.out.println("agirlik...: "+agirlik);
			System.out.println("adi...: "+ad);
		}


		public static void main(String[] args) {

			canlilar c1=new canlilar(5,2,"enes");
			c1.yazdir();


		}

	}
```
>> İnsan sınıfı
    

```java

	public class insan extends canlilar {

		int yas;
		String cins;

		public insan(int bbbb,int aaaa,String isimmmm,String cns,int y){

			super.boyu=bbbb;
			super.agirlik=aaaa;
			super.ad=isimmmm;
			this.cins=cns;
			this.yas=y;


		}


		public static void main(String[] args) {

			insan i1=new insan(180,60,"rabia","insan",20);
			i1.yazdir();

		}

	}
```
>> Hayvan sınıfı
    

```java

	public class hayvanlar extends canlilar {

		String cins;

		public hayvanlar(int bb,int aa,String isimm,String c){

			super.boyu=bb;
			super.agirlik=aa;
			super.ad=isimm;
			this.cins=c;
		}


		public static void main(String[] args) {

		hayvanlar h1=new hayvanlar(5,6,"mırmır","kedi");	
		h1.yazdir();

		}

}

```
>> Bitki sınıfı
    

```java

	public class bitkiler extends hayvanlar {
		// hayvanlardan miras alınmasının sebebi
		// hayvanlar sınıfının miras aldığı, canlılar sınıfının özelliklerini 
		// bitkiler sınıfınında kullanabililyor olmasını göstermek

		String solunum;

		public bitkiler(int bbb,int aaa,String isimmm,String s){

			super.boyu=bbb;
			super.agirlik=aaa;
			super.ad=isimmm;
			this.solunum=s;

		}

		public static void main(String[] args) {

			bitkiler b1=new bitkiler();
			b1.ad="lahana";
			b1.agirlik=2;
			b1.boyu=5;
			b1.cins="sebze";
			b1.solunum="fotosentez";
			b1.yazdir();
		}

}

```
>> 
    

```java
