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
<div>
<div id="highlighter_196809">
<table border="0" cellspacing="0" cellpadding="0">
<tbody>
<tr>
<td>
<div>1</div>
<div>2</div>
<div>3</div>
<div>4</div>
<div>5</div>
<div>6</div>
<div>7</div></td>
<td>
<div>
<div>`$.ajax({`</div>
<div>`　　　　type: ``"POST"``,`</div>
<div>`　　　　url: ``"some.php"``,`</div>
<div>`　　　　data: { name: ``"John"``, location: ``"Boston"` `}`</div>
<div>`}).done(``function``( msg ) {`</div>
<div>`　　　　alert( ``"Data Saved: "` `+ msg );`</div>
<div>`});`</div>
</div></td>
</tr>
</tbody>
</table>
</div>
</div>
We can define a request function to simulate ajax
<div>
<div id="highlighter_654976">
<table border="0" cellspacing="0" cellpadding="0">
<tbody>
<tr>
<td>
<div>1</div>
<div>2</div>
<div>3</div>
<div>4</div>
<div>5</div>
<div>6</div>
<div>7</div>
<div>8</div>
<div>9</div>
<div>10</div>
<div>11</div>
<div>12</div>
<div>13</div>
<div>14</div>
<div>15</div>
<div>16</div>
<div>17</div>
<div>18</div></td>
<td>
<div>
<div>`function` `request(type, url, opts, callback) {`</div>
<div>`　　　　``var` `xhr = ``new` `XMLHttpRequest();`</div>
<div>`　　　　``if` `(``typeof` `opts === ``'function'``) {`</div>
<div>`　　　　　　callback = opts;`</div>
<div>`　　　　　　opts = ``null``;`</div>
<div>`　　　　}`</div>
<div>`　　　　xhr.open(type, url);`</div>
<div>`　　　　``var` `fd = ``new` `FormData();`</div>
<div>`　　　　``if` `(type === ``'POST'` `&amp;&amp; opts) {`</div>
<div>`　　　　　　``for` `(``var` `key ``in` `opts) {`</div>
<div>`　　　　　　　　fd.append(key, JSON.stringify(opts[key]));`</div>
<div>`　　　　　　}`</div>
<div>`　　　　}`</div>
<div>`　　　　xhr.onload = ``function` `() {`</div>
<div>`　　　　　　callback(JSON.parse(xhr.response));`</div>
<div>`　　　　};`</div>
<div>`　　　　xhr.send(opts ? fd : ``null``);`</div>
<div>`}`</div>
</div></td>
</tr>
</tbody>
</table>
</div>
</div>
Then we can simulate get and post method based on request method
<div>
<div id="highlighter_720220">
<table border="0" cellspacing="0" cellpadding="0">
<tbody>
<tr>
<td>
<div>1</div>
<div>2</div></td>
<td>
<div>
<div>`var` `get = request.bind(``this``, ``'GET'``);`</div>
<div>`var` `post = request.bind(``this``, ``'POST'``);`</div>
</div></td>
</tr>
</tbody>
</table>
Kaynak: [http://pixelstech.net/article/1368463977_How_to_be_jQuery-free_](http://pixelstech.net/article/1368463977_How_to_be_jQuery-free_)

&nbsp;

</div>
</div>
