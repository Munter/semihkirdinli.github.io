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

```sql
ALTER TABLE TableName ADD NewColumnName char(30);

ör: ALTER TABLE Kullanici ADD KullaniciAdi char(30);
```