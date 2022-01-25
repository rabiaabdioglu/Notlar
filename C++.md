
## Tüm Basit C++ Ornekleri #
- [Tüm Basit C++ Ornekleri](#Tüm-Basit-C++-Ornekleri)
- [Tüm Basit C++ Ornekleri](#Tüm-Basit-C++-Ornekleri)
- [Tüm Basit C++ Ornekleri](#Tüm-Basit-C++-Ornekleri)
- [Tüm Basit C++ Ornekleri](#Tüm-Basit-C++-Ornekleri)
- [Tüm Basit C++ Ornekleri](#Tüm-Basit-C++-Ornekleri)
- [Tüm Basit C++ Ornekleri](#Tüm-Basit-C++-Ornekleri)
- [Tüm Basit C++ Ornekleri](#Tüm-Basit-C++-Ornekleri)
- [Tüm Basit C++ Ornekleri](#Tüm-Basit-C++-Ornekleri)
- [Tüm Basit C++ Ornekleri](#Tüm-Basit-C++-Ornekleri)
- [Tüm Basit C++ Ornekleri](#Tüm-Basit-C++-Ornekleri)
- [Tüm Basit C++ Ornekleri](#Tüm-Basit-C++-Ornekleri)
- [Tüm Basit C++ Ornekleri](#Tüm-Basit-C++-Ornekleri)
- [Tüm Basit C++ Ornekleri](#Tüm-Basit-C++-Ornekleri)
- [Tüm Basit C++ Ornekleri](#Tüm-Basit-C++-Ornekleri)





##Sayi Karşilaştirma  

```
#include <iostream>

using namespace std;


int main()
{
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
}
```

## Harf notu hesabı  

```

#include <iostream>

using namespace std;


int main()
{
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
}

