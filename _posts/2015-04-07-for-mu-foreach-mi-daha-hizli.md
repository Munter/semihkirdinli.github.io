---
layout: post
title: "&quot;for&quot; &quot;foreach&quot; Performans?"
date: 2015-04-07 08:28
author: semihkirdinli
comments: true
categories: [C#, Genel]
tags: [c#, for, foreach, performance]
---
Yazmış olduğum küçük bir kod parçacığıyla bir döngü içinde dönerek "for"un mu yoksa "foreach"in mi daha performanslı çalıştığını göstermeye çalıştım. Kod her çalıştığında farklı sonuçlar ürettiği için ekran çıktısını bu yazıya dahil etmedim. Kodu çalıştırdığımızda, for döngüsü foreach'e göre daha hızlı sonuçlar verdi.

{% highlight c# %}
static long[] longArray = new long[99999999];
static long total = 0;
static void Main(string[] args)
{
     var watch = new Stopwatch();
     watch.Start();
     CallForEach();
     watch.Stop();
     var elapsedMs1 = watch.ElapsedMilliseconds;
     Console.WriteLine("Foreach Elapsed Ms: " + elapsedMs1);
     watch.Restart();
     CallFor();
     watch.Stop();
     var elapsedMs2 = watch.ElapsedMilliseconds;
     Console.WriteLine("For Elapsed Ms: " + elapsedMs2);
     Console.ReadLine();
}
public static void CallFor()
{
     for (int i = 0; i < longArray.Length; i++)
     {
          total += longArray[i];
     }
}
public static void CallForEach()
{
     foreach (int i in longArray)
     {
          total += i;
     }
}
{% endhighlight %}