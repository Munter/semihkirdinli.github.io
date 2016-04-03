---
layout: post
title: "Android’te Grafik Kaynakları-2 : View Nesnelerine Hareket Kazandırmak"
date: 2011-11-22 15:39
author: semihkirdinli
comments: true
categories: [Android]
tags: [Android, android grafik kaynakları, android graphic]
---
Grafik kaynakları makalelerimizin 2.si olan bu makalede, View nesnelerinin nasıl hareketlendirileceğini öğreneceğiz. View nesneleri burada TextView, ImageView gibi kontroller olabilir. Bir View nesnemiz olduğunu düşünelim. Bizim burada yapacağımız şey view nesnesini büyütüp küçülterek ve genişletip daraltarak hareketlendirmek. Şimdi anlattıklarımızı bir uygulamayla pekiştirelim.

**UYGULAMA**
Makale serimizin ilkinde olduğu gibi File--&gt;New--&gt;Other dedikten sonra **Android Project**’i seçiyoruz. Burada, geçen makalemizde de belirttiğimiz ayarlamaları yaparak **Finish** diyoruz.

<a href="http://www.ceturk.com/images/1.file_new1.png">![](http://www.ceturk.com/images/1.file_new1-1000x704.png)</a>

Yeni Android projemizi oluşturduktan sonra Project Explorer’da bulunan projemizin üstüne yeni bir xml dosyası eklemek üzere sağ tıklayıp New--&gt;Other--&gt;Android--&gt;Android XML File’ı seçiyoruz.

<a href="http://www.ceturk.com/images/2.package_explorer.png">![](http://www.ceturk.com/images/2.package_explorer-1000x562.png)</a>

<a href="http://www.ceturk.com/images/3.new_android_xml_file.png">![](http://www.ceturk.com/images/3.new_android_xml_file.png)</a>

Görüldüğü gibi **img_animation** adında bir xml dosyası oluşturduk. Ayrıca **res** klasörü altına kendiliğinden **anim** adında bir klasör daha oluşturdu ve oluşturduğumuz xml dosyasını da anim klasörünün içine attı. Şimdi view nesnemizin hareket edebilmesi için gereken kodları img.animation.xml dosyasının içine aşağıdaki gibi yazıyoruz.

<a href="http://www.ceturk.com/images/4.img_animation.png">![](http://www.ceturk.com/images/4.img_animation-1000x562.png)</a>

Xml dosyamızı oluşturduktan sonra res/drawable altına göstereceğimiz resmi, main.xml’e de şu kodları yazarak ImageView nesnesi ekliyoruz.

<a href="http://www.ceturk.com/images/5.main_xml.png">![](http://www.ceturk.com/images/5.main_xml-1000x562.png)</a>

Burada id olarak da imageView1 verdik. Bildiğimiz gibi, bir view nesnesine java sınıflarından erişebilmek için id veriyorduk. Şimdi java kodlarımızı yazmak için MoveAppActivity adını verdiğim Java Activity Class’a aşağıdaki kodları yazacağız. Önce ImageView nesnesine erişeceğiz. Ardından img_animation dosyasındaki özellikleri ImageView nesnesinin kullamasını sağlayacağız.

Java kodları :


ImageView imgViewObj = (ImageView)findViewById(R.id.imageView1);
            Animation imgAnim=AnimationUtils.loadAnimation(this, R.anim.img_animation);
            imgViewObj.startAnimation(imgAnim);</pre>
    Bu kodları yazarken sınıflara ait paketleri de import etmemiz gerekiyor. Bunlar :
    <pre class="brush: java">import android.view.animation.Animation;
    import android.view.animation.AnimationUtils;
    import android.widget.ImageView;

<a href="http://www.ceturk.com/images/6.JavaActivity.png">![](http://www.ceturk.com/images/6.JavaActivity-1000x562.png)</a>

Projeyi çalıştırdığımızda ekran çıktısı aşağıdaki gibi olacak. Hareket ettiğini de görmüş olacağız.

<a href="http://www.ceturk.com/images/7.cikti_.png">![](http://www.ceturk.com/images/7.cikti_.png)</a>

Uygulamanın kaynak kodunu indirmek için [ tıklayınız ](http://www.ceturk.com/dosyalar/ornekler/android-move-app.zip)
