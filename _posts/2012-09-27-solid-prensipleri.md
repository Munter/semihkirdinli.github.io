---
layout: post
title: "SOLID Prensipleri"
date: 2012-09-27 22:28
author: semihkirdinli
comments: true
categories: [Object Oriented Programming]
tags: [Dependency Inversion Principle, Interface Segregation Principle, Liskov, nesne yönelimli programlama, object oriented programming, open close principle, Single Responsibility Principle, software design, SOLID]
---
<p style="text-align:left;" align="center">Bu yazıda SOLID prensiplerinden bahsedeceğiz. SOLID prensipleri nelerdir? Gerçekten nesne yönelimli programlama nasıl olmalı? Kısıt nedir? Amacımız nesne yönelimli programlama yapmaksa, ismini prensiplerin baş harflerinden alan SOLID’e uymamız gerekir. Bu prensipleri temel aldığımız zaman nesne yönelimli programlama yapıyoruz diyebiliriz.

** 1. Single Responsibility Principle**
** 2. Open/Closed Principle**
** 3. Liskov ‘s Substitution Principle**
** 4. Interface Segregation Principle**
** 5. Dependency Inversion Principle**

**1.Single Responsibility Principle:** Her modülün(sınıf,nesne,metot) tek bir görevi, tek bir sorumluluğu olmalıdır. Bir nesneyi değiştirmek için tek bir neden olmalıdır. Birden fazla neden varsa, o nesnenin birden fazla sorumluluğu var demektir. Burada istenen birden fazla görev/sorumluluk olmamasıdır.

**2.Open/Closed Principle:** Yazdığımız kod(sınıf,nesne,metot) gelişime açık, değişime kapalı olmalıdır. Yeni bir özellik ekleneceği zaman veya geliştirme yapılacağı zaman kodu değiştirmemek, sadece önceden yazılan kodun üstüne bir şeyler eklemek gerekir.

**3.Liskov’s Substitution Principle:** Alt sınıflarıdan oluşturulan nesneler, üst sınıfların nesneleriyle yer değiştirildiklerinde aynı davranışı göstermek zorundadır. Örnekle gösterecek olursak:


public class Rectangle
    {
       public int Width { get; set; }
       public int Height { get; set; }
       public int GetArea()
       {
          return Width * Height;
       }
    }
    
    public class Square : Rectangle
    {
       private int width;
       public int Width
       {
          get { return width; }
          set
          {
             width = value;
             height = value;
          }
       }
    
       private int height;
       public int Height
       {
          get { return height; }
          set
          {
             height = value;
             width = value;
          }
       }
    }
    
    public static class Factory
    {
       public static Rectangle GetRectangle()
       {
          return new Square();
       }
    }
    
    class Program
    {
       static void Main(string[] args)
       {
          Rectangle rect = Factory.GetRectangle();
          rect.Width = 5;
          rect.Height = 10;
          Console.WriteLine(rect.GetArea());
       }
    }

gibi.

**4.Interface Segregation Principle:** Benzer özellikleri barındıran sınıfları tek bir interface’ten türeterek o interface’e sonradan sınıflarda kesin olarak kullanılmayacak özellikler eklemek doğru değildir. Başta çözüm benzer özelliğe sahip sınıfları tek bir interface’ten türetmek gibi görünse de aslında çok da doğru değildir. Çözüm interface’leri oluştururken içindeki üyeleri ortak olacak şekilde parçalayıp bu üyeleri interface’ler altında toplayıp, ayrı interface’ler oluşturmaktır.

**5.Dependency Inversion Principle:** Somut sınıflara olan bağımlılıklar, soyut sınıflar ve interface’ler kullanılarak ortadan kaldırılmalıdır. Çünkü somut sınıflarda değişiklikler çok olur.

Bu prensipleri ne kadar iyi uygularsak nesne yönelimli programlamayı o kadar iyi yapmış oluruz, ancak amaç nesne yönelimli programlama yapmak için bu kuralları uygulamak değil, bu prensiplere bakarak yazılan koddaki eksikleri bulmak ve düzeltmektir.
