---
layout: single
name: web-sitesindeki-tum-yer-imi-ve-urlleri-listeleme
title: "Web Sitesindeki Tüm Yer İmi ve URL'leri Listeleme"
category: articles
---

[Daniel Foley Carter][ref1]'dan alıntıdır.

Web sitesi içerisindeki tüm yer imi ve URL'leri bir tablo içerisinde listelemek için öncelikle ilgili site içerisinde tarayıcımızdan **Geliştirici Araçları** kısmına girip **Console**'u açmamız gerekli.

Konsola aşağıdaki javascript kodunu yazdığımızda pop-up pencere açarak o sayfadaki tüm linkleri listeleyecektir.

```javascript
var x = document.querySelectorAll("a");
var myarray = []
for (var i=0; i<x.length; i++){
var nametext = x[i].textContent;
var cleantext = nametext.replace(/\s+/g, ' ').trim();
var cleanlink = x[i].href;
myarray.push([cleantext,cleanlink]);
};
function make_table() {
var table = '<table><thead><th>Name</th><th>Links</th></thead><tbody>';
for (var i=0; i<myarray.length; i++) {
table += '<tr><td>'+ myarray[i][0] + '</td><td>'+myarray[i][1]+'</td></tr>';
};

var w = window.open("");
w.document.write(table);
}
make_table()
```

## Peki bu ne işimize yarayacak?

E-ticaret'te rakiplerin kampanyalarını takip etmek en önemli işlerden birisi. Bu veriyi bir veri tabanı içerisine yazıp python ile belirli aralıklarda karşılaştırmalar yapılırsa rakipler yeni bir kampanya hazırladıklarında linkleri direkt olarak listelenebilecektir.

Ayrıca rakiplerin link yapısını çözümlemek için de güzel bir alternatif olarak gözükmektedir.

[ref1]: https://www.linkedin.com/feed/update/urn:li:activity:6793002499134550016/ "Daniel Foley Carter Linkedin Profili"