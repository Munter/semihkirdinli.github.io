---
layout: post
title: "&quot;ref&quot; ve &quot;out&quot; Parametre Kullanımı"
date: 2015-04-02 07:38
author: semihkirdinli
comments: true
categories: [C#]
tags: [c#, parameter, ref]
---
**ref** parametresi, bir metoda parametre geçişinde kullanılırsa nesnenin bellekteki adresi üzerinde değişiklik yapar. int, bool gibi tiplerde durum böyle değildir, nesnenin bir kopyası alınarak işlem yapılır, orijinal nesne üzerinde işlem yapılmaz. Kendi yazdığım çok basit bir örnekle açıklamak gerekirse:
{% highlight c# %}
static int a;
static void Main(string[] args)
{
　　a = 5;
　　tempFunction(a);
　　Console.WriteLine("without ref parameter: {0}", a);
　　tempFunction(ref a);
　　Console.WriteLine("with ref parameter: {0}", a);
　　Console.Read();
}

public static void tempFunction(ref int a) { a++; }
public static void tempFunction(int a) { a++; }
{% endhighlight %}

**out** parametresi de ref parametresinin aynısıdır, tek farkı: parametre fonksiyonun içine girdikten sonra bir değer ataması yapılması gerekir. Onun dışında bir farkı yoktur. Yani şu şekilde olacak:
{% highlight c# %}
static int a;
static void Main(string[] args)
{
　　a = 4;
　　tempFunction(a);
　　Console.WriteLine("without out parameter: {0}", a);
　　tempFunction(out a);
　　Console.WriteLine("with out parameter: {0}", a);
　　Console.Read();
}

public static void tempFunction(out int a) { a = 5; a++; }
public static void tempFunction(int a) { a++; }
{% endhighlight %}