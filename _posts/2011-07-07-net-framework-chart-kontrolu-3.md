---
layout: post
title: ".NET Framework Chart Kontrolü"
date: 2011-07-07 18:05
author: semihkirdinli
comments: true
categories: [.NET Framework, ASP.NET]
tags: [.net framework, asp.net, chart, chart area, chart kontrolü, chartarea, data mining, DataRow, dataset, DataTable, Series, visual studio 2010]
---
![](/images/jekyll/30.png "30")

Bu makalemde sizlere ASP.NET ile *Toolbox’*ın Data alanına gelen, raporları veya bir yerde tuttuğumuz verileri grafiksel gösterim metoduyla önümüze sunan Chart kontrolünden bahsedeceğim. Ardından örnek bir uygulama paylaşacağım. Chart kontrolü Visual Studio’da önceden *toolbox* alanında olmayan bir kontroldü. Bu yüzden User Control haline getirilmiş örnekleri projeye dahil etme yöntemiyle kullanım şekli vardı. *.NET Framework 4.0*’da ise bu kontrol bize *Toolbox’*ta verilmiş olup, bir çok özelliği içinde barındırmaktadır. Bir örnek üzerinden giderek konunun daha iyi anlaşılacağını düşünüyorum.

Chart aracının önemli bir özelliği DataSource’unu verebilmemiz. Örneğimizde veritabanı tabloları mantığıyla aynı olan DataTable sınıfı üzerinden tablolar oluşturup, içerisine elle kayıtlar(DataRow) ekleyeceğiz. Bunu yapabildikten sonra istediğimiz DataTable’ı, bu kontrole datasource olarak verebilmemiz mümkündür.

**File --&gt; New --&gt; Web Site --&gt; ASP.NET Empty Web Site** diyerek başlıyoruz. Ardından sitemize hemen bir **Default.aspx** sayfası ekleyelim. Toolbox’ın **Data** bölümünden Chart kontrolünü sayfamıza sürükleyelim.

![](/images/jekyll/30-2.png "30.2")

Burada Series bölümü tanımlayacağımız nitelik sayısını belirler. Örneğin günlük kayıt sayısını tutmak için bir series, tıklanma sayısını tutmak için bir series tanımlayabiliriz.  ChartAreas bölümünde ise grafiğimize özellikler verebiliriz. Buna örnek olarak ise 3D görünüm, grafiği döndürme, aralıkları belirleme gibi özellikleri mevcuttur. Series,ChartAreas gibi etiketleri arasına Legends tanımlayarak burada da grafikteki renklerin neyi ifade ettiğini kolaylıkla ekranda gösterebiliriz. Ayrıca bu Chart kontrolünün grafiğini istediğimiz gibi ayarlayabileceğimiz seçenkler mevcut. etiketinin içinde **ChartType="Line" **gibi seçenekler mevcut. Bunu dizayn bölümünden gelerek de yapabilriz.

Şimdi gelelim **Default.aspx.cs** dosyamıza **Datatable** **döndüren** fonksiyonumuzu yazmaya.

public DataTable GunlereGoreGirisDagilimi()
{
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DataTable dt = new DataTable();
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;dt.Columns.Add(new DataColumn("Id", typeof(int)));
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;dt.Columns.Add(new DataColumn("Gun", typeof(string)));
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;dt.Columns.Add(new DataColumn("Sayi", typeof(int)));

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DataRow dr1 = dt.NewRow();
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;dr1["Id"] = 1;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;dr1["Gun"] = "Pazartesi";
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;dr1["Sayi"] = 10;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;dt.Rows.Add(dr1);

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DataRow dr2 = dt.NewRow();
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;dr2["Id"] = 2;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;dr2["Gun"] = "Salı";
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;dr2["Sayi"] = 20;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;dt.Rows.Add(dr2);

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DataRow dr3 = dt.NewRow();
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;dr3["Id"] = 3;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;dr3["Gun"] = "Çarşamba";
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;dr3["Sayi"] = 20;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;dt.Rows.Add(dr3);

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DataRow dr4 = dt.NewRow();
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;dr4["Id"] = 4;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;dr4["Gun"] = "Perşembe";
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;dr4["Sayi"] = 15;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;dt.Rows.Add(dr4);

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DataRow dr5 = dt.NewRow();
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;dr5["Id"] = 5;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;dr5["Gun"] = "Cuma";
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;dr5["Sayi"] = 25;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;dt.Rows.Add(dr5);

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DataRow dr6 = dt.NewRow();
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;dr6["Id"] = 6;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;dr6["Gun"] = "Cumartesi";
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;dr6["Sayi"] = 18;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;dt.Rows.Add(dr6);

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DataRow dr7 = dt.NewRow();
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;dr7["Id"] = 7;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;dr7["Gun"] = "Pazar";
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;dr7["Sayi"] = 16;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;dt.Rows.Add(dr7);

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Chart1.Series["Series1"].XValueMember = Convert.ToString(dt.Columns["Gun "]);
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Chart1.Series["Series1"].YValueMembers = Convert.ToString(dt.Columns[["Sayi"]);

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Chart1.DataSource = dt;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Chart1.DataBind();
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Chart1.Visible = true;

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;return dt;
}

Ardından bu fonksiyonu **Default.aspx.cs**’nin **Page_Load()**’ında çağıralım.

protected void Page_Load(object sender, EventArgs e)
{
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;if (!Page.IsPostBack)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;this.Title = "CHART SAMPLE with DATATABLE";
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;GunlereGoreGirisDagilimi();
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}
}

Projeyi debug ettiğimizde alacağımız görüntü şekildeki gibidir.

<a href="/images/jekyll/30-1.png">![](/images/jekyll/30-1.png "30.1")</a>

**Bu makalede ne yaptık ?**


1.  Chart kontrolünü .aspx sayfamıza sürükledik.
2.  DataTable ve DataRow’ları elle girdirdik.
3.  Chart1 nesnesinin Series’lerinde **XvalueMember** ve **YvalueMembers** özelliklerini **Gun** ve **Sayi** olarak verdik. Çünkü isteğimiz günlük tıklanma sayısına bakmak. Burada önemli olan **YvalueMembers** değerleri karşılaştırma yapmak içindir. Bu değerlere göre karşılaştırma yaparak istatistiği grafik olarak önümüze sunmaktadır. **XvalueMember** ise yatay eksende göstereceğimiz isimlerden ibarettir. Karşılaştırma için kullanılmaz.
4.  Yukarudaki bilgileri içeren datatable döndüren fonksiyonu(GunlereGoreGirisDagilimi adında) yazdık.
5.  Page_Load()’ta “**GunlereGoreGirisDagilimi**” fonksiyonunu çağırdık.
6.  Grafiği görüntüledik.
Chart kontrolü hakkında aktaracaklarım şimdilik bu kadar. İyi çalışmalar.
