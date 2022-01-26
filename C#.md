
## Tüm Basit C Ornekleri #
- [Asal Sayi](#Asal-Sayi)
- [İki sayi arasi toplami](#İki-sayi-arasi-toplami)
- [Girilen sifre kontrolü](#Girilen-sifre-kontrolü)
- [Continue  break](#Continue-break)
- [For ve foreach kullanimi](#For-ve-foreach-kullanimi)
- [ASCII karakterleri](#ASCII-karakterleri)
- [Büyük harf yapma](#Büyük-harf-yapma)
- [Dizideki en büyük ve en küçük sayiyi bulma](#Dizideki-en-büyük-ve-en-küçük-sayiyi-bulma)
- [String içerisinden bir alt string alma](#String-içerisinden-bir-alt-string-alma)
- [Rastgele sayi türetme](#Rastgele-sayi-türetme)
- [String içerisinde char karakter arama](#String-içerisinde-char-karakter-arama)
- [Girilen stringte sesli harf sayisini bulma](#Girilen-stringte-sesli-harf-sayisini-bulma)
- [ArrayList](#ArrayList)
- [Sayisal Loto Ornek](#Sayisal-Loto-Ornek)
- [Fonksiyonlar](#Fonksiyonlar)
- [Overloading ve Params](#Overloading-ve-Params)
- [Math sınıfı](#Math-sınıfı)
- [String sınıfı](#String-sınıfı)
- [Nesne oluşturma](#Nesne-oluşturma)
- [Comboboxa veri atma](#Comboboxa-veri-atma)
- [Dosya İşlemleri](#Dosya-İşlemleri)
    - [Dosya Oluşturma](#Dosya-Oluşturma)
    - [Dosya Silme](#Dosya-Silme)
    - [Dosya var mı kontrolü](#Dosya-var-mı-kontrolü)
    - [Dosya taşıma](#Dosya-taşıma)
    - [Dosya listeleme](#Dosya-listeleme)
    - [Klasör listeleme](#Klasör-listeleme)
    - [Mantıksal sürücüleri listele](#Mantıksal-sürücüleri-listele)
    - [Append ile text dosyası üzerine yazma](#Append-ile-text-dosyası-üzerine-yazma)
    - [Text dosyasını okuma, textboxa yazma](#Text-dosyasını-okuma,-textboxa-yazma)
- [DataTable kullanımı](#DataTable-kullanımı)
- [DataGridview Otomatik](#DataGridview-Otomatik)
- [VeriTabanı Bağlantısı](#VeriTabanı-Bağlantısı)




## Asal Sayi




```
  {
          bool asal = false ;
          Console.Write("Sayıyı Girin : ");
          int sayi = Convert.ToInt32(Console.ReadLine());

            for (int i = 2; i < sayi; i++)
             {
            if (sayi % i == 0)      { asal = true;}}

            if (asal==false) { Console.WriteLine("Girilen Sayı Asal");    }
            
            else Console.WriteLine("Girilen Sayı Asal Değil");
            
 ```


## İki sayi arasi toplami



```            
             int temp = 0;
            Console.Write("Alt sinir giriniz:");
            int altsinir = Convert.ToInt32(Console.ReadLine());// dönüþüm iþlemi ve kul deðer alma

            Console.Write("Üst sinir giriniz:");
            int ustsinir = Convert.ToInt32(Console.ReadLine());

            if(altsinir>ustsinir)
            {
                temp = altsinir;
                altsinir = ustsinir;
                ustsinir = temp;
            }
            int toplam = 0;
            while(altsinir<ustsinir)
            { toplam += altsinir;
                altsinir++;

            }
            Console.WriteLine("Toplam deger:" + toplam);
  ```


## Girilen sifre kontrolü



```               
          int sifre = 1234, sifre2;
            do
            {
                Console.Clear();
                Console.Write("Sifre giriniz:");
                sifre2 = Convert.ToInt32(Console.ReadLine());
                if (sifre == sifre2)
                {
                    Console.WriteLine("Sisteme Hoþgeldiniz..");

                }
            }
            while (sifre != sifre2);
 ```


## Continue  break



```      
            for(int i = 0; i < 100; i++)
            {
                Console.WriteLine(i);
                if (i == 50) continue;
                if (i == 50) break;
            }       
```


## For ve foreach kullanimi




``` 
             int[] notlar = new int[10];
            int toplam = 0;
            double ort ;

            for (int i = 0; i < 10; i++)
            {
                Console.WriteLine("{0}.notu gir:",i+1);
                notlar[i]=Convert.ToInt32( Console.ReadLine());
           

            }
            foreach(int item in notlar) { toplam += item; }
            ort = toplam / (notlar.Length*1.0);
            Console.WriteLine("ortalama = {0}",ort);






 ```


## ASCII karakterleri




``` 
          for (int i = 0; i <= 122; i++) 
          Console.WriteLine(i + "-" + Convert.ToChar(i) + "-" + Convert.ToChar(i + 32) + "-" + (i + 32));

             
```


## Büyük harf yapma




``` 
          Console.WriteLine("Bir yazi gir");
          string yazi = Console.ReadLine();
          string cikti = String.Empty; 
           foreach (char eleman in yazi)
            {
                int deger = (int)eleman;   
                if (deger >= 97 && deger <= 122)
                deger -= 32; 
                else if (deger >= 65 && deger <= 97)
                deger += 32;
                cikti += (char)deger;

            }Console.WriteLine(cikti);
            
                 
```


## Dizideki en büyük ve en küçük sayiyi bulma




```         
              int[] dizi = new int[10] { -9, -2, 0, 1, 10, 11, 19, 1, -1, 4 };
            int eb=dizi[0],ek =dizi[0];
            for (int i = 0; i < 10; i++)
            {if (eb < dizi[i]) eb = dizi[i];
                if (ek> dizi[i]) ek = dizi[i];
            }
            Console.WriteLine("Dizinin en büyügü {0}\nDizinin en kücügü {1}",eb, ek);
          
            
            Console.ReadKey();             
```


## String içerisinden bir alt string alma




```    Console.WriteLine("kelime girin");
            char[] kelime = Console.ReadLine().ToCharArray();

            Console.WriteLine("baþlangýç indexi giriniz :");
            int bas = Convert.ToInt16(Console.ReadLine());

            Console.WriteLine("uzunluk sayýsý  giriniz :");
            int uzunluk = Convert.ToInt16(Console.ReadLine());


            char[] yenidizi = new char [uzunluk];
            for (int i = bas; k=i ; i >(bas-uzunluk); i--;k++)
            {
                yenidizi[bas - i] = kelime[k];

            }
            Console.WriteLine(yenidizi);


            Console.ReadKey();
 ```


## Rastgele sayi türetme




```

            Random rndmsayituret = new Random();//random sýnýfý
            //int rastgelesayi = rndmsayituret.Next(5);        //0dan 5 e kadar 5 dahil deðil
            //int rastgelesayi2 = rndmsayituret.Next();        //herhangi bir tam sayi
            //int rastgelesayi3 = rndmsayituret.Next(5,69);    //5den69a 
            //double rastgelesayi4 = rndmsayituret.Next();     //0dan 1 e 
            int[] sayilar = new int[50];
            for (int i = 0; i < 50; i++)
            {
                sayilar[i] = rndmsayituret.Next(20);           //next(20) -20 ye kadar olan sayilari verir

                Console.WriteLine("{0}\t",sayilar[i]);

            }

            Console.ReadKey(); 
            
 ```


## String içerisinde char karakter arama




```
              Console.WriteLine("kelime girin");
            char[] kelime = Console.ReadLine().ToCharArray();
            Console.WriteLine("aranacak karakteri giriniz :");
            char karakter = Convert.ToChar(Console.ReadLine());


            int[] index = new int [kelime.Length];
            int sayac = 0;
            for (int i = 0; i < kelime.Length; i++)
            {
                if( kelime[i]==karakter)
                {
                    index[sayac] = i;
                    sayac++;

                }

            }
            Console.WriteLine("kac tane "+karakter+"="+sayac);
            for (int i = 0; i < sayac; i++)
            { Console.WriteLine("\n{0} index sýrasý  ",index[i]); }
            {

            }
                          Console.ReadKey();
 ```


## Girilen stringte sesli harf sayisini bulma




``` 
            char[] sesli=new char[] { 'a', 'e', 'ı', 'i', 'o','A','E','I','İ','O' };
            Console.WriteLine("kelime girin");
            string a = Console.ReadLine();
            int sayac = 0;
            int asayac=0, esayac = 0, ısayac = 0, isayac = 0, osayac = 0;
             
                     
            for (int i = 0; i <= a.Length; i++)
            {    for (int k = 0; k < sesli.Length; k++)
                {
            if (a[i] == sesli[k])
                    {
                        Console.WriteLine((i + 1) + "  -------> .indexte" + sesli[k] + "vardir\n");
                        sayac++;

                    }
                    if (a[i] == sesli[0] || a[i] == sesli[5]) asayac++;
                    if (a[i] == sesli[1] || a[i] == sesli[6]) esayac++;
                    if (a[i] == sesli[2] || a[i] == sesli[7]) ısayac++;
                    if (a[i] == sesli[3] || a[i] == sesli[8]) isayac++;
                    if (a[i] == sesli[4] || a[i] == sesli[9]) osayac++;
                }
            }

           Console.WriteLine("{0} ADET SESLi HARF VARDIR.",sayac);
                          Console.ReadKey();
            
 ```


## ArrayList




```
//array listi ve onun fonksiyonlarını  kullanmak için  bir nesne oluşturulması gerek. dinamiktir.
 //diziye eleman ekledikçe boyutu artar ,sildikçe küçülür. normal dizilerde silme olmaz.
 //ekleme veya silme: sondan veya istenilen yere şeklinde olur.
 
 //HAZIR FONKSİYONLAR
 //add :                nesneyi sona ekler.
 //insert:              belirlenen indexten itibaren  yerleştirme yapar.araya yerleştirir.
 //Add.range:           yapıyı sona ekler
 //insertrange:         yapıyı belirtilen indexten sonraya koyar.
 //binary search:       nesne arar
 //capacity             arrayliste sınır belirler.
 //clear :              arraylisti temizler.
 //contains:            eleman var mı yok mu diye kontrol eder booll ile değer döndürür.
 //count:               dizideki eleman sayar boyutunu gösterir.
 //ındexof              indexi verir. yoksa -1 i verir.
 //lastındexof          en son görülen indexi int olarak verir.
 //remove :             verilen elemanı siler
 //removeat :           indexi verilen elemanı siler
 //removerange(5,10):   5.indexten 10 tane siler.
 //reverse :            arraylisti terse çevirir.
 //reverse(3,4):        3. elemandan başlar 4 elemanı terse çevirir
 //sort:                sıralar 0-9  a-z tür uyumu olan verileri...
 //toarray :            array listi klasik diziye çevirir
 //tostring:            stringe çevirir
 //

    class Program
    {
        static void Main(string[] args)
        {

            ArrayList arrayList = new ArrayList();
            arrayList.Add(25);
            arrayList.Add("rabia");
            arrayList.Add('E');
            arrayList.Add(24.5456);
            arrayList.Add(true);

            //birden çok veri türünü içinde barındırabilir.
            //object tüm veri türlerini kapsar.
            
            foreach (object item in arrayList)
            {
                Console.WriteLine(item + "-" + item.GetType());    //gettype türünü verir.
            }

            Console.WriteLine("\n\n\n");
            int[] dizi = new int[5] { 10, 15, 19, 29, 35 };

            //arrayList.Insert(2, false);                           //2. indexe false ekler.
            arrayList.InsertRange(0, dizi);                         //diziyi toplu şekilde arrayliste koyar.
            // arrayList.AddRange (dizi);                           //addrange sonuna ekler.//dizinin eklenenden sonraki değerleri birer index kayar. 



            foreach (object item in arrayList)
            {
                Console.WriteLine(item + "-" + item.GetType());
            }
            Console.WriteLine("\n\n\n");



            //if (arrayList.Contains('x') == false)   arrayList.Add('x');

            //else  Console.WriteLine("zaten var");
          

            object[] xyz = new object[1];
            xyz=arrayList.ToArray();

            foreach (object item in xyz)
            {
                Console.WriteLine(item + "-" + item.GetType());
            }
            Console.WriteLine("\n\n\n");

            Console.ReadKey();
            
 ```


## Sayisal Loto Ornek




```
            //sayisal loto 1 kolonda 6  sayi
            //8 kolon  kupon--- 1 den 50 ye kadar sayi


            ArrayList kolon = new ArrayList();

            Random rastgele = new Random();

            int turetilen_sayi;
            for (int k = 0; k < 8; k++)
            {
          
            for (int i = 0; i < 6; i++)
            {
                turetilen_sayi = rastgele.Next(1, 50);
                if (kolon.Contains(turetilen_sayi) == false)
                { kolon.Add(turetilen_sayi);}
                else
                {i--;}   
            }
               

 
            kolon.Sort();
            foreach (int item in kolon)
            {
                Console.Write(item + "\t");
            }
            
             Console.WriteLine();
                kolon.Clear();
            }

            Console.ReadKey();
            
 ```


## Fonksiyonlar




```
        static void Main(string[] args)
        {

            int a, b, secim, sonuc = 0;
            menu_goster();
            secim = sayi_gir();
            Console.WriteLine("Sayi girin");a = sayi_gir();
            Console.WriteLine("Sayi girin");b = sayi_gir();

            switch (secim)
            {
                case 1:yazdir(topla(a,b)); break;
                case 2: yazdir(cikar(a, b)); break;
                case 3: yazdir(carp(a, b)); break;
                case 4: yazdir(bol(a, b)); break;

                default:
                    Console.WriteLine("Hatali");
                    break;
            }

            //int a = 5, b = 8;
            //Console.WriteLine(topla(a,b));

            Console.ReadKey(); 
        }

     

        private static int sayi_gir()
        {
            return (Convert.ToInt32(Console.ReadLine()));
        }

        private static void menu_goster()
        {
            Console.WriteLine("1-Topla\n2-Çıkar\n3-Carp\n4-Bol");
         }

        private static void yazdir(object x)
        {
           Console.WriteLine("Sonuc  "+x); 
        }
        private static object bol(int a,int b)
        {
            return (a*1.0) / (b*1.0);    }

        private static int topla(int a, int b)
        {
            return a + b;
        }

        private static object carp(int a, int b)
        {
            return(a * b);
        }


        private static object cikar(int a, int b)
        {
            return (a-b);
        }

            
 ```


## Overloading ve Params




``` static void Main(string[] args)
        {
            //OVERLOADİNG
            //params değişken sayıda parametre oluşturma

            // overloadingte uygun bir  fonk varsa overloading yapılır. paramsı görmez
            yazdir(6,8);
            yazdir(1,2,3);
            yazdir();
          //  yazdir(5, 6, 9, 2, 8, 7, 9, 3, 2, 1, 7);
          //  yazdir(1, 2,90,85,52, 3);

         
       Console.ReadKey(); }

        private static void yazdir()

        private static void yazdir(int v1, int v2, int v3)
        { Console.WriteLine(v1+v2+v3);}
        
        private static void yazdir(int v1, int v2)
        { Console.WriteLine(v1 + v2);}
      
      
        private static void yazdir(params int[] gelensayi)
        {  Console.WriteLine("Eleman sayisi    "+ gelensayi.Length);
           foreach (int item in gelensayi)
            { Console.WriteLine(item);  }
            Console.WriteLine("-------------------------------");
        }
        
        
        
             
 ```


## Math sınıfı




```    
        
        
        
         class Program
    {
        static void Main(string[] args)
        {
            double sayi = Convert.ToDouble(Console.ReadLine());
            Console.WriteLine(Math.Max(3,5));
            Console.WriteLine(Math.Min(3, 5));
            Console.WriteLine(Math.Abs(-5));
            Console.WriteLine(Math.Sign(-9));
            Console.WriteLine(Math.Pow(-2,3));
            Console.WriteLine(Math.Exp(9));
            Console.WriteLine(Math.Sqrt(121));
            Console.WriteLine(Math.Floor(sayi));
            Console.WriteLine(Math.Ceiling(sayi));
            Console.WriteLine(Math.Round(sayi));
            Console.WriteLine(Math.Round(sayi, 2));



            Console.WriteLine();

            // Kendi fonksiyonlarımız ile 
            
            Console.WriteLine(Matematik.buyukBul(5,32));
            Console.WriteLine(Matematik.kucukBul(5, 10));
            Console.WriteLine(Matematik.mutlak(-45));
            Console.WriteLine(Matematik.isaretBul(-3));
            Console.WriteLine(Matematik.kareAl(3,3));
            Console.WriteLine(Matematik.KarekokAl(9));

            Console.ReadKey();
        }
    }
    
    class Matematik
    {
        public static int buyukBul(int a, int b) {
            if (a > b) return a;
            else return b;
        }

        public static int kucukBul(int a, int b)
        {
            if (a < b) return a;
            else return b;
        }

        public static int mutlak(int a)
        {
            if (a > 0) return a;
            else return -a; ;
        }

        public static int isaretBul(int a)
        {
            if (a > 0) return 1;
            else if (a == 0) return 0;
            else return -1;
        }
        public static int kareAl(int a, int b)
        {
            int sonuc = 1;
            for (int i = 0; i < b; i++) { sonuc *= a; } return sonuc;

        }
        public static int KarekokAl(int a)
        {
            int i = 1;
            for (; i < a; i++)
            {
                if (i * i == a) break;  }return i;

        } 

    }
    
                 
 ```


## String sınıfı




``` 
    

length trim 

to lower upper ı +32 veya-32 şeklinde

dsubstring  string içindeki stringi alma baş ve karakter sayisi verilir


insert
parça al ve yerleştir fonk

replace değiştirme 
(eski metin, yeni metin) şeklinde

remove silme baştan bu kadar karakter sil
yeni diziye atar

index of aranan ifadenin nereden başladığını döndürür


split kelimeyi istenilen kadar parçaya bölme
string dizi ye parça parça atar


join iki karakteri birleştirme
cümle şeklinde olabilir
kelime=dizi(i)*' '

empty dizi içindekileri sıfırlar

pad left-right başı veya sonunu doldurma


ısletter
aranan harf mı diye bakar bool döndürür.

ısdigit
aranan rakam mı diye bakar bool döndürür. ondalık rakam değil 

ısnumber
aranan sayımı mı diye bakar bool döndürür.

ısletterordigit
harf veya rakammı diye bakar. nokt işareti yok

ıspunctutation 
noktalama varmı bakar

ıslower()upper küçükmü büyükmü bool döndürür
ıswhitespace boşluk varmı diye bakar

ısseperator kelimeleri ayırmak için kullanılır/ _-

ıssembol  %+$ varmı diye bakar
    
                 
 ```


## Nesne oluşturma




``` 
    
         class Program
    {
        static void Main(string[] args)
        {

            kare nesne1 = new kare();
            nesne1.kenar_uzunlugu = 15;
            Console.WriteLine("Alan = "+nesne1.alan_hesapla());
            Console.WriteLine("Çevre = " +nesne1.cevre_hesapla());
            nesne1.kare_ciz();
           
        }

    }

    class kare
    {  public int kenar_uzunlugu;

        public int alan_hesapla()    { return kenar_uzunlugu * kenar_uzunlugu;  }
        public int cevre_hesapla()   { return kenar_uzunlugu * 4; }
     
        public void kare_ciz()       {
        
            for(int i=0;i<kenar_uzunlugu;i++)
             {
             for (int k = 0; k <kenar_uzunlugu; k++)
               { Console.Write("-"); } Console.WriteLine();    }
               
      Console.ReadKey();
        }
       
    }
    
                   
 ```


## Get Set




``` 
     class Program
    {
        static void Main(string[] args)
        {

    

            tarih obtarih = new tarih();
            Console.WriteLine("deðer atamasý yapýlmadan önce");
            Console.WriteLine(obtarih.tarihgoster());

            obtarih.gunoku = 04;
            obtarih.ayoku = 01;
            obtarih.yiloku = 2019;

            Console.WriteLine("deðer atamasýndan sonra");
            Console.WriteLine(obtarih.tarihgoster());
            Console.ReadKey();


        }

    }


    class tarih
    {

        private int G, A, Y;
        public tarih()
        {
            G = 1;A = 1;Y = 2000;
        }

        public int gunoku
        {
            get { return G; }
            set { G = value; }
        }
        public int ayoku
        {
            get { return A; }
            set { A = value; }
        }
        public int yiloku
        {
            get { return Y; }
            set { Y = value; }
        }

        public string tarihgoster()
        {
            return G.ToString() + "." + A.ToString() + "." + Y.ToString();
        }

    }
```


## Comboboxa veri atma


                
 ```
      baglanti.open();

      oledbcommand combo_ekle =new oledbcommand
      ("select ders_adi from tbl_ders",baglan);
      
      oledbdatareader combo_oku_combo_ekle.executereader();

      while(comb_oku.raed())
      {
      combobox1.ıtems.add(combo_oku["dera_adi"].tostring());

      }


baglanti.close();      


 ```


## Dosya İşlemleri


>> programlamada ters / farklı anlamı var bu yüzden dosya adresinde ters/ hata verir.
>> üç yöntem var  :  1. çift  \\    -     2. düz /    -    3. string başına  @""      -->  özel karakter yok demek
>>


   ## Dosya Oluşturma
                
 ```
 
  Directory.CreateDirectory("C:/Users//OneDrive/Masaüstü");  
  
  Directory.CreateDirectory(textBox1.Text);               //  -- textbox1 dosya yoludur

       
                       
 ```  
   ## Dosya Silme 
 
 ```  
       if (Directory.GetFiles(textBox1.Text).Length != 0 || Directory.GetDirectories(textBox1.Text).Length != 0)
            {
                if (MessageBox.Show("Klasör dolu\nSilinsin mi ?", "Emin Misin?", MessageBoxButtons.YesNo) == DialogResult.OK)
                {
                    Directory.Delete(textBox1.Text, true);
                    // true herhangi bir alt klasör varsa silmeye izin verir
                }
                else { MessageBox.Show("Klasör Silinmedi."); }
            }                           
 
 
 ```
  ## Dosya var mı kontrolü

```

     if (Directory.Exists(textBox1.Text)) {
                MessageBox.Show("Vardır.");

            }
            else
            {
                MessageBox.Show("Yoktur.");
            }
 ```
 ## Dosya taşıma

```

    Directory.Move(textBox1.Text,textBox2.Text);

 ```
 ## Klasör listeleme


```  

string[] klasor = Directory.GetDirectories(textBox1.Text);
            listBox1.Items.AddRange(klasor);

 

 ```
 ## Dosya listeleme


```  
        listBox2.Items.Clear();
          try        //işlemde hata riski varsa dener. hata alınca geri çeker.
          {
                    //listBox2.Items.AddRange( Directory.GetFiles(listBox1.SelectedItem.ToString()));
                    //addrange ile  list 1 dek itüm klasötlerin içindeki dosyaları list 2 ye alır 

                string[] dosyalar = Directory.GetFiles(listBox1.SelectedItem.ToString());
                listBox2.Items.AddRange(dosyalar);
          }
          catch (Exception)
          {
                 MessageBox.Show("ERROR.");
                 // hata anında programın kapanmasını engeller exceptionı yakalar geri çeker 
          }

 

 ```
 ## Mantıksal sürücüleri listele


```  
  
  listBox1.Items.AddRange(  Directory.GetLogicalDrives());  
  
 

 ```
 ## Text dosyası oluşturma


```  
     TextWriter yaz= File.CreateText(textBox1.Text);
     yaz.WriteLine(richTextBox1.Text);
     yaz.Close();

 

 ```
 ## Append ile text dosyası üzerine yazma


```
          //yazma iki farklı yöntemle yapılır
          //1-- append            kelime anlamı ucuca ekle - böyle dosya yoksa oluştur , varsa sonuna ekle.
          //2-- create text       yoksa oluştur  varsa siler ve yeni oluştur   
          
          
            TextWriter yaz = File.AppendText(saveFileDialog1.FileName);
            yaz.WriteLine(richTextBox1);
            yaz.Close();



 

 ```
 ## Text dosyasını okuma, textboxa yazma


```

          //readtoend en baştan ensona tek string olarak okur
          //read line satır satır okur.
          //TextReader oku = File.OpenText(textBox1.Text);
          //büyük textlerde bu yapılamaz anabelleğe alınmaz


          if (openFileDialog1.ShowDialog() == DialogResult.OK)
          {
              TextReader oku = File.OpenText(openFileDialog1.FileName);
              string satır = oku.ReadLine();

              while (satır != null)
              {
                  richTextBox1.Text += satır + "\n";
                  satır = oku.ReadLine();
              }
              // richTextBox1.Text = oku.ReadToEnd();     //okuduğunu richboxa yazar
              oku.Close();
          }


```  


## DataTable kullanımı

>>    public classtan sonra tanımlanır.
>>    
>>    OleDbConnection bağlantı = new OleDbConnection("Provider=Microsoft.Ace.OleDb.12.0; Data source=takip.accdb");
>>    DataTable veritablosu = new DataTable();    



>>>>  Form1_Load  program başladığında ilk ayarlar yapılır

```


            bağlantı.Open();
            OleDbCommand komut = new OleDbCommand("select * from çalışanlar",bağlantı);
            OleDbDataReader okuyucu = komut.ExecuteReader();

            //listbox a çalışan kişilerin isimleri atılır.
            
            while (okuyucu.Read())            {                listBox1.Items.Add(okuyucu[1].ToString());            }

            bağlantı.Close();

            //Veri tablosu sütunları eklenir
            
            veritablosu.Columns.Add("Kişi ID");            veritablosu.Columns.Add("Kişi İsim");
            veritablosu.Columns.Add("Kişi Soyisim");            veritablosu.Columns.Add("Kişi Meslek");
            veritablosu.Columns.Add("Kişi Kurum TEL");            veritablosu.Columns.Add("Kişi CEP No");
            
```  

>>>>Listboxtan seçilen kişiyi DataGridviewe atma

``` 
      if (listBox1.SelectedIndex!=-1)
            {
                bağlantı.Open();
                OleDbCommand komut = new OleDbCommand("select * from çalışanlar where adı='" + listBox1.SelectedItem.ToString() + "'", bağlantı);
                OleDbDataReader okuyucu = komut.ExecuteReader();
                
                DataRow satır = veritablosu.NewRow();     
                
                while (okuyucu.Read())
                {
                    satır[0] = okuyucu[0].ToString(); satır[1] = okuyucu[1].ToString();
                    satır[2] = okuyucu[2].ToString(); satır[3] = okuyucu[3].ToString();
                    satır[4] = okuyucu[4].ToString(); satır[5] = okuyucu[5].ToString();
                    
                    
                    veritablosu.Rows.Add(satır);                   // Satırı veri tablosuna  ekleme
                }
                dataGridView1.DataSource = veritablosu; bağlantı.Close();
               
                listBox1.Items.Remove(listBox1.SelectedItem); }    //Veri tablosuna atılan kişinin adını listboxtan silme

      else
                MessageBox.Show("Önce Kişi Seçin");

```
## DataGridview Otomatik


>> datagridview oluştur. Sağ üstüne tıkla ve veri kaynağı seç 
>> veritabanı > accsess > gözat       (veritabanı dosya seç > tablo seç )

>> DataGridView özellikler > event > cellcontent      (hücre için tıklama ile dataGridView1_CellContentClick oluşturulur)


```
   //otomatik ekleme butonu
   
 this.çalışanlarTableAdapter.Fill(this._takip___KopyaDataSet.çalışanlar);


```  


## VeriTabanı Bağlantısı





> Source-repos-uygulama-bin-debug içine veritabanı atılır (access)
> birden fazla tablodan veri çekmek için:
> 1- içiçe select
> 2-innerjoin 

>> Adımlar:
>>
>>  1- system.data.oledb
>>  2-OledbConnection baglanti =new oledbConnection("provider=microsoft.ace.oledb.12.0;data.source=veritabanıadı.accdb");
>>  3-baglanti.open();    //açılan bağlantı kapatılmalı -> close();
>>  4- OledbCommand komut=new OLedbCommand( ---select komutu--- select * from kisi,baglanti);
>>  5-OledbReader oku=komut.executeReader();
>>  6- while(oku.read())                  //sorgu sonucu verileri satır satır okur
>>  
>>  string ad= oku["adi"].toString();     //örnek kullanım
>>  

 >  Örnek - Listeden seçilen kişiye ait bilgileri TextBoxa yazdırma
  
``` 
     baglantı.Open();
            OleDbCommand list_oku = new OleDbCommand("select * from kişi where adı = '"+listBox1.SelectedItem.ToString()+"' ",baglantı);
            OleDbDataReader okuyucu = list_oku.ExecuteReader();

            okuyucu.Read();
            
            // farklı kullanımlar 
            
            txttc.Text = okuyucu.GetValue(0).ToString();
            txtad.Text = okuyucu["isim"].ToString();
            txtsa.Text = okuyucu[2].ToString();
            txtdt.Text = okuyucu[3].ToString();
            txtdy.Text = okuyucu[4].ToString();
            txttel.Text = okuyucu[5].ToString();
            txtmail.Text = okuyucu[6].ToString();
            baglantı.Close();
    
    
    


  
``` 


>  Örnek  -  Tc ye göre kişi kaydını silme


  
```  

baglantı.Open();
            OleDbCommand sil_komutu = new OleDbCommand("delete from kişi where tc="+txttc.Text,baglantı);
            if (sil_komutu.ExecuteNonQuery() != 0)      // Eylem Sorguları ile çalışır (Ekle, Güncelle, Sil vb..).  Dönüş türü int
                MessageBox.Show("Kişi Silindi");
            else
                MessageBox.Show("Silinemedi");
            baglantı.Close();  
``` 


>   Örnek  -  TextBoxlardaki veriyle kişi kaydı ekleme


  
```   baglantı.Open();
            OleDbCommand ekle = new OleDbCommand();
            ekle.Connection = baglantı;
            ekle.CommandText = "insert into kişi (tc,adı,soyadı,doğum_tarihi,doğum_yeri,tel_no,email) values (@tc,@adı,@soyadı,@doğum_tarihi,@doğum_yeri,@tel_no,@email)";
            ekle.Parameters.AddWithValue("@tc",txttc.Text);
            ekle.Parameters.AddWithValue("@adı",txtad.Text);
            ekle.Parameters.AddWithValue("@soyadı", txtsa.Text);
            ekle.Parameters.AddWithValue("@doğum_tarihi", txtdt.Text);
            ekle.Parameters.AddWithValue("@doğum_yeri", txtdy.Text);
            ekle.Parameters.AddWithValue("@tel_no", txttel.Text);
            ekle.Parameters.AddWithValue("@email", txtmail.Text);
            ekle.ExecuteNonQuery();


            baglantı.Close();
