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




    
    <span style="color:#0000ff;">EXEC</span> <span style="color:#800000;">sp_rename</span> <span style="color:#ff0000;">'TableName.[OldColumnName]'</span>, NewColumnName, <span style="color:#ff0000;">'COLUMN'</span> ;
    
    
    
    <span style="color:#ff0000;">ör:</span> <span style="color:#0000ff;">EXEC </span>sp_rename <span style="color:#ff0000;">'Kullanici.[KllncAdi]'</span>, KullaniciAdi, <span style="color:#ff0000;">'COLUMN'</span> ;
    


