---
layout: post
title: "ASP.NET ReportViewer Kontrolü Kullanarak Rapor Oluşturmak"
date: 2011-06-25 19:24
author: semihkirdinli
comments: true
categories: [.NET Framework, ASP.NET, Reporting Service]
tags: [asp.net, c#, data mining, dataset, dinamik raporlama, raporlama, reporting service, reportviewer, veri madenciliği]
---
Yeni bir ASP.NET Project açarak işe başlayalım.

Raporlarlarımızın verisini Dataset’ten alacağımız için projemize bir DataSet ekleyelim. * Add New Item --&gt; DataSet*. İsmi önemli değil. Bize *App_Code* da projeye dahil olsun mu diye sorarsa evet diyerek devam ediyoruz. Veritabanını önceden hazırladığımızı ve projeye eklediğimizi kabul ediyorum(Veritabanının nasıl olduğu çok önemli değil).
![](http://semihkirdinli.files.wordpress.com/2011/10/29.png "29")
Şimdi Microsoft Visual Studio üzerindeyken *“Ctrl + Alt + S”* tuş kombinasyonunu kullanarak sol tarafta bulunan *“Server Explorer”* bölümünden önceden hazırlamış olduğumuz tablo veya view’leri sürükleyerek **Dataset1.xsd** içine bırakıyorum.
<a href="http://semihkirdinli.files.wordpress.com/2011/10/29-1.png">![](http://semihkirdinli.files.wordpress.com/2011/10/29-1.png "29.1")</a>
Sonra raporumuzu göstereceğimiz bir .aspx sayfası oluşturuyorum. Buraya Toolbox’ta yer alan “Reporting” sekmesinden bir **“ReportViewer”** kontrolü sürüklüyorum.
<a href="http://semihkirdinli.files.wordpress.com/2011/10/29-2.png">![](http://semihkirdinli.files.wordpress.com/2011/10/29-2.png "29.2")</a>
Bu kontrolün sağ üst tarafındaki butona  tıklayarak, açılan pencerede*(ReportViewer Tasks)* **“Design a new report”** yazısına tıklıyorum. *Report Wizard* kontrolü açılıyor ve buradan Data source bölümünde önceden oluşturmuş olduğumuz dataset’i seçiyorum. *Next *butonuna tıklıyorum. **“Available fields”** bölümünde, raporumda göstermek istediğim alanlara çift tıklayarak **“Row groups”** bölümüne gelmesini, buradan da **“Values”**  bölümüne hangi sırada istersem ona göre sürükleyerek taşıyorum ve Next butonuna tıklıyorum.
<a href="http://semihkirdinli.files.wordpress.com/2011/10/29-3.png">![](http://semihkirdinli.files.wordpress.com/2011/10/29-3.png "29.3")</a>
Raporun tasarımlarından istediğim seçerek *Finish *butonuna basarak işlemi tamamlıyorum. Ve sonunda tekrardan **.aspx **sayfama geliyorum ve **ReportViewer **kontrolünün sağ üst tarafında bulunan butona tıklayarak(ReportViewer Tasks) **Choose Report** deyip raporumu seçiyorum. ReportViewer kontrolü **Script Manager** gerektiriyor. Bunun için de sayfanın en üstüne bir ScriptManager ekliyorum.
<a href="http://semihkirdinli.files.wordpress.com/2011/10/29-41.png">![](http://semihkirdinli.files.wordpress.com/2011/10/29-41.png "29.4")</a>
Burada önemli olan şey; *ScriptManager *daima üstte olmalıdır. *ScriptManager*’ın üstünde kalan kontroller ScriptManager’ ı göremez. Bu yüzden *ReportViewer*’ın altına değil, üstüne bir *Script *Manager ekiyoruz(*ScriptManager *bir AJAX kontrolü olduğu için **AJAX Control Toolkit**’in daha önceden projeye dahil olması gerekir). Debug ettiğimizde projemizin çalıştığını göreceğiz. Anlatırken uyguladığım için sonuç alabildim.
<a href="http://semihkirdinli.files.wordpress.com/2011/10/29-5.png">![](http://semihkirdinli.files.wordpress.com/2011/10/29-5.png "29.5")</a>
Sizin de benim ekranımdaki gibi bir rapor görmeniz dileğiyle… Hoşçakalın.

**Bu makalede ne yaptık ?**
1.       Dataset oluşturduk.
2.       Veritabanı ekledik.
3.       Dataset içine raporlamak istediğimiz tablolarımızı sürükledik.
4.       ReporViewer ekledik.
5.       “Report Wizard” penceresinden,  Dataset’i ReportView’e bağladık.
6.       .aspx sayfamızdan ReportView kontrolüne tekrar gelerek raporumuzu da bağladık.
7.       ReportViewer’ın üstüne ScriptManager ekledik.
8.       Raporumuzu görüntüledik.
