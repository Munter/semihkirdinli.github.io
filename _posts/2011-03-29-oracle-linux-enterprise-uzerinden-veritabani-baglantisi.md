---
layout: post
title: "Oracle Linux Enterprise Üzerinden Veritabanı Bağlantısı"
date: 2011-03-29 01:49
author: semihkirdinli
comments: true
categories: [Oracle]
tags: [linux, linux terminal, listener, oracle, sqlplus, sysdba, veritabanı]
---
**1) Sqlplus bağlantısı yapmak**

oracle kullanıcısıyla bağlanıp

**sqlplus / as sysdba**

komutunu yazıyoruz.

**2) Sql'i devreye sokmak**** **

**startup;**

diyerek boşta olan oracle'ı devreye sokuyoruz.
Şimdi komutlarımızı terminal üzerinden yazabiliriz.

Örneğin:  select name from v$database;

diyerek veritabanının ismini öğrenebiliriz.

**3) Listener açmak**** **

Eğer dışardan bir program aracılığıyla sorgularımızı yazmak istersek listener açmamız gerekir.
Bunu da şöyle yapabiliriz. Sql'den oracle user'a geri gelmeliyiz. oracle user'dayken

**lsnrctl start**

dememiz listener açmamız için yeterli olacak.
Artık komutlarımızı dilediğimiz yerden yazabiliriz.
İsterseniz Linux'ta bulunan terminal'den yazabilirsiniz,
isterseniz de sql developer, toad gibi araçlar kullanabilirsiniz.

**4) Veritabanını güvenli bir şekilde kapatmak**

En son işimiz bittikten sonra veritabanını güvenli bir şekilde

kapatmak için kullandığımız komut ise sql içinde

**shutdown immediate;**

![](http://semihkirdinli.files.wordpress.com/2011/10/25.png "25")

Şimdilik anlatacaklarım bu kadar. Tekrar görüşmek dileğiyle...
