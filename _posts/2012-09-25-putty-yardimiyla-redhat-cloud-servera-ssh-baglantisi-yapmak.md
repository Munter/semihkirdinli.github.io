---
layout: post
title: "Putty Yardımıyla RedHat Cloud Server’a SSH Bağlantısı Yapmak"
date: 2012-09-25 21:31
author: semihkirdinli
comments: true
categories: [Genel]
tags: [cloud, cloud server, ibm cloud, putty, redhat, server, ssh]
---
**1.Putty.exe** çalıştırılır.
![](/images/jekyll/1-connection1.png "1.connection")

**2.Session** bölümünde:
![](/images/jekyll/2-data.png "2.data")

**Host Name (or IP address):** 115.xx.xxx.xx
**Port:** (Default 22)
**Connection type:** (Default SSH)

**3.Connection** bölümünde:
**i.Data** sekmesinde **Auto-login username:** idcuser verilir.
![](/images/jekyll/3-auth.png "3.auth")

**ii.SSH-&gt;Auth**’a gelerek bağlantı için gerekli olan "**private.ppk"** dosyası eklenir. **Not:** "private.ppk" dosyasını elde etmek için: "**puttygen.exe**" çalıştırılır.

Load butonuna tıklayarak cloud server oluştururken aldığımız dosya, public key ve private key olarak kaydedilir.
![](/images/jekyll/4-puttygen.png "4.puttygen")

4.Yapmış olduğumuz ayarları kaybetmemek için: Session bölümüne tekrar gelerek **Saved Sessions**’a herhangi bir isim verilir ve **Save** butouna basılarak ayarlar kaydedilmiş olur. Ardından Open denerek bağlantı sağlanır.
