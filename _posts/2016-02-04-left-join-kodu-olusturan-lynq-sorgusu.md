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



using (DataConnection conn = new DataConnection())  
{  
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;var query = (from o in conn.OrderDbSet  
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;join p in conn.ProductDbSet  
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;on o.ProductId equals p.ProductId into gj  
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;from g in gj.DefaultIfEmpty()  
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;select new OrderDetail()  
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;{  
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;Count = o.Count,  
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;DeliveryPlace = o.DeliveryPlace,  
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;ProductName = g.ProductName  
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;});  
}



Kaynak: https://msdn.microsoft.com/en-us/library/bb397895.aspx

