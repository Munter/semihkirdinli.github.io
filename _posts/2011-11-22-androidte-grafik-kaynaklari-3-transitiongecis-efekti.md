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

<a href="http://www.ceturk.com/images/11.png">![new android project](http://www.ceturk.com/images/11-1000x363.png)</a>

Gerekli işlemleri yaptıktan sonra **Finish** butonuna basarak projemizi açıyoruz.

İkinci aşamada Package Explorer bölümünden projenin isminin yazdığı yere sağ tıklıyoruz. New--&gt;Other--&gt;Android XML File’ı seçiyoruz. Ardından aşağıdaki gibi xml dosyamızı oluşturuyoruz.

<a href="http://www.ceturk.com/images/21.png">![android xml file](http://www.ceturk.com/images/21-1000x539.png)</a>
image_transition.xml dosyasının içindeki kodlar şu şekilde:


&lt;?xml version="1.0" encoding="utf-8"?&gt;
    &lt;transition xmlns:android="http://schemas.android.com/apk/res/android"&gt;
    &lt;item android:drawable="@drawable/and1"&gt;&lt;/item&gt;
    &lt;item android:drawable="@drawable/and2"&gt;&lt;/item&gt;
    &lt;/transition&gt;</pre>
    <a href="http://www.ceturk.com/images/2.png">![android xml](http://www.ceturk.com/images/2-1000x540.png)</a>
    Resimleri eklemediğimiz için bize hata verecektir. Bu nedenle resimleri res/drawable klasörü altına ekliyoruz. Burada dikkat edilmesi gereken nokta; resimlerin ismi neyse xml kodundaki resmin de ismi aynı yazılmaktadır. Bir diğer dikkat edilmesi gereken şey ise resimlerin adını yazarken uzantısını yazmıyoruz. Şimdi main.xml dosyasına giderek bir ImageView tanımlıyoruz.
    <pre class="brush: xml">&lt;ImageView
    android:id="@+id/imgTrans"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:src="@drawable/and1"/&gt;</pre>
    <a href="http://www.ceturk.com/images/4.png">![ImageView](http://www.ceturk.com/images/4-1000x540.png)</a>Buradaki ImageView kontrolü, resimleri göstereceğimiz alanı temsil ediyor ve varsayılan resim olarak da birinci resmi gösteriyor. Artık Java kodları tarafına geçerek bu tanımlamaları kullanacağız. TransitionActivity sınıfındaki onCreate metoduna şu kodları yazıyoruz:
    <pre class="brush: java">TransitionDrawable trans=(TransitionDrawable)getResources().getDrawable(R.drawable.image_transition);
    ImageView transImage=(ImageView)findViewById(R.id.imgTrans);
    transImage.setImageDrawable(trans);
    trans.startTransition(10000);

<a href="http://www.ceturk.com/images/5.png">![](http://www.ceturk.com/images/5-1000x562.png)</a>

Burada 10000 değeri 10000 milisaniye, yani 10 saniyeye denk geliyor . Çalıştırdıktan 10 saniye sonra geçiş efektini görebiliriz.

Ve ekran çıktısı:

<a href="http://www.ceturk.com/images/6.png">![android transition](http://www.ceturk.com/images/6.png)</a>

Uygulamanın kaynak kodunu indirmek için [ tıklayınız ](http://www.ceturk.com/dosyalar/ornekler/android/transition.zip)
