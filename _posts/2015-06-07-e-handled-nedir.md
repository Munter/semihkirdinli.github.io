---
layout: post
title: "&quot;e.Handled&quot; nedir?"
date: 2015-06-07 08:49
author: semihkirdinli
comments: true
categories: [C#]
tags: [.net framework, c#, event, eventargs, eventhandler, eventhandling]
---
Masaüstü uygulamaları geliştiriyorsak ve kontrollere event yazmışsak dikkat etmemiz gereken şeylerden biri de event fonksiyonuna ait parametrelerdir.
{% highlight c# %}
private void StackPanel_PreviewTextInput(object sender, TextCompositionEventArgs e)
{% endhighlight %}
Buradaki TextCompositionEventArgs class'ı sonuç olarak EventArgs class'larından türetilmiş bir sub class'tır. Dolayısıyla base class'larının metot ve değişkenlerini içermektedir. Bu değişkenlerden biri de Handled'tır.
{% highlight c# %}
public bool Handled { get; set; } olarak tanımlanır.
{% endhighlight %}
Handled değişkeni bir olayın gerçekleşip gerçekleşmediğine ait atamayı gösterir. Metodumuzun içinde, "e.Handled = true;" diyerek içinden çıkarsak, yani fonksiyonu return edersek, olay gerçekleşmiş gibi kabul edilir ve tekrar yapılmaz. Örnekle açıklamak gerekirse: klavyeden tuşlara basıyorum, event fonksiyonunun içine "e.Handled = true;" yazarsam olayım gerçekleşmeyecektir. Bu fonksiyonun içine ihtiyacımıza göre farklı kontroller koyarak bazı kısıtlamalar getirebiliriz. Örneğin kullanıcıya Türkçe karakter girdirmek istemiyorsak veya sadece rakam girdirmek istiyorsak, bu şekilde kontrolümüzü geliştirebiliriz.
