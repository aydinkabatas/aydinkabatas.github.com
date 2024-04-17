---
layout: single
name: yaratiliscilarin-matematiksel-savunmasi-borelin-kanunu
title: "Yaratılışçıların Matematiksel Savunması: BOREL'İN KANUNU"
category: articles
---

Yoğun iş temposunun arasında vakit buldukça kendimi geliştirmeye çalışıyorum. Sahip olduğum ve halen diri tutmam gerektiğine inandığım bu araştırmacı yönümü gerek kendi sektörümden bilgiler öğrenme üzerine, gerekse merak ettiğim konuları öğrenme üzerine kullanmaya devam ediyorum. **"Merhaba Dünya! (Yeniden...)"** başlıklı yazımda "Burayı artık daha çok makale ve bilgi paylaşımında bulunacağım bir platform olarak kullanacağım." dedikten sonra 2 makale yazıp gündelik hayattaki yoğunluğun verdiği vakitsizlik ile buraları boş bıraktığım için bir yandan kendimi hep kötü hissediyordum. Fakat bir konu üzerine yazarken iyice bir araştırma yapmanın, yazdığım yazıları referanslı bir şekilde paylaşmanın daha doğru olduğuna inanıyorum. Bu sebeple bu makaleyi bile yaklaşık 1 haftada *(işten ve gündelik telaşlardan arta kalan sürelerde)* yazmış bulunmaktayım.

Bu teoremi araştırıp yazmamın nedeni, iş yerindeki arkadaşlarla aramda çıkan evrim tartışmasında bana anti-tez olarak sunulmasından dolayıdır. İş arkadaşım bana *"10<sup>-50</sup>'den küçük olasılıkların gerçekleşmesi imkansız, bu da zaten Evrim Teorisini direkt çürütüyor."* demişti. Ben de *"Bu sayıyı kim, nasıl, neye göre verebiliyor? Böyle bir oranı istatistik genelinde verebilmek imkansız."* demiştim. Daha sonra "[Rationalwiki][ref0]"  adında bir adresin linkini atıp *"işte kanıt"* demişti. Ama sorun şu ki; kanıtı da onu yalanlıyordu. Yani kanıt diye gönderdiği şey, Borel'in bir alıntısının saptırıldığını söyleyen bir kanıttı. *(Tabi o arkadaş "Böyle bir şey var, sen yok diyordun, sen haksızsın" diyerek arkasını döndü. Halbuki yine de yoktu ama zaten o arkadaşa bilim metodolojisinde bir şeyler anlatmak imkansızdı. Daha fazla uzatmamayı tercih ettim.)*

### ÖZETLE

Her ne kadar Émile Borel'in ortaya çıkarttığı bir **"kanun"** olarak düşünülse de aslında Karl Crawford *(nam-ı diğer ksjj)* tarafından, Borel'in bir kitabında geçen bir örneği hatalı yorumlayarak kanun ilan etmesiyle bu ismi almıştır.

Émile Borel bir alıntısında *"Olasılıkları çok düşük olan olaylar gerçekleşmez."* demiş *(ki bunu da bilim insanları için yazılmamış olan bir kitabında "belirli fiziksel özellikler" ile ilgili olarak örneklendirme amacı ile söylemiş, yani kanun olsun diye değil)*, yaratılışçı bir abimiz de bu kitaptaki bir alıntıyı tahrip edip *"10<sup>50</sup>'de 1'den düşük herhangi bir oranın gerçekleşme olasılığı sıfırdır. ([Karl Crawford](http://www.talkorigins.org/faqs/abioprob/borelfaq.html))"* sözünü ortaya atmıştır.

Sonra da bu "<ins>**ZIRVA**</ins>" özellikle yaratılışçıların arasında "Evrimi Çürüten Kanıt" olarak yerini almıştır.

### BOREL KİMDİR?

Tabi problemin kaynağını anlayabilmek için Borel'i tanımak, onun ne anlatmaya çalıştığını anlamak gerekiyor.

Tam ismi Félix Édouard Justin Émile Borel,  fransız matematikçi ve politikacı. Ölçülebilirlik ve Olasılık teoremleri hakkında çalışmalar göstermiş. Yani abimiz İstatistik ve Olasılık Teorisi konuları ile sürekli haşır neşirdir.

1900'lü yılların başında istatistiksel hipotez testleri çağı başlayınca, rastgele sayılar için bir takım testler önerilmiş, bu abimiz de neredeyse her zaman rasgele seçilen sayıların normal dağılımdan geldiğini keşfetmiş, bu sebeple normal dağılımdan sayı elde etmek için rasgele sayılar seçmenin kâfi geldiğini kanıtlamıştır. Sonra kendisini geometriye vermiştir.

1922'de en eski Fransız istatistik okulu olan Paris İstatistik Enstitüsü'nü kurmuş, daha sonra da 1928'de Paris'te Henri Poincaré Enstitüsü'nü kurmuştur.

Borel cebiri, Borel'in lemması, Borel'in Büyük Sayılar Yasası gibi Borel'e ithaf edilmiş birçok kavram mevcuttur.

Yani matematik ve istatistik bilimlerine gerçekten çok emeği geçmiş, enstitüler kurmuş, adına teoriler ithaf edilmiş bir dahi. Borel'i daha da merak edenler [Vikipedi][ref1]'den araştırabilir.

### NEREDEN ÇIKTI BU KANUN?

Sözde Borel'in Kanunu'na ait ilk temeller yine Émile Borel tarafından, "<ins>bilim insanları için yazılmamış kitaplarında</ins>" verdiği bir örnek içerisinde geçer. Borel kitabında, bilim insanlarının belirli bir olasılık altındaki olayları ihmal edebileceğine ilişkin mantıksal örnekler vermiştir. Bu kitaplar 1962 yılında yazılmış olan "Olasılık ve Yaşam" ve 1963 yılında yazılmış olan "Olasılık ve Kesinlik" isimli kitaplarıdır. 

Fakat Borel, buradaki örnekleri evrensel bir yasa için değil, bazı fiziksel problemlerin çözümlerinde olasılık modellemesi yapabilmek için oluşturmuştur. Borel'in kesme olasılığının seçim problemi için verdiği bir örnek aşağıdaki gibidir;

> Örneğin, Paris'teki milyonda 1 trafik ölüm oranından *(II. Dünya Savaşı öncesi bir istatistiksel oran)* yola çıkarak 10<sup>-6</sup> (yani milyonda bir) **insan ölçeğinde** ihmal edilebilir. Bunu 10<sup>-9</sup> ile çarparak *(1940'larda dünya nüfusu)*, 10<sup>15</sup>'te 1 oran **Dünya ölçeğinde** ihmal edilebilir olarak gözükmektedir.

Görüldüğü gibi, kitabında neye bağlı bir ölçek olduğuna dair tabirler bile mevcuttur. Borel'in yine kozmik ölçekte ihmal edilebilir olasılıklar ile ilgili verdiği bir örnekte de *"10<sup>50</sup>'de 1 oran kabul edilebilir"* şeklinde örneklendirdiğini görüyoruz. Fakat bu örnekler görüldüğü üzere **zaman** kavramından bağımsız, direkt anlık fiziksel ortam örnekleridir. Bu kozmik ölçek örneğinden yola çıkarak Karl Crawford, Borel'e atıf yaparak:

> ...Matematikçiler genellikle, istatistiksel olarak, 10<sup>50</sup>'de 1'in ötesindeki herhangi bir olasılığın sıfır olduğu konusunda hemfikirdirler. Bu, matematikçi Emil Borel tarafından türetilen Borel'in yürürlükteki yasasıdır.

şeklinde bilim camialarınca son derece mantıksız bir sözü ortaya atmıştır.

Öncelikle yeniden üzerine basa basa söylemem gerekli ki, **bu bir yasa/kanun değildir**. Yasalar, bizlerden bağımsız olarak var olan nesnel gerçekliklerdir. [Evrenin yapısı bozulmadığı sürece bu şekilde var olacaktır.][ref2] Örneğin; Yerçekimi Kanunu, Kütlenin Korunumu Kanunu, Evrim Kanunu bunlara örnek verilebilir. Dünya üzerindeki elma ağaçlarının hepsinde elma yukarıdan aşağıya düşer, bu tüm elmalar için geçerlidir. İşte buna biz, Yerçekimi Kanunu diyoruz. Sadece elma için geçerli değildir. Kütlesi ve hacmi olan tüm cisimler için geçerlidir. Dünya'nın merkezine hepsi çekilir *(daha da detaya inersem, elmanın bile bir çekim kuvveti vardır ama orada kafalar biraz karışabilir. Hatta uzayın bükülmesi muhabbeti falan var ki akıllara zarar. Merak edenler [Kozcan Demircan][ref3]'ın yazısına bakabilir)*.

Fakat Karl'ın sözde kanun olduğunu iddia ettiği bu limit problemi, bir istatistikçi için zaten olasılığı mümkün bir limit olarak gözükmektedir. Örneğin; Mustafa Kemal Atatürk'ün Conkbayırı'ndaki bir savaşta göğsüne şarapnel gelmesi ve saatin Mustafa Kemal Atatürk'ü şarapnelden kurtarması ihtimaline bakalım. Matematiksel oranlar vermeyeceğim fakat burada zaten o ihtimalleri ardı ardına yazınca 10<sup>50</sup>'de 1 ihtimalden daha az olduğunu fark edeceksiniz. Burada;<br />
P(x<sub>1</sub>)="Savaş zamanında bulunma ihtimali"<br />
P(x<sub>2</sub>)="Askerlik mesleğini seçme ihtimali"<br />
P(x<sub>3</sub>)="İsminin Mustafa olması ihtimali"<br />
P(x<sub>4</sub>)="Yanında bomba patlama ihtimali"<br />
P(x<sub>5</sub>)="Şarapnel parçalarının göğsüne saplanması ihtimali"<br />
P(x<sub>6</sub>)="Şarapnel parçasının saate çarpması ihtimali"<br />
P(x<sub>7</sub>)="Askeri okul seçme ihtimali"<br />
P(x<sub>8</sub>)="Annesinin isminin Zübeyde olması ihtimali"<br />
P(x<sub>9</sub>)="Babasının isminin Ali Rıza efendi olması ihtimali"<br />
P(x<sub>10</sub>)="Bir saatinin olması ihtimali"<br />
P(x<sub>11</sub>)="Saatin hediye olması ihtimali"<br />
...<br />
şeklinde uzun bir liste yapabiliriz. Sonrasında bu olasılıkları çarparak, ilgili senaryonun gerçekleşme ihtimalini buluruz.

$$
 P(x_1)\times P(x_2) \times P(x_3)\times P(x_4)\times P(x_5)\times P(x_6)\times P(x_7)\times P(x_8)\times ...
$$

Gördüğünüz gibi, zaman ve mekan bile büyük bir olasılık havuzu oluştururken 10<sup>-50</sup>'de 1 ihtimali oluşturmak hiç de zor değil. Fakat böyle bir ihtimalin gerçekleştiğini hepimiz [tarihi kanıtları ile beraber biliyoruz][ref4].

Böyle basit bir durum için bile bu sözde kanunun geçerliliği mümkün değil iken bunu bir **limit kanunu** olarak atfetmek ve kabul etmek "bu ne bilimsizliktir" sözünü aklıma getirmektedir.

<img alt="Bu Ne Bilimsizliktir" src="https://64.media.tumblr.com/628aa2caf061614ea433ecdfae61639e/0f3da714eebf4e5f-43/s1280x1920/974bfda8dc215e1fd8d2882ad280dc1143463324.jpg" style="width:80%; margin:0 auto; display:block" />

[Rationalwiki][ref0] adresinde zaten gerekli ve yeterli bir biçimde durum açıklanmış. Türkçesini görmeyince bir kaynak olması amacıyla da bu yazıyı yazmak istedim. Bu yazıyı yazarken benim en çok hoşuma giden söz, [Usenet](https://rationalwiki.org/wiki/Usenet)'te konunun gündem olmasıyla muhtemelen bir bilim insanının yazmış olduğu şu yorum oldu:

> Sizin var olabilmeniz için anne ve babanızın tam olarak belirli bir zamanda seks yapması gerekiyordu. Belirli bir sperm hücresinin belirli bir yumurtayı döllemesi gerekiyordu. Bunu sadece birkaç nesil geriye alarak Borel'in "yasasının" sınırına hızla ulaşırız. Siz, efendim, bu nedenle imkansızsınız.

[ref0]: https://rationalwiki.org/wiki/Borel%27s_Law
[ref1]: https://en.wikipedia.org/wiki/%C3%89mile_Borel
[ref2]: https://evrimagaci.org/evrim-teori-mi-kanunyasa-mi-5547
[ref3]: https://khosann.com/newtonin-yercekimi-yasasi-yanlis-mi/
[ref4]: https://www.timeturk.com/ataturk-u-olumden-kurtaran-saatin-markasi/haber-1679286
