---
layout: page
title: "Katkıda Bulunanlar"
date: 2014-05-10 -0800
comments: false
categories: [personal blog]
sharing: false
---

## Katkıda Bulunanlar

Blog sitemi geliştirebilir, gördüğünüz problemleri çözmeme katkıda bulunabilirsiniz. Böyle bir isteğiniz olursa bana bir "pull request" göndermeniz yeterli!

Bloğumda düzenleme yapmak istediğiniz her yazı için, başlığın altında gördüğünüz "edit" linkine tıklamanız sayesinde, tarafıma otomatik olarak "pull request" yollanır.

Veya [bloğumu ziyaret et]({{site.github.repository_url}}) üzerinden eski sistem bir "pull request" gönderebilirsiniz..

<ul>
{% for contributor in site.github.contributors %}
  <li>
    <img src="{{ contributor.avatar_url }}" width="32" height="32" /> <a href="{{ contributor.html_url }}">{{ contributor.login }}</a>
  </li>
{% endfor %}
</ul>
