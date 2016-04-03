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



    <span style="color:#0000ff;">DECLARE</span> @procedureName <span style="color:#0000ff;">varchar</span>(500)
    <span style="color:#0000ff;">DECLARE</span> cur <span style="color:#0000ff;">CURSOR</span>
          <span style="color:#0000ff;">FOR</span> <span style="color:#0000ff;">SELECT</span> [name] <span style="color:#0000ff;">FROM</span> sys.objects <span style="color:#0000ff;">WHERE</span> type = <span style="color:#008000;">'p'</span>
          <span style="color:#0000ff;">OPEN</span> cur
    
          <span style="color:#0000ff;">FETCH</span> <span style="color:#0000ff;">NEXT</span> <span style="color:#0000ff;">FROM</span> cur <span style="color:#0000ff;">INTO</span> @procedureName
          <span style="color:#0000ff;">WHILE</span> <span style="color:#ff0000;">@@fetch_status</span> = 0
          <span style="color:#0000ff;">BEGIN</span>
                <span style="color:#0000ff;">EXEC</span>(<span style="color:#008000;">'DROP PROCEDURE '</span> + @procedureName)
                <span style="color:#0000ff;">FETCH</span> <span style="color:#0000ff;">NEXT</span> <span style="color:#0000ff;">FROM</span> cur <span style="color:#0000ff;">INTO</span> @procedureName
          <span style="color:#0000ff;">END</span>
          <span style="color:#0000ff;">CLOSE</span> cur
          <span style="color:#0000ff;">DEALLOCATE</span> cur

