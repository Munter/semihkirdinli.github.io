---
layout: post
title: "Left Join Kodu Oluşturan Lynq Sorgusu"
date: 2016-02-04 20:47
author: semihkirdinli
comments: true
categories: [.NET Framework, C#]
tags: [c#, entity framework, entityframework, left join, lynq]
---


Entity Framework ile Left Join, sık kullanılan ihtiya&ccedil;lardan birisi. Sade bir left join kodu generate eden bir lynq sorgusu &ouml;rneği:
{% highlight c# %}
using (DataConnection conn = new DataConnection())
{
	var query = (from o in conn.OrderDbSet
        join p in conn.ProductDbSet
        on o.ProductId equals p.ProductId into gj
        from g in gj.DefaultIfEmpty()
        select new OrderDetail()
        {
            Count = o.Count,
            DeliveryPlace = o.DeliveryPlace,
            ProductName = g.ProductName
		});
}
{% endhighlight %}

Kaynak: https://msdn.microsoft.com/en-us/library/bb397895.aspx

