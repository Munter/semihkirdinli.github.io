---
layout: post
title: "Salt Okunur Ocak '10"
date: 2010-01-14 17:12
author: semihkirdinli
comments: true
categories: [Object Oriented Programming]
tags: [e-dergi, Ocak '10, ocp, open close principle, saü, salt okunur, SOLID]
---
Merhabalar herkese artık dergi yazılarımı blogumda da yayınlamaya karar verdim.Dergideki yazdıklarımın uçmaması için böyle bir karar aldım ve aynı zamanda dergi dışında blogdan da takip edenler olursa artık buradan okuyabilecekler her ay yazdığım yazıları.

**OPEN CLOSED PRINCIPLE(OCP)**

![](http://semihkirdinli.files.wordpress.com/2011/10/8.png "8")
Bu ay da geçen ay olduğu gibi yazılım üzerine bir konu seçtim. Yazılım geliştirmede, temel ilkelerden birisi olan Open Closed Principle(OCP). Türkçeye çevirecek olursak Açık-Kapalı Tasarım Prensipleri de denilebilir. Bu ilke Bertnard Meyer tarafından geliştirilmiş, Robert C. Martin’ in kitabında popülerleşmiştir. Peki, ne anlama geliyor bu OCP? Kodlarımızı genişletmelere açık ve modifikasyonlara kapalı olarak yazıyorsak OCP’ yi kullanıyoruz demektir.
Yeni kod yazmak mı kolay, yoksa var olan kodu değiştirmek mi? Eski kodu anlamaya çalışmak ve üzerinde değişiklik yapmak oldukça zor bir iş. Yeni yöntem ve sınıfları yazmak bu konuda daha kolay görünüyor. Eski kodu değiştirme, işlevselliğin kırılma riskini artırıyor. Bir kodun geliştirilemez olması bize hem pahalıya mal olur, hem de üretkenliği azaltır. Projemizi OCP’ ye uygun bir şekilde geliştirirsek, telafisi olmayan hatalarla sık karşılaşmayız.
Birçok program, müşteri gereksinimleri doğrultusunda ilk sürümden sonra değişikliğe uğrar. Müşteri, programı kullandıkça tanıyacak ve geliştirilip geliştirilmemesini talep edecektir. Değişiklik mutlaka olacaksa bir yazılımı gelecekteki bütün değişikliklere ayak uyduracak şekilde tasarlamak mümkün müdür? Hepsini düşünmemiz mümkün değildir, ama o anın şartlarına göre uyabildiğimiz kadarıyla OCP ilkesine göre tasarlamaya özen göstermeliyiz. Yani ensek bir yapıda programlarımızı tasarlamamız gerekiyor.
Programı geliştirmek, davranış biçimi eklemektir. Kodu değiştirmeyip, yeni kod yazmak…
Müşterinin bir gereksinimi olduğunda kodu değiştirmek zorunda kalıyorsanız OCP’ ye ters düşüyorsunuz demektir. Kod üzerinde değişiklik yaparsak, implemente etmek zorunda kalacağımız için kendimizi sonradan karmaşık bir yapı içinde bulabiliriz.
Öncelikle birbirine bağlı sınıfların esnek davranması beklenemez. Sisteme yeni bir şey eklenecek olursa sistemin birçok yerinde değişikliğe neden olacak. Bu durumda karmaşık yapılarda iş akışı hataları ve exception’ların çıkması muhtemel… Son olarak birbirine bağlı sınıfları tek başına bir yere taşıyamazsınız. Çünkü bu sınıflara doğrudan bir bağımlılık vardır.

![](http://semihkirdinli.files.wordpress.com/2011/10/8-2.png "8.2")
Diyagramda gösterilen OCP’ ye aykırı bir yazım şekli. Interface olmazsa At, Fil gibi sınıflarda yapılacak değişiklikler, HareketEt sınıfını da doğrudan etkileyecek ve yapısal değişikliğe sebep olacaktır.  Projemizi altta verilen diyagramdaki gibi tasarlarsak OCP’ ye ters düşmemiş oluruz.
![](http://semihkirdinli.files.wordpress.com/2011/10/8-3.png "8.3")
Oyna metodu sadece IHareket tipinde olan bir sınıf değişkeni üzerinde işlem yapar. Bu örnekte Oyna metodu değişikliğe kapalı, diğer tüm program gelişime açıktır. Çünkü IHareket interface sınıfını implemente ederek sisteme yeni aletleri eklemek mümkündür. Sisteme her yeni alet eklemek istediğimizde, sınıfın kendisine ait Oyna metodunu tekrar tekrar yazmamıza gerek yoktur.
Bu ayki yazımda Nesneye Dayalı Programlamanın ilkelerinden biri olan OCP’ yı gördük. Bu ilkeyi programlarımızda nasıl kullanabiliriz sorusunu kısa bir örnekle açıklamaya çalıştım.
Yazımın sonuna gelirken; gelecek ay görüşme umudumu sözlerime ekleyip herkese çalışmalarından dolayı teşekkür ediyor, değerli okurlarımıza da buradan seslenmek istiyorum.
Bizi okumaya devam edin.

![](http://semihkirdinli.files.wordpress.com/2011/10/8-4.png "8.4")
<table width="590" border="0" cellspacing="0" cellpadding="0">
<tbody>
<tr>
<td valign="top" width="403">Yararlandığım Kaynaklar:
[http://www.kurumsaljava.com](http://www.kurumsaljava.com/)
[http://www.lostechies.com](http://www.lostechies.com/)
[http://joelabrahamson.com](http://joelabrahamson.com/)
[http://en.wikipedia.org/wiki/Open/closed_principle](http://en.wikipedia.org/wiki/Open/closed_principle)</td>
<td valign="top" width="222">Semih KIRDİNLİ
semihkirdinli@gmail.com
semih.kirdinli@saltokunur.com</td>
</tr>
</tbody>
</table>
