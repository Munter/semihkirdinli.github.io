---
layout: post
title: "Android’te Grafik Kaynakları-4 : Video Ekleme"
date: 2011-11-22 16:06
author: semihkirdinli
comments: true
categories: [Android]
tags: [3gp, Android, android grafik kaynakları, Graphic Layout, graphic resources, H.264, HTTP Server, MediaController, semih kırdinli, Uniform Resource Identifier, URI, video, VideoView]
---
Grafik Kaynakları yazı dizimizin sonuncusunda, bir Android uygulamasına nasıl video eklenir, bunu öğreneceğiz. Bazen uygulamaları emülatörde çalıştırdığımızda video’ları net gösterememe sorunu olmuştu. Bunun emülatörde çalıştığı için böyle olduğunu, gerçek ortama taşındığında bu sorunun ortadan kalkacağı konusunda birkaç yazı okumuştum.

Uygulamamıza video eklemek için VideoView sınıfını projeye import etmek gerekiyor. VideoView kontrolü de TextView, ImageView gibi bir View kontrolü. VideoView nesneleri MPEG-4 H.264([Moving Pictures Experts Group](http://tr.wikipedia.org/wiki/MPEG), *<a title="Hareketli Görüntü Uzmanları Birliği" href="http://tr.wikipedia.org/wiki/Hareketli_G%C3%B6r%C3%BCnt%C3%BC_Uzmanlar%C4%B1_Birli%C4%9Fi">*Hareketli Görüntü Uzmanları Birliği*</a>*) tarafından geliştirilen ve geliştirilmesine devam edilen çoklu-iletişim görüntü kodlama standardı, H.264 ise bir görüntü sıkıştırma standartıdır.) *videolarına erişim için kullanılmaktadır.

Bildiklerimizi bir proje üzerinde görelim. Önce bir VideoView nesnesi ekleyelim. Ardından bu nesneye kod tarafından nasıl erişilir ve video eklenir, bunu gerçekleştirelim.

**UYGULAMA**

Her zamanki gibi Eclipse IDE’sinden File–&gt;New–&gt;Other dedikten sonra **Android Project**’i seçiyoruz.

<a href="http://www.ceturk.com/images/video1.png">![android slayt](http://www.ceturk.com/images/video1-1000x364.png "video1")</a>

Main.xml’e gelerek bir VideoView nesnesi ekliyoruz. Bu işlemi ister Graphic Layout kısmından **Views** bölümü altındaki VideoView kontrolünü sürükleyerek, istersek de kod tarafından şu kodları yazarak ekleyebiliriz.


&lt;VideoView
    
    android:id=*"@+id/videoView1"*
    
    android:layout_width=*"fill_parent"*
    
    android:layout_height=*"fill_parent"*&gt;
    
    &lt;/VideoView&gt;</pre>
    <a href="http://www.ceturk.com/images/videoview21.png">![video view](http://www.ceturk.com/images/videoview21-1000x540.png "videoview2")</a>
    
    Ardından Activity sayfasına geçiyoruz. Sunucudan video’yu almak için bir yol tanımlamamız gerekiyor. Bu yüzden Uri paketini import edeceğiz. Resim gösterebilmek için ImageView içinde resmin kaynağını verdiğimiz gibi video oynatabilmek için de bir VideoView widget’ı tanımlıyoruz. Yapacağımız uygulamada, video’nun yolunu Activity sınıfında yazacağımız java kodlarıyla vereceğiz. Son olarak video’yu oynatabilmek için gerekli olan MediaController paketini import ediyoruz.
    
    Sonuç olarak import edilecek paketler aşağıdaki gibi olacak.
    <pre class="brush: java">
    android.net.Uri
    
    android.widget.VideoView
    
    android.widget.MediaController
    </pre>
    Artık java kodlarını yazmaya başlayabiliriz. Öncelikle sunucudaki video’nun yolunu veya adresini tutabilmek için Uri referans tipinde bir nesne oluşturacağız. Uri(Uniform Resource Identifier)’nin kullandığı protokollerden birisi de HTTP Server. Bu yüzden video’nun yolunu internet üzerinden verebiliriz. Uri tipinden referans alacak bir nesne tanımı yaparak, internet üzerinden verdiğimiz yolu Uri tipine parse ederek bu nesneye atıyoruz.
    <pre class="brush: java">
    Uri videoFile= Uri.parse(“http://commonsware.<span style="text-decoration:underline;">com</span>/misc/test2.3gp”);
    </pre>
    Main.xml’deki VideoView kontrolüne, tanımlamış olduğumuz Uri nesnesini set ediyoruz.
    <pre class="brush: java">
    VideoView vv=(VideoView)findViewById(R.id.*videoView1*);
    vv.setVideoURI(videoUri);
    </pre>
    Activity sınıfında yeni bir MediaController nesnesi oluşturarak, yine VideoView kontrolüne set ediyoruz.
    <pre class="brush: java">
    vv.setMediaController(**new** MediaController(**this**));
    </pre>
    Son olarak start() metoduyla video’nun oynatılmasını sağlıyoruz.
    <pre class="brush: java">
    vv.start();
    </pre>
    Avtivity sınıfının onCreate metodunda yazdığımız kodlar şu şekilde:
    <pre class="brush: java">
    Uri videoUri=Uri.*parse*("http://commonsware.com/misc/test2.3gp");
    VideoView vv=(VideoView)findViewById(R.id.*videoView1*);
    vv.setVideoURI(videoUri);
    vv.setMediaController(**new** MediaController(**this**));
    vv.start();
    

<a href="http://www.ceturk.com/images/videoactivity3.png">![video activity](http://www.ceturk.com/images/videoactivity3-1000x562.png "videoactivity3")</a>

**Not:** Bu işlemleri yaparken internetin bağlı olması gerektiğini unutmayınız.

Uygulamayı çalıştırıyoruz ve ekran çıktısı:

<a href="http://www.ceturk.com/images/ekranCiktisi4.png">![ekran çıktısı](http://www.ceturk.com/images/ekranCiktisi4.png "ekranCiktisi4")</a>



Uygulamanın kaynak kodunu indirmek için [ tıklayınız ](http://www.ceturk.com/dosyalar/ornekler/android/video-ekleme.zip)


Grafik Kaynakları yazı dizisinin sonuna geldik. Android uygulamalarının grafik tarafı ile ilgili neler yapılabilir girişini yapmış olduk. Umarım yararı olmuştur. Bir dahaki konularda görüşmek dileğiyle…
