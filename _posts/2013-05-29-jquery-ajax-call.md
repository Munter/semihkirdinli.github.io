---
layout: post
title: "Jquery ajax call"
date: 2013-05-29 21:36
author: semihkirdinli
comments: true
categories: [jquery]
tags: [ajax, ajax call, javascript, jquery ajax, request]
---
jQuery has an ajax method

{% highlight javascript %}
$.ajax({
　　　　type: "POST",
　　　　url: "some.php",
　　　　data: { name: "John", location: "Boston" }
}).done(function( msg ) {
　　　　alert( "Data Saved: " + msg );
});
{% endhighlight %}

We can define a request function to simulate ajax
{% highlight javascript %}
function request(type, url, opts, callback) {
　　　　var xhr = new XMLHttpRequest();
　　　　if (typeof opts === 'function') {
　　　　　　callback = opts;
　　　　　　opts = null;
　　　　}
　　　　xhr.open(type, url);
　　　　var fd = new FormData();
　　　　if (type === 'POST' && opts) {
　　　　　　for (var key in opts) {
　　　　　　　　fd.append(key, JSON.stringify(opts[key]));
　　　　　　}
　　　　}
　　　　xhr.onload = function () {
　　　　　　callback(JSON.parse(xhr.response));
　　　　};
　　　　xhr.send(opts ? fd : null);
}
{% endhighlight %}

Then we can simulate get and post method based on request method
{% highlight javascript %}
var get = request.bind(this, 'GET');
var post = request.bind(this, 'POST');
{% endhighlight %}
Kaynak: [http://pixelstech.net/article/1368463977_How_to_be_jQuery-free_](http://pixelstech.net/article/1368463977_How_to_be_jQuery-free_)