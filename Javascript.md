

## Javascript Ornekleri #
- [Veri Tipleri](#Veri-Tipleri)
- [Var Let Const](#Var-Let-Const)
- [Veri Tip Dönüşümleri](#Veri-Tip-Dönüşümleri)
- [Döngüler](#Döngü)
- [Math](#Math)
- [String](#String)
- [Array](#Array)
- [Nesne oluşturma](#Nesne-oluşturma)
- [Fonksiyon](#Fonksiyon)
- [Değişkenler](#Değişkenler)
- [Değişkenler](#Değişkenler)
- [Değişkenler](#Değişkenler)











  ## Veri Tipleri



```javascript

    var degisken = 3.14;             // Number Veri Tipi
    
    console.log(typeof degisken);    // değişkenin türü
    
    var name = "Rabia";              // String Veri Tipi
  
    console.log(name);               //ekrana yazdırma
    
    var a = false;                   //bool
    
    var numbers = [1,2,3];           //dizi
    
    var person = {                   // nesne
    name: "Rabia",
    age : 24 }
    
    var date = new Date();            //date

    var yaz = function(){             //fonksiyon
     console.log("Merhaba"); }
     
     
```
  ## Var Let Const

  > var:  global/function scope
  
  >> Sonradan tekrar değiştirilebilir
  >> Sadece fonksion ile kapsanabilir (function scope).
  >> Fonksiyon süslü parantezleri içerisinde var ile tanımlanan değişkene dışarıdan erişilemez.
  >> 
```javascript
 
    var name = "Rabia Abdioğlu";
    console.log(name);

    name = "Rabia";   //Sonradan değiştirilebilir

    console.log(name);



```
  > let:  block scope
  
  >> Sonradan tekrar değiştirilebilir
  >> Aynı kapsam (scope) içerisinde sadece bir sefer tanımlanabilir.
  >> Tekrar tanımlanmaya çalıştığında kod hata verir ve çalışmayı durdurur.
  >> 
  ```javascript
 
    let a,b;

    a = 50;   //Sonradan değer verilebilir
    b = 77;

    console.log(a+b);


```
  > const:  block scope , immutable
 
  >> Sonradan değiştirilemez
  >> Aynı kapsam (scope) içerisinde sadece bir sefer tanımlanabilir.
  >> Tekrar tanımlanmaya çalıştığında kod hata verir ve çalışmayı durdurur
  >> 
```javascript
 
    const name = "Rabia Abdioğlu";      //sabit değişken değer ilk tanımlanınca verilir

    console.log(name);

    name = "Rabia";

    console.log(name);      //Hata verir
```
--
 ```javascript
    //arraylerde a dizinin başlangıç yerini gösterir.
    // bu yüzden a değişmez ama diziye push edilebilir
    
    const a = [1,2,3,4,5];

    console.log(a);
    
    a = [1,2,3,4,5];    //hata verir
     
    a.push(6);

    
```



  ## Veri Tip Dönüşümleri



```javascript 

let value;

value=String([1,2,3,4]);      //string
value = (10).toString();


value = Number([1,2,3,4]);    //number

value = parseFloat("3.14");   //float
  
value = parseInt("3");        //integer

value = Boolean(0);           //bool
```
  ## Döngüler




```javascript 


    const ogrenciler = ["Ayşe","Rabia","Hasan"];

    let i = 0;
    
    //While
    while(i < ogrenciler.length){
      console.log(ogrenciler[i]);
      i++;}
      
      
    //For
    for (i = 0;i < ogrenciler.length;i++){
      console.log(ogrenciler[i]);}
      
      
    //ForEach
    ogrenciler.forEach(function(ogrenciler,i){
      console.log(ogrenciler,i); });
   
```
## Math 



```javascript  
    value = Math.PI;                //pi sayısı
    value = Math.E;                //log e

    value = Math.round(3.6);      // yakın olana yuvarlar
    value = Math.ceil(3.7);       // büyük olan tamsayıya yuvarlar
    value = Math.floor(3.7);      // küçük olan tamsayıya yuvarlar
    value = Math.sqrt(36);        // karekök
    value = Math.abs(-85);        // mutlak değer
    value = Math.pow(x,y);        // x üzeri y
    value = Math.max(96,-56);
    value = Math.min(5,32);

    value = Math.random();        // Rastgele sayi 0-1
    value = Math.floor(Math.random() * 20 + 1);


  ```
  ## String



```javascript 
   

    const isim = "Rabia";
    const soyisim = "Abdioğlu";
    const isim_soyisim =  "Rabia Abdioğlu";


    isim.length;              //uzunluk

    isim.concat(" ",soyisim); // birleştir

    isim.toLowerCase();       //küçük harf

    isim.toUpperCase();       //büyük harf

    isim[isim.length - 1];    //son indexteki harf

    soyisim.indexOf("o");     // o harfinin bulunduğu ilk index

    firstName.charAt(4);      // 4. indexteki karakteri alır

    isim_soyisim.split(" ");  // boşluk sayıysına göre ayırır

    isim_soyisim.replace("Rabia","Kader");  //değiştirir

    isim_soyisim.includes("ab");  //verilen stringi içeriyormu


    Template Literal Örneği

    const a = `İsim:${isim}\nSoyisim:${soyisim}`;


```
  ## Array




```javascript 



      const array = [1,2,3,6,5,92,53];    //Array oluşturma

      //const array = new Array(1,2,3,6,5,92,53);


      array.length;           // Uzunluk

      array[0];               //0. index

      array[0] = 80;          //0. indexi değiştirme

      array.indexOf(92);      //92 nin bulunduğu ilk index

      array.push(2000);       // arrayin sonuna  ekleme

      array.unshift(3000);    // arrayin başına ekleme

      array.pop();            //sondan değer alma     

      array.shift()           //baştan değer alma

      array.splice(x,y);      //x ten y ye kadar olan kısmı alma

      array.reverse();        //diziyi ters çevirme



      value = array.sort();   //sıralama



      value = array.sort(function(x,y){ // Küçükten Büyüğe
          return x - y;
      });

      value = array.sort(function(x,y){ // Büyükten Küçüğe
          return y-x;
      });

```
  ## Nesne oluşturma


```javascript 

      let yaz;

      const insan = {
          isim : "Rabia ABDİOĞLU",
          yas : 24,
          yetenek : ["Koşmak","Nefes almak"],

          address : {
              city : "İstanbul",
              street : "Bahçelievler"
          },

          nefesAl : function(){
              console.log("Nefes Alınıyor...");
          }
         nefesVer : function(){
              console.log("Nefes Veriliyor...");
          }


      }

      yaz = insan;

      yaz = insan.email; 
      yaz = programmer["isim"];
      yaz = programmer.yetenek;
      yaz = programmer.address.city;

      insan.nefesAl();
      insan.nefesVer();


   //Diziler halinde obje
      const hayvan = [
          {tür: "Tavuk",ayak:2},
          {tür : "Kuzu",ayak:4}
      ];

      value = hayvan[1].ayak;     //1 indexli hayvanın ayak sayısı


      console.log(value);


```
  ## Fonksiyon




```javascript 
   
   
  // fonksiyon    -- obje dışı 
      
        const fonk = function(name){
        console.log("Merhaba " + name);};

        fonk("Rabia");
   
   // (IIFE)

       (function(name){
        console.log("Merhaba: " + name);})("Rabia");

  // metod    -- obje içi 

      const metod = {
          host: "localhost",
          add: function(){                  //parametresiz
              console.log("Eklendi");
          },
          update:function(id){               //parametreli
            console.log(`Id: ${id} Güncellendi`);  
          },
          delete:function(id){
            console.log(`Id: ${id} Silindi`);  
          }
      }

      console.log(metod.host);
      metod.delete(10);
```
 
  ## DOM Manipülasyonu



```
Document object model -  DOM

Sabit web sayfalarına dinamiklik katmak için kullanılır. 

Html sayfası ve etiketleri arasında parent - child  ilişkisi vardır. 
Elementler arası ilişki ile element idsi kullanarak obje manipüle edilebilir. 

Window object içerisinde document, link özellikleri vardır. 

```
 
 ### Document Object

```javascript 

let value;

value=document.all;
value=document.all[document.all.length-1];  //en son satıra ulaşmak için


const elements=document.all; //hmtl collection

for(let i=0;i<elements.length;i++){
console.log(elements[i]);


//foreach için arraye çevirmek gerekir. 

const collections=Array.from(document.all);
collections.forEach(
function(collection){
console.log(collection);}
);

value=document.characterSet;  // utf-8

value=document.scripts.length; //kaç script var

//Links


value=document.links[2];      //2. link
value=document.links[0].getAttribute("class");  //hangi sınıf
value=document.links[0].className veya classList ile kullanılabilir.  


//Forms


value=document.forms[2];  
value=document.links["form"];  
value=document.forms[0].getAttribute("name");   // formun name bilgisini almak için 

value=document.forms[0].method;  

``` 

 
 ### Elementleri Seçme

```javascript

let element

element=document.getElementById("todo-form");  //id ye göre 
element=document.getElementByClassName("list-group-item")[0]; //class birden çok olduğu için dizi döndürür 
element=document.getElementByTagName("div"); //tüm divleri gösterir.

element=document.querySelector("#todo-form");  //id ile

element=document.querySelector(".list-group-item");  //class ile


//Birden çok elemet için 
element=document.querySelectorAll(".list-group-item"); 


element.forEach(function(el){console.log(el);});

//Özelliklere bakmak için 

console.log(element.id);  
console.log(element.classList[1]);  
//hred innerHtml  vb özelliklere bakılabilir.


console.log(element.style); //elementin css özellikleri gelir.  

//css özelliklerini değiştirme 

element.className="btn btn-primary";
element.style.color="#000";
//diğer tüm css özellikleri bu şekilde değiştirilebilir. 

element.href="http.....";
element.target="_blank";

element.textContent="Sil";
  
element.innerHTML="<span style='red'> Sil</span>";

//sınıfı aynı olan tüm elementleri dizi olarak alır. Foreach ile her birine özellik ataması yapar
elements=doceument.querySelectorAll(".list-group-item");//NodeList
element.forEach(function(el){
el.style.color="red";
el.style.background="white";

});


//li elementleri içerisinde çift olanları alır.  
let element2=document.querySelector("li:nth-child(2));




``` 

 
 ### Dom elementleri üzerinde gezinme















