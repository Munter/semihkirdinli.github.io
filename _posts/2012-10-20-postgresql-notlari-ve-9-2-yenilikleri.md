---
layout: post
title: "PostgreSql Notları ve 9.2 Yenilikleri"
date: 2012-10-20 22:36
author: semihkirdinli
comments: true
categories: [PostgreSql, SQL]
tags: [Bgwriter, checkpointer, Fast path locking, Index only scans, JSON, master sunucu, Pg_stat_activity, pg_stat_statements, Postgres, Postgres 9.2, PostgreSql 9.2, PostgreSql 9.2 Features, Range, shared buffers, Space-Partitioned GiST, SP_GIST, Synchronous_commit write, veritabanı, WAL, walwriter, Write-ahead logging]
---
20.10.2012 tarihinde yapılan Özgür Web Günleri etkinliği kapsamındaki PostgreSql semineri eğlenceli geçti, bunun yanında not alma fırsatım da oldu. Yararlı olması dileğiyle...

***PostgreSQL 9.2 ile gelen, yeni özellikler***


*   8.3‘ten sonraki ilk başarım sürümü.
*   **Önceki sürümler: 8CPU** kullanıyor iken,** 9.2 sürümü: 64-80 CPU** kullanabilmektedir.
*   **512k tps(transaction per second) okuma hızı**, **60k tps yazma hızı.**
*   Daha fazla bellek kullanabilme. (Önceden 8gb kullanılabiliyordu.) Bu sayede, özellikle **shared buffers**’ı daha geniş tutabilme.(CPU’ya da bağlı.)
*   **Fast path locking:** Select, SelectForUpdate, Index vb. gibi sorgular içeren, okuma ağırlıklı işlemler varsa, veritabanı kısa yoldan lock almak isteyecek. Bu da performansın artmasını sağlar.
*   **pg_stat_statements:** En çok sorgulanan kayıtları cache’ler. Optimizasyon için idealdir.
*   Toplu copy işleminde başarım artışı var.
*   Daha az **WAL(Write-ahead logging)** kaydı, daha az **lock** gereksinimi, daha az **I/O** = **yüksek performans.**
*   **Index only scans:** Veri, çok az değişiyorsa, veritabanından değil, index’ten getirir.
*   Bir replikasyon sunucusu, başka bir replikasyonun **master sunucusu** olarak gösterilebilir.
*   **Bgwriter, checkpointer** ve **walwriter** artık sadece ihtiyaç duydukları zaman çalışacaklar.
*   **JSON** veri tipi kullanılabiliyor. Şu anda çok özelliği yok, geliştiriliyor. JSON kullanmak için herhangi bir eklentiye ihtiyaç yok.
*   **Pg_stat_activity:** Transaction içinde son çalıştırılan script görüntülenebilir.
*   **Range veri tipi:** Bir kolona başlangıç ve bitiş zamanı yazılabilir, indexlenebilir, partitioning yapılabilir.
*   **Synchronous_commit write:** Önceki sürümlere göre daha hızlı sıralama
*   **SP_GIST(Space-Partitioned GiST):** Coğrafi bilgi sistemleri ile ilgili verilerde kullanılabilecek indexleme altyapısı. (*http://www.pgcon.org/2011/schedule/events/309.en.html*)
**Kaynak: **Devrim Gündüz([gunduz.org](http://gunduz.org))
Özgür Web Günleri([www.ozgurwebgunleri.org.tr/2012/](http://www.ozgurwebgunleri.org.tr/2012/))
