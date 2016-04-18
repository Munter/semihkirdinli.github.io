---
layout: post
title: "ASP.NET’te Chart Kontrolü Kullanırken Temp Directory Sorunu"
date: 2011-08-24 20:41
author: semihkirdinli
comments: true
categories: [ASP.NET]
tags: [asp.net, error, permissions for tempImages, temp directory]
---
Merhabalar bu yazıda ASP.NET 4.0 ile gelen Chart kontrolünün sebep olduğu bir hatayı inceleyeceğiz.
<a href="http://semihkirdinli.files.wordpress.com/2011/10/32.png">![](http://semihkirdinli.files.wordpress.com/2011/10/32.png "32")</a>
“The temp directory in chart handler configuration is not accessible” hatası, projemizin kök dizininde bir “temp” klasörü bulunmadığından kaynaklanmaktadır. Bu nedenle projemizin kök dizinine “tempImages” adında bir klasör ekleyerek Web.config dosyamızda da etiketinin altında

&lt;add key=**"**ChartImageHandler**"** value=**"**Storage=file; Timeout=20; Url=~/tempImages/; **"**/&gt;

şeklinde bir key oluşturmalıyız. Daha sonra “tempImages” dosyasının fiziksel yoluna gitmeliyiz. Burada “tempImages” e sağ tıklayıp Properties’ i seçerek Security sekmesinde Edit butonuna tıklıyoruz. Önce “Group or user names” bölümünden “Users” ı seçiyoruz. Daha sonra da “Permissions for Users” bölümünden de Full control’ü “Allow” olarak işaretleyerek işlemleri onaylıyoruz.
<a href="http://semihkirdinli.files.wordpress.com/2011/10/32-1.png">![](http://semihkirdinli.files.wordpress.com/2011/10/32-1.png "32.1")</a>
Bu şekilde sorunun ortadan kalktığını göreceğiz.
