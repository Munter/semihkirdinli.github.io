---
layout: post
title: "Sql Server Veritabanında Bulunan Tüm Stored Procedure'leri Silmek"
date: 2012-02-21 14:16
author: semihkirdinli
comments: true
categories: [Sql Server]
tags: [declare, exec, fetch, procedure name, sql, sql server, stored procedure]
---
Sql Server veritabanında bulunan tüm stored procedure'leri silmek için aşağıdaki kodu çalıştırmamız yeterli olacaktır.

```sql
DECLARE @procedureName varchar(500)
DECLARE cur CURSOR
      FOR SELECT [name] FROM sys.objects WHERE type = 'p'
      OPEN cur

      FETCH NEXT FROM cur INTO @procedureName
      WHILE @@fetch_status = 0
      BEGIN
            EXEC('DROP PROCEDURE ' + @procedureName)
            FETCH NEXT FROM cur INTO @procedureName
      END
      CLOSE cur
      DEALLOCATE cur
```