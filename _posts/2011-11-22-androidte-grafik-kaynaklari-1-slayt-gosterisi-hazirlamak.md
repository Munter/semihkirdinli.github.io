---
layout: post
title: "Android'te Grafik Kaynakları-1 : Slayt Gösterisi Hazırlamak"
date: 2011-11-22 15:33
author: semihkirdinli
comments: true
categories: [Android]
tags: [Android, android grafik kaynakları, android graphic, slayt gösterisi, slideshow]
---
Bu makalede slayt gösterisi hazırlayacağız. Konyua ait bir uygulamayı da beraber yapacağız. View nesnelerini kullanarak kontrollere ne gibi özellikler kazandırırız? Bir resmi nasıl hareketlendiririz? sorularının cevaplarını öğreneceğiz.

Android’te çözünürlüklerine göre 4 adet ekran tipi bulunmaktadır. Bunları

• 640x480 pixel - VGA
• 320x240 pixel - QVGA(Quarter screen version of VGA)
• 480x320 pixel - HVGA(Half screen version of VGA)
• 800x480 pixel - WVGA(Wide screen version of VGA)

olarak sınıflandırabiliriz. Ekran çözünürlüğü ne kadar çok olursa kullanabileceğimiz alan da o kadar çok olacaktır.

Android projemizde grafiklerle ilgili işlemler yapmak istiyorsak projemize ***android.graphics.drawable*** ve ***android.view.animation* **paketlerini import etmemiz gerekiyor.

Android framework yapısına göre kaynaklar res/drawable klasörü altında tutulur. Grafik uygulamaları için bu klasörün altına bitmap resimler, CAD çizim(şekil), gradient(aynı rengin tonlarına yumuşak geçiş), yumuşak geçiş(bir şekilden başka bir şekle yumuşak geçiş), animasyon ve görüntü geçişleri(bir resimden diğerine geçiş-slide) kaynakları eklenebilir. Res/drawable klasörünün altına atacağımız dosyaların formatı GIF,JPG veya PNG olabilir.

Grafik işlemleri için ***android.graphics.drawable ***paketinin alt sınıflarından oluşturulan BitmapDrawable object, ColorDrawable object, GradientDrawable object, AnimationDrawable object(bizim projemizde kullanacağımız), TransitionDrawable object veya NinePatchDrawable object gibi nesnelere ihtiyaç duyarız.

**UYGULAMA**

Uygulamamıza Eclipse IDE’sinden File à New à Other dedikten sonra Android klasöründen **Android Project**’i seçerek başlıyoruz. Ardından açılan wizard’ta Project name kısmından proje adını veriyoruz. Build Target bölümünden Android versiyonunu seçiyoruz(Burası önemli, Android versiyonunu burada ne seçtiysek aşağıdaki Min SDK Version bölümüne buradaki versiyon sürüm numarasının tam 2 katını yazıyoruz). Projemizde 1.5 seçmiştik. Bu yüzden aşağıda Min SDK Version bölümünün değerine 3 yazdık. Application name kısmında uygulamaya isim verdik. Package name kısmı da önemli(Burada vereceğimiz isim ise araya nokta koymak şartıyla en az 2 kelimeden oluşmalıdır). Projemizde Package name kısmına isim olarak com.graphicapp verdik. Bir de Java aktivite sınıfına isim veriyoruz ve Finish diyerek bitiriyoruz.

<a href="http://www.ceturk.com/images/1.open_.png">![open-image](http://www.ceturk.com/images/1.open_.png)</a>

İlk uygulamamız bitmap resimler kullanarak çerçeve tabanlı animasyon yapmak. Bunun için önce resimleri res/drawable dosyasının altına kopyalayacağız. Ardından aynı klasör içine bir de XML dosyası koyacağız. Bu da resimleri referans eden dosya olacak. Kaynak olarak bu dosyayı verdiğimizde bir animasyon elde etmiş olacağız.

<a href="http://www.ceturk.com/images/2.newXMLFile.png">![](http://www.ceturk.com/images/2.newXMLFile.png)</a>

<a href="http://www.ceturk.com/images/3.XMLName.png">![](http://www.ceturk.com/images/3.XMLName.png)</a>

Resimleri res/drawable klasörünün altına şekildeki gibi attık. Daha sonra drawable klasörüne sağ tıklayarak New à Other à File dedik ve gelen wizard’ta Next butonuna bastıktan sonra XML dosyamızın adını **logo_animation.xml** olarak verdik ve işlemi tamamladık. XML dosyasının içine yazacağımız kodlar :


**&lt;?xml version="1.0" encoding="utf-8"?&gt;**
    **&lt;animation-list** xmlns:android="http://schemas.android.com/apk/res/android"
    android:oneshot="false"&gt;
    &lt;item android:drawable="@drawable/resim1" android:duration="2000" /&gt;
    &lt;item android:drawable="@drawable/resim2" android:duration="2000" /&gt;
    &lt;item android:drawable="@drawable/resim3" android:duration="2000" /&gt;
    &lt;item android:drawable="@drawable/resim4" android:duration="2000" /&gt;
    &lt;item android:drawable="@drawable/resim5" android:duration="2000" /&gt;
    &lt;item android:drawable="@drawable/resim6" android:duration="2000" /&gt;
    **&lt;/animation-list&gt; **</pre>
    <a href="http://www.ceturk.com/images/4.XML_icerik.png">![](http://www.ceturk.com/images/4.XML_icerik.png)</a>
    
    Şimdi sırada animasyonu oynatmak var. Bizim yapacağımız örnekte resimlerin boyutları hep aynı kalmakta, sadece içerisindeki resim değişmektedir. Bu şekilde yapılan animasyonlar transform-based(biçim değiştirme tabanlı) deniyor. Bunun için main.xml ‘e bir ImageView kontrolü ekliyoruz.
    
    **Main.xml kodları :**
    <pre class="brush: xml">&lt;?xml version="1.0" encoding="utf-8"?&gt;
    
    &lt;LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical"
    android:layout_width="fill_parent"
    android:layout_height="fill_parent"&gt;
    
    &lt;ImageView
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:id="@+id/imageView"/&gt;
    
    &lt;/LinearLayout&gt;</pre>
    <a href="http://www.ceturk.com/images/5.ImageView_id.png"> ![](http://www.ceturk.com/images/5.ImageView_id.png)</a>
    <pre class="brush: java">import android.view.MotionEvent;
    import android.widget.ImageView;
    import android.graphics.drawable.AnimationDrawable;
    
    public class GraphicAppActivity extends Activity {
        AnimationDrawable logoAnimation;
        @Override
        public void onCreate(Bundle savedInstanceState) {
            super.onCreate(savedInstanceState);
            setContentView(R.layout.main);
    
            ImageView logoImage = (ImageView) findViewById(R.id.imageView1);
            logoImage.setBackgroundResource(R.drawable.logo_animation);
            logoAnimation = (AnimationDrawable) logoImage.getBackground();
        }
    
        public boolean onTouchEvent(MotionEvent event) {
            if (event.getAction() == MotionEvent.ACTION_DOWN) {
                logoAnimation.start();
                return true;
            } else
                return super.onTouchEvent(event);
        }
    }</pre>
    <a href="http://www.ceturk.com/images/6.Java_aktivite.png">![](http://www.ceturk.com/images/6.Java_aktivite.png)</a>
    
    Bu kodlarla önce animasyonun hareket yeteneği kazanabilmesi için AnimationDrawable sınıfından bir nesne türettik. Önceden oluşturmuş olduğumuz ImageView kontrolüne Id’si ile ulaştık. Daha sonra ekrana dokunduğunda bu animasyonu oynat dedik.
    
    Uygulamayı **onTouchEvent** içinde start ettiğimiz için ekrana dokunmadan slayt başlamayacaktır. Bu uyarıyı ekrana yazdırmak için main.xml dosyasında ImageView’in üstüne bir TextView ekleyeceğiz.
    
    TextView’in text özelliğine de vermek istediğimiz uyarıyı yazacağız. Main.xml içinde yazdığımız kodlar :
    <pre class="brush: xml">&lt;TextView
    android:layout_width=*"wrap_content"*
    android:layout_height=*"wrap_content"*
    android:text=*"Ekranın herhangi bir yerine dokunduğunuzda slayt gösterisi başlayacaktır."*/&gt;

<a href="http://www.ceturk.com/images/7.uyariText.png"> ![](http://www.ceturk.com/images/7.uyariText.png)</a>

**Uygulamanın ekran çıktısı :
**

<a href="http://www.ceturk.com/images/8.ekranCiktisi.png">![](http://www.ceturk.com/images/8.ekranCiktisi.png)</a>

Uygulamanın kaynak kodunu indirmek için [tıklayınız](http://www.ceturk.com/dosyalar/ornekler/android-GraphicApp-slide-show.rar)
