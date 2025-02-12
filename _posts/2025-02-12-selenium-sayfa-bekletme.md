---
layout: single
name: selenium-ile-her-aksiyonda-sayfa-yenilemesi-yapan-javascript-kodunu-bekletme
title: "Selenium <Python> içerisinde her aksiyonda sayfa yenilemesi yapan Javascript kodu için duraklatma"
category: articles
---

Şirket içi sistemimiz üzerinde selenium <python> robotu ile bir takım aksiyonlar almaya çalıştığımda her aksiyondan sonra sayfanın sürekli kendisini Javascript ile yenilediğini ve bu yüzden her defasında programın patladığını gördüm. Yaptığım aramalar ve denemeler sonrasında aşağıdaki yöntem ile sayfanın hazırlık durumunu okuyarak ilgili problemi çözmeyi başardım. Gerek Türkçe gerekse İngilizce kaynaklarda böyle bir açıklama bulamadığım için buraya not olarak bırakıyorum.

Öncesinde ve sonrasında 0.2 sn zaman bırakmamın nedeni, selenium bazen tarayıcı aksiyonlarından daha hızlı aksiyonları almaya çalıştığından hataya sebebiyet verebiliyordu. Ben de tarayıcı ile senkronize gidebilmesi için 0.2 sn öncesi ve sonrasına ekledim.

Bu yöntem ile türlü bir sürü “try-except” kullanmadan sayfayı bekleyerek işlem yapabilmek mümkün.

```python
def element_waiter(): #Element Waiter
    time.sleep(0.20)
    while True:
        try:
            WebDriverWait(drv, 0.20).until(lambda d: d.execute_script("return document.readyState") == "complete")
            break;
        except:
            pass
    time.sleep(0.20)
```
