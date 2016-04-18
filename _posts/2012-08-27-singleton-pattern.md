---
layout: post
title: "Singleton Pattern"
date: 2012-08-27 21:34
author: semihkirdinli
comments: true
categories: [Creational Design Patterns]
tags: [design patterns, design patterns with javacsript, javascript ile tasarım desenleri, nesne yönelimli programlama, singleton, singleton pattern, tasarım desenleri]
---
Singleton Pattern'de amaç; yaratılması pahalı olan nesnelerin tekrar yaratılmasını engellemek, varsa eldeki nesneyi kullandırmaktır. Nesne yoksa yeni bir nesne oluşturulur, varsa elde olan kullanılır. Tek bir nesne olması, class'tan **new** anahtar sözcüğü ile yeni bir nesne oluşturulmasını engeller. Tek bir nesne üzerinde çalışmayı gerektirecek durumlarda **Singleton Pattern** kullanmak avantajlı olacaktır. JavaScript ile singleton pattern kullanımının yaklaşık 10 çeşit örneği bulunmaktadır. En kullanışlı kullanımlardan biri aşağıdaki gibidir:

{% highlight javascript %}
var Singleton = (function () {
    var instantiated;
    function init() {
        // singleton here
        return {
            publicMethod: function () {
                console.log('hello world');
            },
            publicProperty: 'test'
        };
    }
	
    return {
        getInstance: function () {
            if (!instantiated) {
                instantiated = init();
            }
            return instantiated;
        }
    };
})();
{% endhighlight %}

public metod böyle çağrılabilir.
{% highlight javascript %}
Singleton.getInstance().publicMethod();
{% endhighlight %}

ekran çıktısı: hello world

JavaScript ile Singleton pattern kullanımında sınıf syntax'ı aşağıdaki gibi olmalıdır.
{% highlight javascript %}
var Singleton(function(){ 
   /*kodlar buraya yazılacak.*/
})();
{% endhighlight %}

JavaScript'te private sınıf üyeleri(property ve metotlar) tanımlamak için **return** anahtar kelimesi kullanılır. return olmadan bir class içindeki tüm sınıf üyeleri public'tir. return yazıldığı anda return dışında kalan kısımlar dışarıdan erişime kapalı hale gelir, yani private olur. return içinde kalanlar ise public'tir.

{% highlight javascript %}
return{
   /*public metot ve property'ler buraya yazılacak.*/
};
{% endhighlight %}

Yeni bir nesne yaratmayı engellemek için constructor private yapılır. Private yapmak için yapılması gereken ilk iş return yazmak ve private olacak olan sınıf üyesini return'ün dışına yazmaktır. Burada constructor'ı return bloğunun dışına yazmalıyız.

{% highlight javascript %}
var Singleton(function(){ 
   function init() {return{ /* constructor */};}
   return{};
})();
{% endhighlight %}

Nesneyi çağırmak için:
{% highlight javascript %}
Singleton.getInstance().publicMethod();
{% endhighlight %}

dediğimizde, yoksa yeni bir nesne oluşacak, varsa olan nesneyi gelecektir. Bu şekilde, yaratılması pahalı olan nesnelerin tekrar tekrar yaratılması engellenmiş, maliyet azalmış olur.

**Not:** Singleton nesne çağırmak için kullanılan fonksiyon, static fonksiyon çağırmayla aynıdır. **ClassName.getInstance()** şeklinde nesneye ulaşılabilir.

**Kaynak:** Learning JavaScript Design Patterns - Addy Osmani
