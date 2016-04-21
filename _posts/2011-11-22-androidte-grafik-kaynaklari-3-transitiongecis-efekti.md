---
layout: post
title: "Android’te Grafik Kaynakları-3 : Transition(Geçiş) Efekti"
date: 2011-11-22 15:44
author: semihkirdinli
comments: true
categories: [Android]
tags: [Android, android grafik kaynakları, android graphic, Android xml file, apress, drawable, geçiş, getResource, ImageView, image_transition, package explorer, semih kırdinli, transition]
---
Bu makalede resimlerde transition(geçiş) konusunu ele alıyoruz. Bu özellik, bir resimden diğerine yumuşak geçiş yapmak için kullanılıyor. Bu özelliği View nesnelerine uygulayabilmek için TransitionDrawable sınıfı kullanılıyor. Nasıl yapılır sorusuna gelince, Res/drawable dizini altına koyacağımız bir xml dosyası, bu efekti vermemizi sağlayacak. Uygulamanın kod tarafı ise şöyle:

**UYGULAMA**

Eclipse IDE’sinden File–&gt;New–&gt;Other dedikten sonra **Android Project**’i seçiyoruz.

![new android project](/images/jekyll/1.png)

Gerekli işlemleri yaptıktan sonra **Finish** butonuna basarak projemizi açıyoruz.

İkinci aşamada Package Explorer bölümünden projenin isminin yazdığı yere sağ tıklıyoruz. New--Other--Android XML File’ı seçiyoruz. Ardından aşağıdaki gibi xml dosyamızı oluşturuyoruz.

![android xml file](/images/jekyll/2.png)
image_transition.xml dosyasının içindeki kodlar şu şekilde:

xml version="1.0" encoding="utf-8" transition xmlns:android="http://schemas.android.com/apk/res/android"
    item android:drawable="@drawable/and1"/item
    item android:drawable="@drawable/and2"/item /transition
![android xml](/images/jekyll/4.png)
    Resimleri eklemediğimiz için bize hata verecektir. Bu nedenle resimleri res/drawable klasörü altına ekliyoruz. Burada dikkat edilmesi gereken nokta; resimlerin ismi neyse xml kodundaki resmin de ismi aynı yazılmaktadır. Bir diğer dikkat edilmesi gereken şey ise resimlerin adını yazarken uzantısını yazmıyoruz. Şimdi main.xml dosyasına giderek bir ImageView tanımlıyoruz.
    <pre class="brush: xml">&lt;ImageView
    android:id="@+id/imgTrans"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:src="@drawable/and1"/&gt;</pre>
![ImageView](/images/jekyll/5-imageview_id.png)
Buradaki ImageView kontrolü, resimleri göstereceğimiz alanı temsil ediyor ve varsayılan resim olarak da birinci resmi gösteriyor. Artık Java kodları tarafına geçerek bu tanımlamaları kullanacağız. TransitionActivity sınıfındaki onCreate metoduna şu kodları yazıyoruz:
    <pre class="brush: java">TransitionDrawable trans=(TransitionDrawable)getResources().getDrawable(R.drawable.image_transition);
    ImageView transImage=(ImageView)findViewById(R.id.imgTrans);
    transImage.setImageDrawable(trans);
    trans.startTransition(10000);

![](/images/jekyll/5.png)

Burada 10000 değeri 10000 milisaniye, yani 10 saniyeye denk geliyor . Çalıştırdıktan 10 saniye sonra geçiş efektini görebiliriz.

Ve ekran çıktısı:

![android transition](/images/jekyll/6.png)

Uygulamanın kaynak kodunu indirmek için [ tıklayınız ](http://www.ceturk.com/dosyalar/ornekler/android/transition.zip)
