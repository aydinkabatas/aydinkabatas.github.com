---
layout: single
name: linuxa-donus
title: "Linux'a Dönüş"
category: articles
---

Öncelikle bunu bir **Linux github denemesi** olarak atacağım. Ardından bunun üzerine konuşacağız. *(Devamı ~~gelecek~~ geldi)*

Bir süre önce *(ki bu da bu postu attığım tarihe tekabul eder)* kesin dönüş yaparak tekrar Linux işletim sistemine geçiş yaptım. Windows işletim sisteminin bu bilgisayar üzerinde aşırı hantallığını ve SSD üzerinde kapladığı yüksek boyutu görünce Linux alternatifini tekrar gözden geçirmeye karar verdim. Beni tanıyanlar açık kaynak kodlu sistemleri ne kadar sevdiğimi, bu camiaya ne kadar gönül verdiğimi bilir. Mesleğim sebebi ile kullanmak zorunda olduğum programlar Windows üzerinde çalıştığından ve Linux'un ciddi bir stabilizasyon problemi olduğundan uzun bir süre Windows ile ilişkimiz devam etti. SSD'den sonra işletim sistemi o kadar yorgunluk yaratmasa da gün geçtikçe gelen güncelleştirmeler yavaş yavaş Windows hantallığını hissettirmeye başlamıştı.

![Linux](../../assets/images/linux.png "Linux"){:style="padding-left:10%;width:90%"}

Son zamanlarda internet üzerinde Linux için yazılan yazılımların sayısı bir hayli dikkatimi çekmeye başladı. Ayrıca yazılım geliştiricileri çoğu yorumlarda Linux'un stabilite problemlerini büyük ölçüde aştığını vurguluyordu. İş ortaklarımızdan birinde de Linux işletim sistemlerinden Ubuntu üzerinde geliştirme yaptığını görünce *"Sanırım geçiş yapmak için en uygun zaman, bu zaman"* diye düşündüm. *"Hantallaşmış bu bilgisayarı madem formatlayacağım, Linux'a yeniden bir şans vermeliyim"* diye düşünerek **Ubuntu Mate 20.04 LTS** kurulumunu tamamladım.

İlk iş olarak arayüzü kullanabileceğim, düzenli hale getirmeye başladım. Burada **"Welcome"** uygulamasının gerçekten çok yardıcı olduğunu fark ettim. Farklı arayüz seçenekleri içerisinde bana en uygun olanının **"Munity"** olduğunu fark edip ilgili arayüzün kurulumunu tamamladım.

![Ekran Görüntüsü](../../assets/images/screenshot.png "Ekran Görüntüsü"){:style="padding-left:10%;width:90%"}

Ardından bir bilgisayarda bulunması gereken temel uygulamaları kurmaya başladım. **"Libreoffice, Google Chrome, VLC Player, Spotify, GIMP, Atril, Engrampa** ilk kurduğum uygulamalar arasında yerini aldı.

Ardından *arada bilgisayar oyunlarına bir göz atarım* umuduyla **"Steam"** kurulumu yaptım. **"Dota 2, Champions of Regnum, CS:GO, Outlast, Life is Strange"** oyunları ilk indirdiğim oyunlar oldu.

Bu arada Linux ile ilgili bir eksiyi not olarak düşmem gerekli. Linux işletim sistemlerinin büyük bir çoğunluğu AMD Radeon HD 6xxxM serisi ekran kartlarını desteklemiyor. Bu sebeple ilgili sürücü kurulumlarını yapamıyorsunuz ve bilgisayarınız o anki entegre Intel HD serisi ekran kartı ile çalışıyor. İnterneti biraz karıştırınca birkaç yazı görüyorum, fakat yazının yorumlarında çoğunlukla *"Bilgisayarı yeniden formatlamak zorunda kaldım"* şeklindeki yorumları okuyunca vazgeçiyorum. Bu sebeple eski ekran kartı sürümlerini kullanıyorsanız *(özellikle AMD'nin Switchable teknolojiisini kullanan)* ekran kartından feragat etmeniz gerektiğini hatırlatayım. Ayrıca eski bluetooth kartının da sorun çıkarttığını belirtmeliyim. Ara ara ses kesintileri olmakta. 

Buna karşın sağladığı yüksek performans sayesinde ekran kartının yokluğunu hissettirmediğini belirtmeliyim. Ayrıca Ubuntu Mate'ye geçtiğimden beri bilgisayarımın şarjı gerçekten çok daha uzun süre gidiyor. Windows'ta Netflix'ten bir dizi izlemeye çalıştığımda yarım saatte pil kritik uyarısı alırken Linux'ta bu süre iki katından fazla. Ayrıca depolama konusunda gerçekten çok cimri. Mate kurulumu sonrası işletim sistemi sadece 3 GB'lık yer kaplıyordu. Windows 10'u temel kurulumla kursanız dahi min 16-20GB arası yer kaplıyor.

Tüm bu kurulumların ardından ihtiyacım olan **"Yazılım Geliştirme"** işleri için gerekli olan programları kuruyorum. **"Visual Studio Code, Azure Data Studio, MS-SQL for Linux, Github, LAMP"** kurduğum programlardan başlıcaları. Her ne kadar "İstatistikçi" olsak da gönlümüz halen "Yazılım Geliştiricisi" olmaktan yana.

Tabi aldığım freelance İstatistik işlerini yapmak için Windows'a ihtiyacım vardı. Burada yardımıma **"Virtualbox"** yetişti. İçerisine en güncel Windows sürümünü kurdum. Ardından **"Minitab, SPSS, AMOS, MS-Office, Peazip"** programlarını kurdum.

Böylece tam olarak sistemim hazır oldu. Zorunlu olmadıkça her şeyi Linux üzerinden çözeceğim. Analiz işlerinde ise Windows'a Virtualbox üzerinden bağlanarak erişmiş olacağım. Bu esnada tüm bu kurulumlara ve yüklere rağmen Virtualbox kapalı 5481MB ram bellek boşta gözükmekte (virtualbox açık iken 1282MB - 6GB atama yapıldı). Ayrıca VirtualBox içerisinde 50GB'lık işletim sistemi olmasına ve tüm bu program-oyun kurulumlarına rağmen 240GB'lık HDD'nin 108GB'ı boş gözükmekte (ki *Mate Disk Utility* ile analiz yaptığımda oyunların da 51GB kapladığı gözükmekte).

---

Son zamanlarda stabilizasyon problemleri de çözülmüş olan bu işletim sistemini **KULLANMAYI BİLEN** herkese tavsiye ederim.