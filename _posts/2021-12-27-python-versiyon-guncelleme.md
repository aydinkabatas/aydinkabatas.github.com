---
layout: single
name: python-versiyon-guncelleme
title: "Python Versiyon Güncelleme"
category: articles
---

Son zamanlarda sektörün beni itmesinden dolayı daha fazla haşır neşir olduğum bu programlama dili, dürüst olmam gerekirse her geçen gün beni kendisine hayran bırakmayı başarıyor. *"Amaaaan alt tarafı PHP gibi, C# gibi bir programlama dili. Ne gerek var bu kadar popülerleştirmeye"* derken bir anda elimin altında vazgeçemediğim bir enstrüman haline gelmiş durumda. Tabi ki bir programlama diline böyle bağlanmaya başladığınızda, o programlama dilinin getirdiği sorunları da kabulleniyorsunuz demektir. Dürüst olmam gerekirse hiç "aman aman" bir problem ile karşılaşmadım. Bazı problemlerin etrafından dolanmam gerekliydi, bazılarında StackOverflow üzerinde biraz vakit geçirmem kâfiydi. Çoğunlukla Türkçe kaynaklar işimi görüyordu. Taa ki Python'u güncelleyene kadar...

Güncelledikten sonra güncel versiyonu kullanmadığımı fark ettim. Eski versiyonları kaldırınca bu sefer Python komple çalışmamaya başladı. Sürekli "Python yolu mevcut değil" hatası ile karşılaşınca soluğu Hz. Google'da aldım. Fakat gariptir, Türkçe kaynak olarak da problemimi çözen bir kaynağa rastlayamadım. En sonunda problemimi İngilizce aramaya başladığımda yol katetmeye başladım. Aslında çok basit olan bu problemin çözümünü de çerezlik bilgi tadında burada bulundurayım istedim.

## Peki neden?: Environment Variables neden, Could'nt Find Python sonuçtur.

Öncelikle problemin asıl kaynağı, Windows. Eğer siz, hiç Python'u kurmadan PowerShell açıp "python" yazarsanız, öncelikle Microsoft Store içerisinde böyle bir uygulama var olup olmadığına bakacak, eğer varsa Microsoft Store'u açacak, yoksa komut satırında "Böyle bir komut bulunamadı" hatası döndürecek. Programı kurduktan sonra, program içerisinde eğer **"Çevre Değişkenlerine Ekle" (Add to Environment Variables)** seçeneğini etkinleştirdiyseniz kurulum dosyası Python'un kurulduğu klasörü Windows içerisine tanımlayacak. Böylece siz PowerShell içerisinde "python" yazdığınızda karşınıza o sempatik ">>>" işareti gelecek ve Python'a göre komutları işlemeye başlayacak.

<img alt="Powershell-Python" src="/assets/images/python-powershell.png" style="width:80%; margin:0 auto; display:block" />

Buraya kadar herşey tamam. Peki ya yazılımı güncellerseniz? İşte o zaman da kullandığınız programlar (Visual Studio Code, PyCharm vs...), tanımlanan o Environment Variable Path'i izlemeye devam edecek. Sizin Python sürümünüz 3.9'dan 3.10'a çıksa da eski yolu izledikleri için eski sürümü çalıştırmaya devam edecek.

Peki güncelledikten sonra eski sürümü kaldırırsanız ne olacak? O zaman da yolu bulamadığı için yeniden size Microsoft Store'u açıp duracak. Python'unuz var, yüklü, ama kullanamıyorsunuz. Nasıl? Sinir edici öyle değil mi?

## Peki ne yapalım?: Ya temiz kurula, ya da Environment Variable değiştirile!

Aslında siz Python'u önce tamamen kaldırıp sonra yeniden temiz kurulum yapsaydınız bu problemler yaşanmayacaktı. O halde, Python'u komple kaldırıp kurmayı deneyebilirsiniz.

**"Ben üşengeçim kardeşim, kaldır-indir-kur uğraşamam"** diyenler için tavsiyem: Environment Variable'ları değiştirin. Windows 10 için arama kısmına "Çevre değişkenlerini düzenle" yazdığınızda ya da Bilgisayarım'a sağ tıklayıp **"özellikler > gelişmiş sistem ayarları > gelişmiş > çevre değişkenleri"** yolunu takip ederek ilgili pencereye ulaşabilirsiniz. Tablonun üst kısmında sizin kullanıcınız için geçerli olan **kullanıcı değişkenleri**, alt kısmında ise tüm kullanıcıları kapsayan **sistem değişkenleri** kısmı yer almakta. Herkesin kullanmasını istiyorsanız "Sistem Değişkenleri" tablosundaki **PATH** değişkenini bulup çift tıklayın. Eğer yoksa, **YENİ** diyerek oluşturabilirsiniz. Ardından Python dosyanızın bulunduğu dosya yolunu ve Script yolunu kopyalayın ve tabloya yapıştırın.


<img alt="Environment-Variables" src="/assets/images/environment-variables.png" style="width:80%; margin:0 auto; display:block" />


```
Not: Genellikle yol şu şekilde > "C:\Users\[username]]\AppData\Local\Programs\Python\[python.vers]]" ve "C:\Users\[username]]\AppData\Local\Programs\Python\[python.vers]]\Script"
```

Sonrasında oturumunuzu kapatıp açmanız yeterli. Bu yöntem bir çok *"öntanımlı programın eski versiyonu çalıştırmaya devam ettiği"* senaryoda kullanılabilir.
