##  C Ornekleri #
- [Tüm Basit C Ornekleri](#Tüm-Basit-C-Ornekleri)
- [Girilen sayıların toplam ortalama ve sayisi](#Girilen-sayıların-toplam-ortalama-ve-sayisi)
- [Girilen 10 adet sayının tek ve çift olanlarının adet,ortalama ve toplam](#Girilen-10-adet-sayının-tek-ve-çift-olanlarının-adet,ortalama-ve-toplam)
- [Çarpma kullanmadan toplama işlemi ile sonuç](#Çarpma-kullanmadan-toplama-işlemi-ile-sonuç)
- [Basamak toplamı](#Basamak-toplamı)
- [Girilen sayılar arasındaki çift sayılar](#Girilen-sayılar-arasındaki-çift-sayılar)
- [Girilen sayının faktöriyel sonucunu bulan](#Girilen-sayının-faktöriyel-sonucunu-bulan)
- [Karenin alan ve çevresi](#Karenin-alan-ve-çevresi)
- [Ödev vize ve final ortalamasına göre harf notu](#Ödev-vize-ve-final-ortalamasına-göre-harf-notu)
- [Asal sayi](#Asal-sayi)
- [Çarpım Tablosu](#Çarpım-Tablosu)
- [Dört işlem hesap makinesi](#Dört-işlem-hesap-makinesi)
- [10 kişilik sınıftaki not ortalamasi ve kalanlarin sayisi](#10-kişilik-sınıftaki-not-ortalamasi-ve-kalanlarin-sayisi)
- [Fonksiyonlara giriş](#Fonksiyonlara-giriş)
- [Fonksiyon örneği- Yollanan dizinin ortalama ve toplamı](#Fonksiyon-örneği--Yollanan-dizinin-ortalam-ve-toplamı)
- [Sayaç](#Sayaç)
- [Fonksiyon örneği- Girilen cumlendeki sesli harflerin indexini bulma](#Fonksiyon-örneği--Girilen-cumlendeki-sesli-harflerin-indexini-bulma)
- [Dizinin içerisine rastgele sayi atama, atılan sayı kadar yıldız yazdırma](#Dizinin-içerisine-rastgele-sayi-atama,-atılan-sayı-kadar-yıldız-yazdırma)
- [Girilen iki stringi birlestirme](#Girilen-iki-stringi-birlestirme)



## Girilen sayıların toplam ortalama ve sayisi

```
#include"stdio.h"


main()

{
int sayi,adet=0,toplam=0;
float ortalama;

printf("Sayı gir:	");
scanf("%d",&sayi);

while(sayi>0)
{
toplam+=sayi;
adet++;
printf("Sayı Gir:	");
scanf("%d",&sayi);

}
ortalama=toplam/(adet*1.0);
printf("%d adet sayı girildi",adet);	
printf("\nToplam=%d",toplam);
printf("\nOrtalama=%.2f",ortalama);}
```


## Girilen 10 adet sayının tek ve çift olanlarının adet,ortalama ve toplam




```
#include"stdio.h"
main()
{
	int sayi,c_ad=0,c_t=0,t_ad=0,t_t=0;
	float c_o,t_o;
	
	for(int i=0;i<10;i++)
	{
	printf("%d.sayigir:	",i+1);
	scanf("%d",&sayi);
	
	if(sayi%2==0)
	{
		
		c_ad++;
		c_t+=sayi;
	}
		else{
		t_ad++;
		t_t+=sayi;
		
		
	}}
	t_o=t_t/(t_ad*0.1);
	
	c_o=c_t/(c_ad/0.1);
	
	printf("\n%d cif toplam=%d ortalama= %.2f",c_ad,c_t,c_o);
	
	printf("\n%d tek toplam=%d ortalama= %.2f",t_ad,t_t,t_o);
	

}
```

## Çarpma kullanmadan toplama işlemi ile sonuç  

```

#include"stdio.h"


main(){
	
	int a,b,sonuc=0;
	
	printf("ilk sayi gir:	");
	scanf("%d",&a);
	
	
	printf("ikinci sayi gir:	");
	scanf("%d",&b);
	 
	 
	 for(int i=0;i<a;i++){
    	sonuc+=b;
	 	
	 	
	 }
	
printf("%d *  %d	=	%d",a,b, sonuc);	
}

```
## Basamak toplamı

```


main(){
	
	int sayi,basamak,toplam=0;
	printf("sayı gir:	");
	scanf("%d",&sayi);
	int yedek=sayi;
	
	while(sayi!=0)
	{
		basamak=sayi%10;
		toplam+=basamak;
		sayi/=10;
		
		
		
		
	}
	
	printf("%d sayisinin basamak toplamı = %d", yedek, toplam);
	

	 } 


```

## Girilen sayılar arasındaki çift sayılar 


```
#include"stdio.h"

main(){
	
	int a,b;
	printf("sayıları gir:	");			scanf("%d%d",&a,&b);
	
	
	if(a<=b){
      for(int i=a;i<=b;i++)   
 	  	{
 			  	if(i%2==0)
 			  	printf("%d\n",i);
 		
		 }}
 	else{
			for(int i=b;i<=a;i++)   
 		{
 				if(i%2==0)
 				printf("%d\n",i);
 		
		 }	}	}
```
## Girilen sayının faktöriyel sonucunu bulan

```
#include"stdio.h"

main(){
	
	int sayi,sonuc=1;
	printf("sayi gir:	");
	scanf("%d",&sayi);
	
 	for(int i=2;i<=sayi;i++)   //	for(int i=sayi;i<=2;i--)  de olabilir.
 	{
 		sonuc*=i;
 		
 		
	 }
	
	
	printf("%d !  = %d",sayi,sonuc);
}

```
## Karenin alan ve çevresi
```
#include <stdio.h>

main()
{
	int kenar,alan,cevre;
	
	printf("Karenin kenarını girinizi= ");
	scanf("%d",&kenar);
	
	alan=kenar*kenar;
	cevre=4*kenar;
	
	printf("ALAN = %d\n",alan);/* \n komudu bir alt satıra geçirir*/
	printf("ÇEVRE = %d\n",cevre);
}
``` 
## Ödev vize ve final ortalamasına göre harf notu
```
#include"stdio.h"

main()
{
	
	float o,v,f;
	
	printf("odev giriniz:	"); scanf("%f/n",&o);
	

	printf("vize giriniz:	"); scanf("%f/n",&v);
	
	printf("final giriniz:	"); scanf("%f/n",&f);
		
   
 
   if (o>100 || v>100 || f>100 || o<0 || v<0 || f<0 )
   { 
   printf("hatali not girildi");
   
   } 
   
   else {
      float ort=(o*0.2)+(v*0.3)+(f*0.5);
	
	printf("ortalamaniz: %.2f	",ort);
	

	
 if(ort>=85)
  {
 	printf("Harf notunuz:	AA");
 	
 } 
 else if(ort>=70 && ort<85){
 	printf("Harf notunuz:	BB");
 	
 
}
 else if(ort>=50 && ort<70){
 	printf("Harf notunuz:	CC");
 	
 
}
	
	 else if(ort>=30 && ort<50){
 	printf("Harf notunuz:	DD");
 	
 
}
	
	 else if(ort<30){
 	printf("Harf notunuz:	FF");
 	
 
}

	 else {
 	printf("Hata!");}}}
  ```
  
## Asal sayi 
```
  
  #include"stdio.h"
main()
	
	
{
	int s=0;
	for(int i=2;i<100;i++){
		for(int k=2;k<i;k++){
			if(i%k==0){
	                            	//	printf("%d  -  %d\n",i,k);		
			s++;//farketmez
			}
	
	
 }
	 
	if(s==0)
	printf("%d asal sayidir",i);
	s=0;
printf("\n");
}	}
```
## Çarpım Tablosu
```
#include"stdio.h"
main(){
	
	
	 printf("----------CARPIM TABLOSU----------\n");
	 printf("\ni\tXk\t\n");
	for(int i=2;i<10;i++)
	{
			for(int k=1;k<=10;k++){
				int a=k*i;
				printf("\n%d\tX%d\t=%d",i,k,a);
				
				
			}
			printf("\n-------------------------");	}}
```
## Dört işlem hesap makinesi
```
#include <stdio.h>

main()
{
	int a,b,sonuc;
	char islem,cevap;
	 	
 do
   {
  	printf("+ - * /    Islemlerinden birini seciniz = ");
	scanf("%c",&islem);
	
	printf("\nSayi Giriniz =  \n");
	scanf("%d%d",&a,&b);

	switch(islem)
	{
		case '+':  printf("Sonuc = %d",a+b);	break;
		case '-': printf("Sonuc = %d",a-b); break;
		case '*': printf("Sonuc = %d",a*b); break;
		case '/': printf("Sonuc = %.2f",a/(b*1.0)); break;
		default: printf("Hatali islem ");
}
	printf("\nDevam Etmek İstiyor musunuz?(E/H)\n");scanf("%c",&cevap);		
	 	
	  }
while (cevap!='E');


}
```
## 10 kişilik sınıftaki not ortalamasi ve kalanlarin sayisi
```

#include"stdio.h"
main(){
		int notlar[10];
		int toplam=0; 
	    int gad=0,kad=0;
		float ort;
		int inde1,inde2;
	for(int i=0;i<10;i++){
	
	printf("%d.index giriniz : ",i);
	scanf("%d",&notlar[i]);
    toplam+=notlar[i];
    
}
 	 ort=toplam*1.0/10;
  
 	 printf("\n\n\nNotlarin Toplami : %d  -  Ortalamasi  :  %.2f\n\n\n\n",toplam,ort);
 

 	 for(int i=0;i<10;i++){
  	
		   if(notlar[i]>=ort)	{printf("\n+		%d.index %d ile gecti",i,notlar[i]); gad++;}
	       else{ printf("\n-		%d.index %d ile kaldi",i,notlar[i]); kad++;
	  } }

	 printf("\n\n\n\n\nGecenlerin sayisi = %d\n\nKalanlarin sayisi %d\n\n\n\n\n",gad,kad);
	
	int enb,enk;
	enb=enk=notlar[0];

	for(int i=0;i<10;i++){      
	 if(notlar[i]>enb) {	 enb=notlar[i];	
	   inde1=i; }
	 else if(notlar[i]<enk){ enk=notlar[i];	
	  inde2=i;}	}
	 
	printf("\n\n\nEn yüksek not  :  %d  -  %d. index \n\n En dusuk not  :  %d  -  %d. index\n\n\n",enb,inde1,enk,inde2);
	
	
} 

```
## Fonksiyonlara giriş
```
#include"stdio.h"
#include <conio.h> 


 int sayigir(int x)
 {
 	int sayi;
 	printf (" %d. sayi gir: ",x+1);
 	scanf("%d",&sayi);
 return sayi;
 }
  void diziyaz(int z[]){

	 for (int i=0;i<5;i++)	printf ("\n %d ",z[i]);
 }
main(){	
	int sayi[5];
	 
	 
	 for (int i=0;i<5;i++)
	{  sayi[i]=sayigir(i);
		
	}
	diziyaz(sayi);
	
}
```
## Fonksiyon örneği- Yollanan dizinin ortalama ve toplamı
```

#include"stdio.h"
#include <conio.h> 

 int sayigir(int x)
 {
 	int sayi;
 	printf (" \n%d. sayi gir: ",x+1);
 	scanf("%d",&sayi);
 	
 return sayi;
 
 }
  void diziyaz(char isim,int z[]){
   printf("\n %c dizisi yazdiriliyor.",isim);
   for (int i=0;i<5;i++)	printf ("\n %d ",z[i]);

	 
 }
 void topla(int a[],int b[]){
 	
	 for (int i=0;i<5;i++)  
	 printf("\n%d + %d = %d",a[i],b[i],a[i]+b[i]);
 
 }
float diziort (int dizi[])
  { int top=0;
    for (int i=0;i<5;i++) {
    top+=dizi[i];
    }
    return top/5.0;
 }
main(){	
	int a[5],b[5]; 
  float ort;
	 
	 
	 for (int i=0;i<5;i++)  a[i]=sayigir(i);
	 for (int i=0;i<5;i++)  b[i]=sayigir(i);
  
	
	 diziyaz('A',a);	
   
   printf("\n--------------------------\n");
    
   diziyaz('B',b);
    
   printf("\n--------------------------\n");
   
   topla(a,b);
    
   printf("\n--------------------------\n");
   printf("\n--------------------------\n");
	
	 ort=diziort(a); printf("\nA dizisi ortalamasi = %.2f ",ort);	 
	 ort=diziort(b); printf("\nB dizisi ortalamasi = %.2f ",ort);
	
		}	
```
## Sayaç
```

#include"stdio.h"
#include"unistd.h"
main(){
	
	
	 
int sa=0, dk=0,sn=0,i;
while(1){
	
	for(i=0;i!=23;i++){

	printf("\n");
	if(sn==60){ sn=0;dk++;
	
	}
	if(dk==60){dk=0;sa++;
	}
	printf("%d:%d:%d",sa,dk,sn);
	sleep(1);
	sn++; 	}
}
		}
    
 ```
## Fonksiyon örneği- Girilen cumlendeki sesli harflerin indexini bulma


```
	#include "stdio.h"
  #include "string.h"
 
 
 int karakter_bul(char dizi[],char x)
 {
 	int sayac=0;
 	for(int i=0; i<strlen(dizi); i++)
 	{
 	   if(dizi[i]==x)  sayac++;	
	}
	return sayac;
 }
 
  int index_bul(char dizi[],char x)
 {
 	int sayac=0;  int index[strlen(dizi)];
 	for(int i=0; dizi[i]!='\0'; i++)
 	{
 	   if(dizi[i]==x) {index[sayac]=i; sayac++;}
 	}
	for(int i=0; i<sayac; i++)   printf("\n%d.indexte",index[i]);
	return sayac;
}

	
 
 
main()
{
	printf("Cumle yazin \n",i,isim[i]);

	char isim[100];
	gets(isim);
	char sesli_harfler[]={'a','e','i','o','u','\0'};
	int sayac=0;
	
	
	for(int i=0;i<strlen(isim);i++)
	{
		for(int k=0;k<strlen(sesli_harfler);k++)
		{
			if(isim[i]==sesli_harfler[k])
			{
				sayac++;
			printf("\n%d.indexte %c vardir",i,isim[i]);
			}
			
		}
	}
	printf("\n%d adet sesli harf vardir.",sayac);
	
	
  	char karakter;
	printf("\naranacak karakter gir: ");  scanf("%c",&karakter);
	
	printf("\n%d adet vardir",karakter_bul(isim,karakter));
	index_bul(isim,karakter);

   
}

```
## Dizinin  içerisine rastgele sayi atama, atılan sayı kadar yıldız yazdırma
```
	#include"stdio.h"
#include"stdlib.h"
#include"time.h"
#define x 10 // tüm 5 değerleri yerine x yazılır değer değiştiğinde x te değişir bkz. a[x ]

main()


	
{
        int a[x];
		srand(time(0));
		for (int i=0;i<x;i++){
	
    a[i]=rand()%10;
	
    printf("%d. sayi  %d\n",i+1,a[i]);
}

for(int i=0;i<x;i++){
printf("\n%d -> ",a[i]);
	for(int k=0;k<a[i];k++){
printf("*");

	}printf("\n");
}



```
## Girilen iki stringi birlestirme
```
#include "stdio.h"
#include "string.h"

void str_kopyala(char kelime1[],char kelime2[])  //kopyalama fonksiyonu
{
	int i=0;
	while(kelime2[i]!='\0')
	{
		kelime1[i]=kelime2[i];
		i++;
	}
	kelime1[i]='\0';// diğer kelime ondan uzunsa hata verir
	
	puts(kelime1);
}

int uzun_bul(char yazi[]) //birleştirme fonksiyonu için gerekli başka bir fonksiyon 
	{
		int sayac=0;  while(yazi[sayac]!='\0')  sayac++;  return sayac;
	}

void str_birlestir(char kelime1[],char kelime2[])   //birlestirme fonksiyonu 
{

      int uzn_s1=uzun_bul(kelime1);
      int uzn_s2=uzun_bul(kelime2);
      char kelime3[uzn_s1+uzn_s2];

      int i=0;
      for(;i<uzn_s1+uzn_s2;i++)
      {
        if(i<uzn_s1)
        kelime3[i] = kelime1[i];
        else
        kelime3[i]=kelime2[i-uzn_s1];
      }
      kelime3[i]='\0';
      str_kopyala(kelime1,kelime3);
	
}


main()
{
      char s1[100],s2[100];

      puts("1.string gir: ");  gets(s1);
      puts("2.string gir: ");  gets(s2);

      /*strcpy(s1,s2);  //s2 deki veriler s1'e kopyalanıyor
      puts("kopyalama islemi sonrasi 1.string");
      puts(s1);*/

    	//str_kopyala(s1,s2);   //kendimiz fonksiyonla kopyalıyoruz
	
      /*	strcat(s1,s2);// ikisini birleştiriyor
      puts("birlestirme islemi sonrasi 1.string");
      puts (s1);*/
	
    	str_birlestir(s1,s2);   //kendimiz fonksiyonla birlestiriyoruz
	
}

