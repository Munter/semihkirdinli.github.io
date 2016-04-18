---
layout: post
title: "UML (Unified Modelling Language)"
date: 2009-10-06 16:33
author: semihkirdinli
comments: true
categories: [Object Oriented Programming]
tags: [birleşik modelleme dili, uml, Unified Modelling Language, use case]
---
Türkçe olarak "Birleşik Modelleme Dili" şeklinde adlandırılabilir. UML bir programlama(yada yazılım geliştirme) dili olmaktan ziyade, iş sistemlerinin nasıl modellenebileceğini belirleyen ve açıklayan yöntemlerin bir araya toplanmış halidir.

UML'in belkide en kullanışlı diyebileceğimiz diyagram türü olan Etkinlik Diyagramları(Activity Diagram) ile yazılım haline getirilmek istenen süreçler, herkesin anlayabileceği şekilde görüntülenebilir. Bu açıdan etkinlik diyagramları hem yazılımcıya hem de yazılımı kullanacak olan kişilere net bir görüş sağlar.

UML diyagramları, bir sistem modelini 3 farklı açıdan ele alırlar.

## İşlevsel Gereksinimler Açısından:
Kullanıcının bakış açısından sistemin gereksinimleri vurgulanır. Kullanım Senaryosu(use-case) diyagramını içerir.

## Statik Yapısal Açıdan:
Nesneler, nesnelere ait özellikler ve ilişkiler kullanılarak sistemin statik yapısı incelenir. Sınıf(Class) ve Birleşik Yapı(Composite Structure) diyagramlarını içerir.

## Dinamik Davranış Açısından:
Nesneler arası ortak çalışmalar ve nesnelerin durumlarındaki değişiklikler gösterilerek sistemin dinamik davranışı incelenir. Sıralama(Sequence), Faaliyet(Activity) ve Durum(Statechart) diyagramlarını içerir.

> Use-case:
Sistemin kullanıcılara sunacağı bir hizmetin senaryo şeklinde anlatımıdır. Sistem gereksinimleri, Use Case diyagramları ile belirtilir. Yazılım geliştirme için gerekli değildir, fakat gereksinimler ve nesnesel modeller arasında en önemli bağlantıdır.

__Sembol Açıklaması:__
__use-case:__ Belli bir hedefe ulaşmak için kullanılabilecek tüm alternatif senaryolar.
__aktör:__ Sistemle etkileşen kişilerin canlandırdıkları roller ve dış sistemler.
__extend:__ Bir usecase’in kullanıcısının bağlı olarak çalıştırdığı diğer usecase’i vurgular.
__include:__ Bir usecase’nin her zaman çalıştırdığı diğer bir usecase’i vurgular.

![örnek uml tablosu](/images/jekyll/62.gif)

Bir sınıf; ortak yapısı, ortak davranışları, ortak ilişkileri ve ortak semantiği bulunan nesneler koleksiyonudur.

* UML’ de üç farklı alanı olan bir dikdörtgen şeklinde gösterilirler.
* Bu üç bölümden ilki sınıf ismini, ikinci kısım yapısını(attributes), ve üçüncü bölüm ise davranışını(operations) gösterir.
* Sınıfların gösteriminde sadece sınıf ismini, yapısını ya da davranışlarını veya her üçünü de birden görebilirsiniz.
* Sınıflar isimlendirilirken bir standardizasyon olması amacıyla bütün isimler büyük harf  ile başlarlar.

1.SINIF ADI
2.ÖZELLİKLER
3.METOTLAR
