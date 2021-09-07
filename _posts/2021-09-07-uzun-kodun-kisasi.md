---
layout: single
name: uzun-kodun-kisasi
title: "Uzun Kodun Kısası"
category: articles
---

Meslek lisesinde **Bilişim Teknolojileri** bölümü okuyan birisi olarak kodlama dilleri ile hep haşır neşir oldum. **Web Programcılığı** ana dalında aldığım eğitim gereği **HTML, CSS, PHP, MySQL** kodlama dillerine başlangıç seviyesinde hakimdim. Üniversite'de **İstatistik** bölümünü kazandıktan sonra bu kodlama dillerinin temellerine hakim olmanın değerini çok daha iyi anladım. Analiz edilmesi gereken verilerin bulunduğu veri tabanlarına kodlamalar ile bağlanılıyor, yine veri alma ve çıktı alma işlemleri kodlamalar ile yapılıyordu. Özellikle büyük veri analizi kısmında Excel programı hiçbir işe yaramıyor, standart yöntemler işletim sistemini sonsuz döngülere sokuyor, kullanılan programlara hatalar verdiriyordu. Veri tabanı programlama, büyük veri istatistiğinin ve büyük veri raporlamanın altın kuralıydı. Ben de bunun temellerine hakimdim.

Şu anda çalışmakta olduğum **BKMKİTAP** firmasında **Veri Analisti** olarak başladığımda bu temellerin üzerine nasıl binalar çıkmak gerektiği hususunda bir fikrim yoktu. Bir *case* gelir ve ben de *study* edinirim düşüncesi ile verilen görevleri yapmaya başladım (*bu arada "case study" cümlesinin "vaka analizi" olarak çevirilmesine karşıyım. Sözcüğün anlamı bence "**durum öğrenimi**"dir*). Zaten şirketlerin <ins>deneyimli personel</ins> isteği de bu sebepten değil midir? Deneyimli personel aramalarının nedeni, *case study* bilgisi yüksek personel bulmak içindir. Çünkü gerçek hayatta özellikle büyük şirketlerde öğrenme denilen süreç sancılıdır. Öğrenene kadar yapılan hatalar, kayıplar, geri dönülmesi zor aksiyonlar özellikle IK (*HR mı demeliydim yoksa*) departmanlarının gözünü korkutmaktadır. Gerçi bu başka bir yazının konusu (*hatta sosyoloji konusu*) biz en iyisi konumuza dönelim.

Burada profesyonel iş hayatında kullandığım, birazını yazılım uzmanımız **Hakan Bey**'den, çoğunluğunu [Hz. Google](https://www.google.com)'dan öğrendiğim bir takım kısa yol kod örneklerini ve bunların kullanım durumlarını paylaşacağım. İş hayatında tabiri caizse **zamandan kurtaran** kod kısaltmaları olmasaydı, basit kodları dakikalarca yazmak durumunda kalacaktım hiç şüphesiz...

***NOT:** Burada yazılan kısa yol örnekleri, Azure Data Studio programı üzerinde MsSQL veri tabanı kodlama dili ile anlatılmıştır. MySQL veritabanı kodlama dilinde bulunmayanlar olabilir. Aynı şekilde editör kısa yolları da diğer editörlerde bulunmuyor olabilir.*

## 1. Select sorgusundaki verileri bir tablo içerisine yazma

Örneğin bir *customers*, bir de *orders* tablolarımız olsun. Bunları beraber bir şekilde (*customerID üzerinden*) bağladığımızı hayal edelim. Veri tablomuzda müşteri ismi (*customername*), sipariş edilen ürün (*productname*) ve adet (*quantity*) olsun.

***NOT:** Bundan sonra bu örnek "**STANDART ÖRNEK**" olarak anılacaktır.*

```sql
SELECT C.customername, O.productname, O.quantity
FROM orders O
JOIN customers C on C.customerID=O.customerID
```

Normal şartlar altında bu çıktıyı *customer_orders* isimli bir tabloya yazmak istersek şunu yapmamız gerekirdi.

```sql
CREATE TABLE customer_orders (
customername VARCHAR, 
productname VARCHAR,
quantity INT
)
INSERT INTO customer_orders VALUES (
SELECT C.customername, O.productname, O.quantity
FROM orders O
JOIN customers C on C.customerID=O.customerID
)
```

Önce tabloyu oluşturduk, sonra aynı isimle değişkenler tanımladık, sonra da bu tabloya verileri yazdık. Burada bir sıkıntı yok. Peki bunu daha kısa nasıl yazabilirdik?

```sql
SELECT C.customername, O.productname, O.quantity
INTO customer_orders
FROM orders O
JOIN customers C on C.customerID=O.customerID
```

Direkt olarak çıktıyı oluşturduğumuz tabloya yazdı. Nasıl? Basit değil mi?

## 2. Veri tabanlarını kitlemeden iş yapma

Bu seferki ipucu, sorguyu kısaltmak yerine uzatıyor. Fakat iş hayatında çokca kullanıldığı için burada da yazmak istedim. Bir sorgu yazdığınızda, o sorgu sonucu size dönene kadar ilgili veri tabanı tablosu **kullanılamaz hale gelir**. Bu durum, o tabloya bağlı girdi yapan programları - sistemleri - veri üzerinde çalışan başka çalışanları da **kuyrukta bekletmesi** (*ve genellikle hata alması*) ile sonuçlanır.

Tablo sonuna yazılacak basit bir kod ile tablonun kilitlenmesinin önüne geçebiliriz. **WITH (NOLOCK)** yazarak ilgili tabloyu o anki durumu ile kullanabiliriz. Tek dezavantajı, o tablo çalışırken yeni veriler girilmeye (ya da silinmeye) devam ettiğinden, kodu çalıştırdığınız an veri tabanındaki değişiklikler sebebiyle raporlarınızda küçük değer hataları meydana gelebilmektedir. Yaptığım iş raporlama ile ilgili olduğundan ve büyük veriler üzerinde çalıştığımdan çoğunlukla bir zararını (*anlamlı bir veri farkını*) göremedim.

```sql
 SELECT * FROM orders O WITH (NOLOCK)
```

## 3. MsSQL'de IF sorguları

Eğer ki SELECT içerisinde koşullu çıktılar almak istiyorsak genellikle **CASE WHEN ... THEN ... END** şeklinde bir yapı kullanırız.

Örneğin; STANDART ÖRNEK'teki tablo yapısı içerisinde eğer toplam *quantity* değeri 10'dan yüksek ise "**HIGH10**", değilse "**NORMAL**" şeklinde çıktı veren *TOTALQUANTITY* sütununu oluşturalım.

```sql
SELECT C.customername, O.productname, SUM(O.quantity),
	CASE WHEN SUM(O.quantity) > 10 THEN 'HIGH10' ELSE 'NORMAL' END AS 'TOTALQUANTITY'
FROM orders O
JOIN customers C on C.customerID=O.customerID
GROUP BY C.customername, O.productname, 
	CASE WHEN SUM(O.quantity) > 10 THEN 'HIGH10' ELSE 'NORMAL' END

```

Eğer koşullu durumumuz yalnızda 2 koşuldan ibaretse (*yukarıdaki örnekteki gibi*) CASE WHEN ... THEN ... END yapısındansa daha kısa bir yapı olan **IIF(... , ... , ...)** yapısını kullanabiliriz. Aynı sonucu verecektir.

```sql
SELECT C.customername, O.productname, SUM(O.quantity),
	IIF(SUM(O.quantity)>10, 'HIGH10', 'NORMAL') AS 'TOTALQUANTITY'
FROM orders O
JOIN customers C on C.customerID=O.customerID
GROUP BY C.customername, O.productname, 
	IIF(SUM(O.quantity)>10, 'HIGH10', 'NORMAL')

```

Tabi ki bu durum, sadece 2 koşul için geçerlidir. 3'lü koşullarda CASE kullanımına devam ediyorum. IIF sorgusu iç içe de kullanılabilir, fakat CASE kullanımına göre daha az performans gösterdiğini düşünüyorum.

## 4. OR ... OR ... OR ...

Eğer elinizde hücre içeriği ile tam eşleşen çıktılarınız varsa ve bu çıktılar üzerinden satırları seçmek istiyorsanız genellikle WHERE koşulu içerisinde **OR** kullanıyor olursunuz.

Örneğin; STANDART ÖRNEK'teki tablo yapısında *productname* sütununda **Faber Castel Kalem, 1984 Kitap, GIPTA Defter** ürünlerinin bulunduğu satırları seçelim.

```sql
SELECT C.customername, O.productname, O.quantity
FROM orders O
JOIN customers C on C.customerID=O.customerID
WHERE ( O.productname = 'Faber Castel Kalem' 
OR O.productname = '1984 Kitap'
OR O.productname = 'GIPTA Defter')
```

Fakat buna benzer bir dizi eğer ki 100'ü aşkın ürün için varsa, bu OR'lar can sıkıcı hale gelmeye başlayabilir. Bu gibi durumlar için "**IN**" operatörü kullanmaktayım.

```sql
SELECT C.customername, O.productname, O.quantity
FROM orders O
JOIN customers C on C.customerID=O.customerID
WHERE O.productname IN ('Faber Castel Kalem', '1984 Kitap', 'GIPTA Defter')
```

Tek can sıkıcı noktası, eğer **LIKE** kullanmak zorundaysanız (*ki metinsel koşullarda LIKE kullanılması daha iyidir*) onu desteklememesi. Yani bir "**LIKE IN**" komutu da olsaymış tadından yenmezmiş şu MsSQL 🙂.

## 5. Betimleyici istatistik operatörleri

Bu operatörleri genellikle müşterinin ilk ve son siparişini, sepet ortalamasını vesaire gözlemek için kullanıyorum. Mesela yine STANDART ÖRNEK'teki tablo yapısı üzerinden gidersek, müşteriye ait son sipariş ID'sini (*orderID*) ve tarihini (*orderdate*)" görüntüleyelim.

```sql
SELECT C.customername, O.orderID, MAX(O.orderdate)
FROM orders O
JOIN customers C on C.customerID=O.customerID
GROUP BY C.customername, O.orderID

```

İlk başladığım zamanlarda **ROW NUMBER() OVER()** yöntemi ile **WITH** içerisinde önce numaralandırıp sıralıyor, ardından ilk sıradaki çıktıyı gözlemlemeye çalışıyordum. MIN ve MAX komutunun **tarihte** ve hatta <ins>**metinde**</ins> bile kullanıldığını öğrendikten sonra uzun uzadıya tablolar oluşturmak yerine kısa yoldan işleri halletmeye başladım. Belki benim gibi işin kolayı varken kendisine işkence eden başkaları da vardır diye bu da burada bulunsun.

## 6. JOIN ile koşullandırma

Bu basit gelebilir, fakat en büyük performans artılarından bence birisidir. STANDART ÖRNEK'teki tablo yapısını üzerinden gidelim. Burada yalnızca müşteri adı içerisinde "**ahmet**" geçen müşterileri görüntüleyelim.

```sql
SELECT C.customername, O.productname, O.quantity
FROM orders O
JOIN customers C on C.customerID=O.customerID
WHERE C.customername LIKE '%ahmet%'

```

Yukarıdaki sorguda önce tüm *customers* tablosunu siparişler ile eşledi, daha sonra içlerinden yalnızca müşteri adı sütununda içerisinde **ahmet** geçenleri ekrana yazdı. Fakat bunu yaparken (*farazi konuşuyorum*) 20 milyon satırlık *orders* tablosu ile 5 milyon satırlık *customers* tablosunun tamamını eşitledi, sonrasında bu eşitlenmiş tablo içerisinde müşteri adı **ahmet** ismi geçenleri aradı.

Eğer ki tablo genelinde müşteri adı içerisinde **ahmet** geçenler haricindekilerle hiçbir analiz/çalışma yapılmayacaksa bunu direkt **JOIN** içerisinde belirtip daha az sayıda tablo eşitlemesi yapabiliriz.

```sql
SELECT C.customername, O.productname, O.quantity
FROM orders O
JOIN customers C on C.customerID=O.customerID AND C.customername LIKE '%ahmet%'

```

Burada, (*az önceki farazi örneğe dayalı olarak*) 20 milyon satırlık *orders* tablosu ile 200 bin satırlık "*içerisinde ahmet kelimesi geçen customers*" tablosunu eşitlemiş olduk. Böylece sorgu, daha hızlı bir çıktı vermiş olacaktır.

## 7. TEMP TABLE

Bu bölüme geçmeden önce bir efsaneyi yâd etmek istiyorum.

> But anyway, now is in the **TABELE**, we have to see the situation, now is second position, and ... 
> -- Fatih Terim (Türkiye - Yunanistan Maçı basın açıklaması | 17.10.2007)

Bu yöntem özellikle **linked server** üzerinden veri almaya çalışıldığında çok verimli olabilmektedir. STANDART ÖRNEK'teki tablo yapısına başka bir veri tabanı üzerinde bulunan ve linked server aracılığı ile eriştiğimiz **crm** tablosunu *customerID* üzerinden bağlayalım.

```sql
SELECT C.customername, O.productname, O.quantity, CRM.IYS_onay
FROM orders O
JOIN customers C on C.customerID=O.customerID
JOIN linked.crm CRM on CRM.customerID=C.customerID
```

Burada **crm** tablosunu eklemeden önce (*farazi olarak*) 10 saniyede gelen sorgu sonucu, bu tabloyu ekledikten sonra 35-40 saniyede anca gelecektir. Özellikle linked server üzerinden karmaşık sorgular gerçekleştirirsek süre daha da uzayacaktır. Bu süreyi **TEMP TABLE** kullanarak kısaltabiliriz. Bir TEMP TABLE oluşturup, içerisine linked server içerisindeki tabloya ait kullanacağımız verileri yazdırmamız yeterlidir.

```sql
SELECT customerID, IYS_onay
INTO #temp_crm
FROM linked.crm
-- Yukarıdaki tablo sadece 1 defa çalıştırılır.

SELECT C.customername, O.productname, O.quantity, CRM.IYS_onay
FROM orders O
JOIN customers C ON C.customerID=O.customerID
JOIN #temp_crm CRM ON CRM.customerID=C.customerID
```

Burada tek kare işareti (#) o geçici tablonun **sadece yaratıcısı tarafından kullanılabileceği** anlamına gelir. İki kare işareti (##) ise ilgili geçici tabloya **başka kullanıcılar veya diğer oturumlar üzerinden de ulaşılabileceği** anlamına gelir. Bağlantı kesildiğinde, geçici tablolar da otomatik olarak silinir. (*Farazi*) 35-40 saniye geciken sorgu, bu yöntemle 15-20 saniye civarına indirilebilmektedir.

## 8. WITH ile tablolama

Bu yöntemi daha çok iç içe sorgular yapmam gerektiğinde kullanıyorum. Mesela bir sorgu içerisinde 2 defa *orders* tablosuna bağlı bir işlem yapmam gerektiğinde **WITH** imdadıma yetişiyor. STANDART ÖRNEK'teki tablomuzu baz alırsak;

```sql
WITH ictablo AS(
	SELECT
	C.customername, O.productname, O.quantity
	FROM orders O
	JOIN customers C on C.customerID=O.customerID
)

SELECT * FROM ictablo
```

şeklinde bir WITH örneği oluşturabiliriz. *ictablo* isimli tablo artık kendi içerisinde sorgunun tamamını çekip, bir tablo gibi davranıyor. Bu tabloya *orders* tablosunu yeniden bağlayıp işlem yapmak mümkün. Aklıma şu an için bir örnek gelmiyor fakat iş hayatımda bol WITH içeren sorgular yazdığımı biliyorum.

## 9. Spagetti Düzenleme

Bu ipucu,  editör'den editör'e değişebilmekte. Ben VS-Code tabanlı Azure Data Studio kullanmaktayım. Bu sebeple tüm bilgilerimi onun üzerinden anlatacağım.

Extentions kısmından "**Poor SQL Formatter**" şeklinde aratarak ilgili eklentiye ulaşabilirsiniz. Eklentiyi yükledikten sonra **CTRL + SHIFT + P** ile komut paletini açıp içerisine "*poor sql: format t-sql*" yazıp enter tuşuna basarsanız daha düzenli bir sorgunuzun olduğunu göreceksiniz. STANDART ÖRNEK üzerinden anlatırsam;

```sql
SELECT C.customername, O.productname, O.quantity FROM orders O
JOIN customers C on C.customerID=O.customerID
```

şeklindeki sorguyu

```sql
SELECT C.customername
    , O.productname
    , O.quantity
FROM orders O
JOIN customers C
    ON C.customerID = O.customerID
```

şekline çevirecektir. Uzun SQL kodları içerisinde neyin nereden geldiğini anlama açısından güzel bir yöntemdir.

## 10. Editörün güzellikleri

Bu kısım da yine kullandığım editörün beni hızlandırdığı alanlar olarak yer almakta.

Mesela sorgu içerisindeki bir değişkeni (*ax1*) değiştirip yerine başka bir değişken ismi (*figa*) yazmak istersem **CTRL-H** kısa yolu ile **tamamını** değiştirebilirim. Fakat sorgu içerisindeki tüm kelimeleri değil de, sorguya ait belli bir satırdan itibaren, ilerleyen satırlardaki 4 kelimeyi seçip de değiştirmek istersem, değişecek metinden bir tanesini çift tık ile seçip 4 defa **CTRL-D** kısa yolunu kullanarak manuel değişim de sağlayabilmek mümkün.

**ALT+SHIFT+MLCLICK** ile "**serbest seçimli**" olarak kelime seçimi yapılabilmekte.

**ALT+SHIFT+DOWNARROW** ile imlecin bulunduğu satır bir alt satıra kopyalanabilmekte.

**CTRL+ALT+UPARROW/DOWNARROW** ile birden fazla satır içerisinde imleç kullanımı yapılabilmekte.

**CTRL+ALT+LEFTARROW/RIGHTARROW** ile program içerisinde pencere yaslaması yapılabilmektedir.

## 11. Excel ile kombo!

Kitap sektöründe barkod listeleri üzerinden çalışmalar yapılmaktadır. Bu barkod listeleri Excel ile tarafıma iletilmekte. Benim de barkod özelinde SQL ile çalışma yapmak için uygun formata çevirmem gerekmekte. Bu durumda da Excel'in nimetlerinden faydalanmaktayım.

Gelen barkodları "**IN**" komutu ile kombine edebilmek için;

```visual-basic
 = ",'"&barkodHücresi&"'"
 
```

Excel formülünü sıklıkla kullanmaktayım.

Ayrıca veri tabanından beslenen **Canlı Excel** tabloları oluşturmak için de Excel'in nimetlerinden faydalanmaktayım. Genellikle Excel'in içerisindeki "*Diğer Kaynaklar*" kısmından SQL Server'i bağlamaktayım. Güvenli bir yöntem olmadığının bilincindeyim, fakat şirket içinden dışarı çok fazla dosya çıkartmadığımız için işimizi görmekte. Güvenlik endişesi olanlar için ise **Power Query**'i öneririm.

Veri Madenciliği yapmak için Microsoft'un sitesinde eklenti olarak bulunan "**Data Mining add-in**"ini öneririm. 1 milyon satıra kadarki verilerde madencilik yapmamızı sağlayan bu eklenti, basit düzeyde de olsa veri madenciliği yapmamızı sağlamakta.

----------

İşte böyle... İşimi yaparken beni hızlandıran ipuçları bunlar. Aralarında yeni duyduğunuz yöntemler olduysa ne mutlu bana 😊.
