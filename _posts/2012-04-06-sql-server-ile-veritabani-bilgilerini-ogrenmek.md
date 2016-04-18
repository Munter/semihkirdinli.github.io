---
layout: post
title: "Sql Server ile Veritabanı Bilgilerini Öğrenmek"
date: 2012-04-06 12:45
author: semihkirdinli
comments: true
categories: [Sql Server]
tags: [check, constraint, default, foreign key, primary key, sql, sql server, sql server 2008, unique, veritabanı, veritabanı bilgileri öğrenmek]
---
Bu yazıda Sql Server veritabanı yönetim sisteminde kaç tane CHECK Constraint, DEFAULT Constraint, UNIQUE Constraint, FOREIGN KEY Constraint, PRIMARY KEY, kaç adet sistem tablosu, kaç adet kullanıcı tablosu bilgileri alabileceğimiz bir sorguyu paylaşıyorum. Umarım işinize yarar.

```sql
SELECT xtype,CASE(xtype)
	WHEN 'AF' THEN 'Aggregate function (CLR)'
	WHEN 'C' THEN 'CHECK constraint'
	WHEN 'D' THEN 'Default or DEFAULT constraint'
	WHEN 'F' THEN 'FOREIGN KEY constraint'
	WHEN 'L' THEN 'Log'
	WHEN 'FN' THEN 'Scalar function'
	WHEN 'FS' THEN 'Assembly (CLR) scalar-function'
	WHEN 'FT' THEN 'Assembly (CLR) table-valued function'
	WHEN 'IF' THEN 'Inlined table-function'
	WHEN 'IT' THEN 'Internal table'
	WHEN 'P' THEN 'Stored procedure'
	WHEN 'PC' THEN 'Assembly (CLR) stored-procedure'
	WHEN 'PK' THEN 'PRIMARY KEY constraint (type is K)'
	WHEN 'RF' THEN 'Replication filter stored procedure '
	WHEN 'S' THEN 'System table'
	WHEN 'SN' THEN 'Synonym'
	WHEN 'SQ' THEN 'Service queue'
	WHEN 'TA' THEN 'Assembly (CLR) DML trigger'
	WHEN 'TF' THEN 'Table function'
	WHEN 'TR' THEN 'Trigger'
	WHEN 'TT' THEN 'Table type'
	WHEN 'U' THEN 'User table'
	WHEN 'UQ' THEN 'UNIQUE constraint (type is K)'
	WHEN 'V' THEN 'View'
	WHEN 'X' THEN 'Extended stored procedure'
	END Açıklama,
COUNT(*) AS Toplam FROM sys.sysobjects with(NOLOCK)
GROUP BY xtype
```

 İyi çalışmalar.
