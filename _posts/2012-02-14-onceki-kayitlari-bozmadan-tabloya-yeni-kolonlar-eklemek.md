---
layout: post
title: "Sql Server Veritabanında Önceki Kayıtları Bozmadan Tabloya Yeni Kolonlar Eklemek"
date: 2012-02-14 21:44
author: semihkirdinli
comments: true
categories: [Sql Server]
tags: [alter, char, kullanici, kullaniciAdi, newcolumnname, query, sorgu, sql, sql server, table, tablename]
---
Sql Server veritabanında önceki kayıtları bozmadan tabloya sadece yeni bir kolon eklemek istersek yazacağımız sql sorgusu şöyle olmalıdır:



<span style="color:#0000ff;">ALTER TABLE</span> TableName <span style="color:#0000ff;">ADD</span> NewColumnName <span style="color:#0000ff;">char</span>(30);
    
    <span style="color:#ff0000;">ör:</span> <span style="color:#0000ff;">ALTER TABLE</span> Kullanici <span style="color:#0000ff;">ADD</span> KullaniciAdi <span style="color:#0000ff;">char</span>(30);

