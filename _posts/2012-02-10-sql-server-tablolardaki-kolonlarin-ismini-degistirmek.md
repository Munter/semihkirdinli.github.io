---
layout: post
title: "Sql Server Veritabanında Kayıtlara Zarar Vermeden Tablolardaki Kolonların İsimlerini Değiştirmek"
date: 2012-02-10 20:33
author: semihkirdinli
comments: true
categories: [Sql Server]
tags: [exec, sp_rename, sql server, stored procedure, tablo, veritabanı]
---


Sql Server veritabanında, verilere zarar gelmeden sadece kolonların adını değiştirmek istiyorsanız şu sorguyu çalıştırmak yeterli olacaktır.

```sql
EXEC sp_rename 'TableName.[OldColumnName]', NewColumnName, 'COLUMN' ;

ör: EXEC sp_rename 'Kullanici.[KllncAdi]', KullaniciAdi, 'COLUMN' ;
```

    


