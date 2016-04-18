---
layout: post
title: "Putty Yardımıyla RedHat Cloud Server’a SSH Bağlantısı Yapmak"
date: 2012-09-25 21:31
author: semihkirdinli
comments: true
categories: [Genel]
tags: [cloud, cloud server, ibm cloud, putty, redhat, server, ssh]
---
**1.Putty.exe** çalıştırılır.<a href="http://semihkirdinli.files.wordpress.com/2012/09/1-connection1.png">![](http://semihkirdinli.files.wordpress.com/2012/09/1-connection1.png "1.connection")</a>

**2.Session** bölümünde:<a href="http://semihkirdinli.files.wordpress.com/2012/09/2-data.png">![](http://semihkirdinli.files.wordpress.com/2012/09/2-data.png "2.data")</a>

**Host Name (or IP address):** 115.xx.xxx.xx
**Port:** (Default 22)
**Connection type:** (Default SSH)

**3.Connection** bölümünde:
**3.1.Data** sekmesinde **Auto-login username:** idcuser verilir.<a href="http://semihkirdinli.files.wordpress.com/2012/09/3-auth.png">![](http://semihkirdinli.files.wordpress.com/2012/09/3-auth.png "3.auth")</a>

**3.2.SSH-&gt;Auth**’a gelerek bağlantı için gerekli olan "**private.ppk"** dosyası eklenir. **Not:** "private.ppk" dosyasını elde etmek için: "**puttygen.exe**" çalıştırılır.

Load butonuna tıklayarak cloud server oluştururken aldığımız dosya, public key ve private key olarak kaydedilir.<a href="http://semihkirdinli.files.wordpress.com/2012/09/4-puttygen.png">![](http://semihkirdinli.files.wordpress.com/2012/09/4-puttygen.png "4.puttygen")</a>

4.Yapmış olduğumuz ayarları kaybetmemek için: Session bölümüne tekrar gelerek **Saved Sessions**’a herhangi bir isim verilir ve **Save** butouna basılarak ayarlar kaydedilmiş olur. Ardından Open denerek bağlantı sağlanır.
