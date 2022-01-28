
## Java Ornekleri


- [Sayi Karşilaştirma](#Sayi-Karşilaştirma)




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
public static void main(String[] args) {

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
			
		
		System.out.println(a+">"+b+">"+c);}

```
    
    
## String sınıfı metodları 

    > .toLowerCase()
		> Methodu cağıran metin ifadesinin(dizgi) nesnesinin tamamen
		> küçük harfe çevrilmiş halini geri verir.

	```java	 
				string kelime="MERHABA";
				string kkelime=kelime.toLowerCase();
		```
		> .toUpperCase();
		> Methodu çağıran dizgi nesnesini tamamen büyük harfe çevrilmiş
		> olan dizgi verir.

	```java	 		
				string kelime="merhaba";
				string bkelime=kelime.to.UpperCase();
  ```			
		> .substring(Başlangıç)
		> Methodu çağıran dizgi nesnesinin başlangıç numaralı karekterinden
		> dizginin sonuna kadar olan bölümünü bir dizgi olarak geri verir.
```java
		
				string kelime="merhaba";
				string parçala=kelime.substring(4);
```
				
		> .substring(Başlangıç,son)
		> Methodu çağıran başlangıç numaraları karakterinden son numaralı
		> karakterine kadar olan bölümünü bir dizgi olarak geri verir.
```java

				string kelime="merhaba";
				string oarçala=kelime.substring(1,4); erh
				string kelime="bilgisayar";
				string oarçala=kelime.substring(1,4); gi
				string kelime="enes rabia";
				string oarçala=kelime.substring(2,7); es ra
```
				
		> .indexOf(bir dizi)
		> String üzerinde bir dizgin ile kayıtlı ilk görüldüğü noktayı bulur.
		> Eğer bir dizgi dizgisinin içinde yoksa -1 değerini verir.
```java
				
				string kelime="nur nur nur";
				int a = kelime.indexOf("nur"); 0
				int a = kelime.indexOf("r"); 2
				System.out.println(a);
```		
		> .indexOf(dizgi,başlangıç)
		> Bir dizgi üzerinde başlangıç numaralı karekterden sonra başka bir
		> dizginin ilk görüldüğü noktayı bulur,yoksada -1 döndürür.
				
```java
				string kelime="nur nur nur";
				int a = kelime.indexOf("nur",5); 8
```
		
		> .lastindexOf(dizgi)
		> Dizgi üzerinde bir dizgi ile tanımlı başka bir dizginin son 
		> görüldüğü noktayı bulur.Eğer dizgi içinde yoksa sonuç olarak -1 
		> değerini verir.
				
```java

				string kelime="nur nur nur";
				int a = kelime.lastIndexOf("nur"); 8
```
				
		> .length()
		> Dizgi nesnesinin içinde bulunan karekter sayısını verir.
```java
				
				String kelime = "fatma nur";
				int a = kelime.length();
				System.out.printIn(a);
```

		> .trim()
		> Dizginin başındaki ve sondaki boşlukları silindiği bir dizgi
		> geri verir.
```java
				
				string kelime = " enes kılıç ";
				string at = kelime.trim();
 ```		
		> .charAt(konum)
		> Dizginin üzerinde yer alan konum numaralı karekteri geri verir.
```java
				
				string kelime="merhaba";
				char a = kelime.CharAt(3); h
```				
		> .compareTo(dizgi)
		> Methodu çağıran nesne ile dizgi nesnesini alfabetik olarak
		> karşılaştırır.Eğer methodu çağıran nesne daha kuçuk ise method
		> sıfırdan daha küçük bir değer verir.eğer iki dizgi eşitse sıfır
		> verir.Eğer methodu çağıran nesne büyükse 0 dan büyük değer verir.
```java
				 
				 String kelime="merhaba";
				 int a = kelime.compareTo("merhaba"); 1
				 System.out.println(a);
```
				
		> .equals()             eşit mi true false döndürür.
		> .equalsIgnoreCase()   büyük küçük önemli değil eşit ise true.
    
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
    
    
## Kullanıcıdan alınan 5 sayi pozitif mii negatif mi 

```java	```
    
    
## Kullanıcıdan alınan 5 sayi pozitif mii negatif mi 

```java	```
    
    
## Kullanıcıdan alınan 5 sayi pozitif mii negatif mi 

```java	```
    
    
## Kullanıcıdan alınan 5 sayi pozitif mii negatif mi 

```java	```
    
    
## Kullanıcıdan alınan 5 sayi pozitif mii negatif mi 

```java	```
    
    
## Kullanıcıdan alınan 5 sayi pozitif mii negatif mi 

```java	```
    
    
## Kullanıcıdan alınan 5 sayi pozitif mii negatif mi 

```java
