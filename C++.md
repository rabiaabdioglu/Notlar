
##  C++ Ornekleri #
- [Sayi Karşilaştirma](#Sayi-Karşilaştirma)
- [Harf notu hesabı](#Harf-notu-hesabı)
- [Basit dört işlem](#Basit-dört-işlem)
- [Sıfırdan girilen sayiya kadar sayilarin toplam, adet ve ortalamasi](#Sıfırdan-girilen-sayiya-kadar-sayilarin-toplam,-adet-ve-ortalamasi)
- [Faktoriyel bulma](#Faktoriyel-bulma)
- [Girilen sayilarin toplami](#Girilen-sayilarin-toplami)
- [Negatif değer girilene kadar değer alma](#Negatif-değer-girilene-kadar-değer-alma)
- [100 e kadar olan asal sayilar](#100-e-kadar-olan-asal-sayilar)







##Konsol ekranında türkçe karakter kullanımı için  

```
setlocale(LC_ALL, "Turkish");


```


>>		 Continue -  Alt satırlar atlanır. 
>>		 Break	  -  Döngüden çıkılır



##Sayi Karşilaştirma  

```

	int sayi1, sayi2;

	cout << "iki sayi giriniz: ";
	cin >> sayi1 >> sayi2;
   
	if( sayi1<sayi2)
	{   
		cout << sayi1<<"\t" <<sayi2 <<"den kucuk...\n";
	}
   
	if( sayi1>sayi2)
	{
		cout << " sayi1 sayi2 den buyuk...\n";
	}
	
	if( sayi1==sayi2)
	{
		cout << " sayi1 sayi2 ye esit...\n";
	}
	return 0;

```

## Harf notu hesabı  

```

	int vize, final;

	cout << "Vize ve Final notunu giriniz: ";
	cin >> vize >> final;

	float ortalama = (vize * 0.4 + final * .6);

	cout << "OrtalamanÄ±z : " << ortalama;

	if (ortalama >= 90)				
		cout << "A";
	else if (ortalama >= 80)	
		cout << "B";
	else if (ortalama >= 70)	 
		cout << "C";
	else if (ortalama >= 60)	  
		cout << "D";
	else if (ortalama >= 50)	
		cout << "E";
	else						 
		cout << "F";

	system("pause");

	return 0;


```

## Basit dört işlem  

```

	char islem;
	float sayi1, sayi2;

	cout << "Bir işlem seçin (+, -, *, /): ";
	cin >> islem;

	cout << "Sayilari girin: ";
	cin >> sayi1 >> sayi2;

	switch (islem)
	{
	case '+':
		cout << sayi1 << " + " << sayi2 << " = " << sayi1 + sayi2;
		break;
	case '-':
		cout << sayi1 << " - " << sayi2 << " = " << sayi1 - sayi2;
		break;
	case '*':
		cout << sayi1 << " * " << sayi2 << " = " << sayi1 * sayi2;
		break;
	case '/':
		cout << sayi1 << " / " << sayi2 << " = " << sayi1 / sayi2;
		break;
	default:
		cout << "Hata!...";
		break;
	}




```

## Sıfırdan girilen sayiya kadar sayilarin toplam, adet ve ortalamasi  

```


	int tekToplam = 0, ciftToplam = 0;
	int tekSayac = 0, ciftSayac = 0,sayi;
	
	cout<<"Sayi giriniz"<<endl;
	cin>>sayi;

	for (int i = 1; i <=sayi; i++)
	{
		if (i % 2 == 0)		
		{
			ciftToplam += i;
			ciftSayac++;

		}
		else
		{
			tekToplam += i;
			tekSayac++;
		}
	}

	cout<<"\nCift sayilarin   :   \n\n  Toplami =  "<<ciftToplam;
	cout<<"\n  Adedi =  "<<ciftSayac;
	cout<<"\n  Ortalamasi =  "<<ciftToplam/ciftSayac<<"\n\n";

	cout<<"\nTek sayilarin   :   \n\n  Toplami =  "<<tekToplam;
	cout<<"\n  Adedi =  "<<tekSayac;
	cout<<"\n  Ortalamasi =  "<<tekToplam/tekSayac<<"\n\n";


```

##  Faktoriyel bulma  

```
	int sayi , faktoriyel=1;
	cout << "Sayi girin : "; 
	cin >> sayi; 

	for (int i = 2; i <= sayi; i++)	faktoriyel *= i; 	
	
	//2 den girilen sayiya kadar çarpım yapılır
	
	cout << sayi << "! = " << faktoriyel << endl;

```

## Girilen sayilarin toplami  

```
	int sayac=0;
	int toplam=0;
	while(sayac<10)
	{	int sayi;
		cout<<sayac<< ". Sayi  -> : ";
		cin>>sayi;
		toplam+=sayi;
		sayac++;
	}
	cout<<"\n Toplam =  "<< toplam <<endl;
```

## Negatif değer girilene kadar değer alma  

```

unsigned long x;
do {
cout<< "Bir sayi giriniz : ";
cin>> x;

}
while (x>=0);
cout<<"Negatif değer girildi..."<<endl;


```


## 100 e kadar olan asal sayilar  



```
	int sayi;
	bool asal;	

	for (int i = 2; i <= 100; i++)
	{  asal = true;

		
		for (int j = 2; j < i; j++)
		{
		if (i%j == 0)
		{	asal=false;
			break;	}}
			
		if(asal) cout << i <<"\n" ;
	}
```

## Harf notu hesabı  

```




















