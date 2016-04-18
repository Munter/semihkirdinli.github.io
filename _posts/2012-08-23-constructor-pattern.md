---
layout: post
title: "Constructor Pattern"
date: 2012-08-23 23:15
author: semihkirdinli
comments: true
categories: [Creational Design Patterns]
tags: [constructor, constructor pattern, desing pattern, prototype, tasarım desenleri]
---
Merhabalar, yeni bir aktif blog dönemine girmiş bulunmaktayım. Bu yazıda Tasarım Desenleri'ne kısa bir giriş olması amacıyla Creational(Yaratımsal) Pattern'lerden biri olan Constructor Pattern'den bahsedeceğiz.

**Basit bir constructor örneği:**


function Car(model, year, miles) {
        this.model = model;
        this.year = year;
        this.miles = miles;
        this.toString = function () {
            return this.model + " has done " + this.miles + " miles";
        };
    }
    
    var civic = new Car("Honda Civic", 2009, 20000);
    var mondeo = new Car("Ford Mondeo", 2010, 5000);
    
    console.log(civic.toString());
    console.log(mondeo.toString());</pre>
    **Prototype kullanılarak yapılan bir constructor örneği:**
    <pre class="brush: java">function Car(model, year, miles) {
        this.model = model;
        this.year = year;
        this.miles = miles;
    }
    
    Car.prototype.toString = function () {
        return this.model + " has done " + this.miles + " miles";
    };
    
    var civic = new Car("Honda Civic", 2009, 20000);
    var mondeo = new Car("Ford Mondeo", 2010, 5000);
    
    console.log(civic.toString());

Burada ister normal yöntemde olduğu gibi **this** diyerek, istersek de **Car.prototype** diyerek Car nesnesini çağırabiliriz. **this.toString** metodu Car nesnesinin içerisinden çıkarılmış, ancak **Car.prototype.toString** ile tanımlandığında yine Car'a ait bir metot olarak çağrılabilmiştir. Prototype, adından da anlaşılacağı gibi, büyük bir nesnenin küçük bir parçası olarak düşünülebilir.

**Kaynak:** Learning JavaScript Design Patterns - Addy Osmani
