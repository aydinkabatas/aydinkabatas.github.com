---
layout: single
name: python-ile-mssql-baglantisi-yapma
title: "Python ile MSSQL bağlantısı yapma"
category: articles
---

Veri tabanından veri çekip Python üzerinde kullanmak için aşağıdaki betikte uygun yerlere kendi veri tabanı bilgilerinizi yazmanız yeterlidir. Kodlar üzerinde açıklamalar mevcuttur.

```python
import pymssql #MSSQL bağlantısını sağlayan kütüphaneyi ekliyoruz (-pip install pymssql- ile kurulur).

conn = pymssql.connect(server="sunucuadresi", user="kullanıcıadı", password="şifre.", database="veritabanıadı") #Bağlantı bilgilerini "pymssql" ile "conn" nesnesine atıyoruz.
isaret = conn.cursor() #Connection için işaretçi oluşturuyoruz.

isaret.execute("SELECT * FROM denemetablo") #İşaretçinin metodunu içerisindeki kodu çalıştıracak şekilde çalıştırıyoruz.
row = isaret.fetchone() #Aldığı veri içerisindeki ilk satırı göstermesi için "fetchone" kullanıyoruz (tümü için "fetchall") ve "row" değişkenine atıyoruz.

conn.close() #Bağlantıyı kapatıyoruz (güvenlik için).

print(row) #Çıktıyı yazdırıyoruz.
```

Çerezlik bilgi tadında, burada bulunsun.