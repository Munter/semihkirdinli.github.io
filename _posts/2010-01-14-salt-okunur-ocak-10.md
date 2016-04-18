---
layout: post
title: "Salt Okunur Ocak '10"
date: 2010-01-14 17:12
author: semihkirdinli
comments: true
categories: [Object Oriented Programming]
tags: [e-dergi, Ocak '10, ocp, open close principle, saü, salt okunur, SOLID]
---
Merhabalar herkese artık dergi yazılarımı blogumda da yayınlamaya karar verdim. Dergideki yazdıklarımın uçmaması için böyle bir karar aldım ve aynı zamanda dergi dışında takip edenler olursa buradan okuyabilirler.

## Open Closed Principle(OCP)

![](/images/jekyll/8.png "8")

Dergide bu ay da geçen ay olduğu gibi yazılım üzerine bir konu seçtim. Yazılım geliştirmenin temel ilkelerinden birisi olan Open Closed Principle(OCP). Türkçe anlamıyla Açık-Kapalı Tasarım Prensipleri de denilebilir. Bu ilke Bertnard Meyer tarafından geliştirilmiş, Robert C. Martin’ in kitabında popülerleşmiştir. OCP ne anlama geliyor derseniz: Kodlarımızı genişletmelere açık ve modifikasyonlara kapalı olarak yazmak anlamına geliyor.

* Yeni kod yazmak mı kolay, yoksa var olan kodu değiştirmek mi? Eski kodu anlamaya çalışmak ve üzerinde değişiklik yapmak oldukça zor bir iş. Yeni yöntem ve sınıfları yazmak daha kolay görünüyor. Eski kodu değiştirme, işlevselliğin kırılma riskini artırıyor. Bir kodun geliştirilemez olması bize hem pahalıya mal olur hem de üretkenliği azaltır. Projemizi OCP’ye uygun bir şekilde geliştirirsek, telafisi olmayan hatalarla sık karşılaşmayız.

* Birçok program, müşteri gereksinimleri doğrultusunda ilk sürümden sonra değişikliğe uğrar. Müşteri, programı kullandıkça tanıyacak ve geliştirilip geliştirilmemesini talep edecektir. Değişiklik mutlaka olacaksa, bir yazılımı gelecekteki bütün değişikliklere ayak uyduracak şekilde tasarlamak mümkün müdür? Hepsini düşünmemiz mümkün değildir, ama OCP ilkesine göre tasarlama yaklaşımında olmak yararımıza olacaktır.

* Programı geliştirmek, davranış biçimi eklemektir. Kodu değiştirmeyip, yeni kod yazmak… Müşterinin bir gereksinimi olduğunda kodu değiştirmek zorunda kalıyorsak OCP’ye ters düşüyoruz demektir. Kod üzerinde değişiklik yaparsak, implemente etmek zorunda kalacağımız için kendimizi sonradan karmaşık bir yapı içinde bulabiliriz.

* Öncelikle birbirine bağlı sınıfların esnek davranması beklenemez. Varolan uygulamaya yeni bir özellik eklemek, uygulamanın birçok yerinde değişikliğe neden olacak. Bu durumda karmaşık yapılarda iş akışı hataları ve exception’ların çıkması muhtemel… Ayrıca birbirine bağlı sınıfları tek başına bir yere taşıyamazsınız. Çünkü bu sınıflara doğrudan bir bağımlılık vardır.

![Resim 1](/images/jekyll/8-2.png "8.2")
* Diyagramda gösterilen OCP’ ye aykırı bir yazım şekli. Interface olmazsa At, Fil gibi sınıflarda yapılacak değişiklikler, HareketEt sınıfını da doğrudan etkileyecek ve yapısal değişikliğe sebep olacaktır.  Projemizi altta verilen diyagramdaki gibi tasarlarsak OCP’ ye ters düşmemiş oluruz.

![Resim 2](/images/jekyll/8-3.png "8.3")
* Oyna metodu sadece IHareket tipinde olan bir sınıf değişkeni üzerinde işlem yapar. Bu örnekte Oyna metodu değişikliğe kapalı, diğer tüm program gelişime açıktır. Çünkü IHareket interface sınıfını implemente ederek sisteme yeni özellikleri eklemek mümkündür. Sisteme her yeni özellik eklemek istediğimizde, sınıfın kendisine ait Oyna metodunu tekrar tekrar yazmamıza gerek yoktur.

Bu ay yazımda Nesneye Dayalı Programlamanın ilkelerinden biri olan OCP’yi elimden geldiği kadarıyla anlatmaya, bu yaklaşımda nasıl kod geliştirmemiz geliştiririz, kısa bir örnekle açıklamaya çalıştım.

Yazımın sonuna gelirken; gelecek ay görüşme umudumu sözlerime ekleyip herkese çalışmalarından dolayı teşekkür ediyorum.
Bizi okumaya devam edin.


### Yararlandığım Kaynaklar:

* [kurumsaljava.com](http://www.kurumsaljava.com/ "www.kurumsaljava.com")
* [lostechies.com](http://www.lostechies.com/ "www.lostechies.com")
* [joelabrahamson.com](http://joelabrahamson.com/ "joelabrahamson.com")
* [en.wikipedia.org/wiki/Open/closed_principle](http://en.wikipedia.org/wiki/Open/closed_principle "en.wikipedia.org/wiki/Open/closed_principle")
