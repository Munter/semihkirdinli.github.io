---
layout: post
title: "Module Pattern"
date: 2012-08-31 06:19
author: semihkirdinli
comments: true
categories: [Creational Design Patterns]
tags: [design patterns, design patterns with javacsript, desing pattern, javascript, javascript ile tasarım desenleri, module, module pattern, object literal notasyonu, object literal notation, tasarım desenleri]
---
**Object Literal Notasyonu**
Modüller, büyük bir uygulamada yer alan parçalardır. JavaScript’te nesne tanımlamanın bir kaç yolu vardır.

{% highlight javascript %}
var newObject = {}; //or
    var newObject = Object.create(null); //or
    var newObject = new Object(); //or
{% endhighlight %}
	
Bu tanımlardan biri de örneğin ilk sıradaki tanım olan object literal notasyonudur. Nesne tanımı içinde kalan isimler aralarına virgül konularak birbirinden ayrılır ve son elemandan sonra virgül konulmaz. Object literal’le nesne tanımlamak için new anahtar kelimesini kullanmaya gerek yoktur.
    
Object Literal tanımı aşağıdaki gibidir:
{% highlight javascript %}
var myObjectLiteral = {
    variableKey: variableValue,
    functionKey: function(){
       // ...
    }
};
{% endhighlight %}

Aşağıda object litaral örneğine yer verilmiştir.
{% highlight javascript %}
var myModule = {
    myProperty: 'someValue',
    // object literals can contain properties and methods.
    // here, another object is defined for configuration
    // purposes:
    myConfig: {
        useCaching: true,
        language: 'en'
    },
    // a very basic method
    myMethod: function () {
        console.log('I can haz functionality?');
    },
    // output a value based on current configuration
    myMethod2: function () {
        console.log('Caching is:' + (this.myConfig.useCaching) ? 'enabled' : 'disabled');
    },
    // override the current configuration
    myMethod3: function (newConfig) {
        if (typeof newConfig == 'object') {
            this.myConfig = newConfig;
            console.log(this.myConfig.language);
        }
    }
};

myModule.myMethod(); // I can haz functionality
myModule.myMethod2(); // outputs enabled
myModule.myMethod3({
language: 'fr',
useCaching: false
});
{% endhighlight %}

Buraya kadar olanlar Module Pattern’i daha iyi anlamak için gerekli bilgilerdir.
    
**Module Pattern**
Module pattern gizlilik içerir. Karışık public/private metot ve değişkenlerin paketlenmesini sağlar. Global scope’taki kodların, bir başka geliştirici tarafından yazılan kodlarla çarpışmasını engeller.
    
**Module pattern uygulanışı – Örnek1:**
{% highlight javascript %}
var testModule = (function(){
    var counter = 0;
    return {
        incrementCounter: function(){
            return counter++;
        },
        resetCounter: function(){
            console.log(‘counter value prior to reset:’ + counter);
            counter = 0;
        }
    };
})();

testModule.incrementCounter();
testModule.resetCounter();
{% endhighlight %}
	
Yukarıdaki örnekte incrementCounter() metodu ile counter değişkenin değeri 1 artarak 1 oldu. Ardından resetCounter() metodu çağrıldığında önce counter değeri yazıldı. Burada önceden değeri artırılan counter, değerini içeride(return bloğunda) korudu.
    
**Module pattern uygulanışı – Örnek2:**
{% highlight javascript %}
var someModule = (function () {
    //private attributes
    var privateVar = 5;

    //private methods
    var privateMethod: function () {
        return "Private Test";
    };
	
    return {
        //public attributes
        publicVar: 10,
        //public methods
        publicMethod: function () {
            return "Followed By Public Test";
        },
        getData: function () {
            return privateMethod() + this.publicMethod() + privateVar;
        }
    }
})();

SomeModule.getData();
{% endhighlight %}

Yukarıdaki örnekte tek bir string ifadesi ayrı metotlarda modüler bir şekilde yazılmış ve ardından istenen sırada çağrılarak birleştirilmiştir. Module pattern ile yapılmak istenen de yaratılacak olan nesneyi tek bir metotta değil de, farklı amaçlar doğrultusunda da kullanabilmek için basit ve tek bir iş yapan ayrı metotlarda yazmak ve istenen doğrultuda bu modülleri birleştirerek kullanmaktır.

**Kaynak:** Learning JavaScript Design Patterns – Addy Osmani
