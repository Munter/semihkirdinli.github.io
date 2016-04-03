---
layout: post
title: "&quot;for&quot; mu &quot;foreach&quot; mi Daha Hızlı?"
date: 2015-04-07 08:28
author: semihkirdinli
comments: true
categories: [C#, Genel]
tags: [c#, for, foreach, performance]
---
Yazmış olduğum küçük bir kod parçacığıyla bir döngü içinde dönerek "for"un mu yoksa "foreach"in mi daha performanslı çalıştığını göstermeye çalıştım. Kod her çalıştığında farklı sonuçlar ürettiği için ekran çıktısını bu yazıya dahil etmedim. Kodu çalıştırdığımızda, for döngüsünün foreach'e göre daha hızlı olduğunu söyleyebiliriz.

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
<div>18</div>
<div>19</div>
<div>20</div>
<div>21</div>
<div>22</div>
<div>23</div>
<div>24</div>
<div>25</div>
<div>26</div>
<div>27</div>
<div>28</div>
<div>29</div>
<div>30</div>
<div>31</div>
</td>
<td>
<div>
<div>`static long[] longArray = new long[99999999];`</div>
<div>`static long total = 0;`</div>
<div>``</div>
<div>`static void Main(string[] args)`</div>
<div>`{`</div>
<div>`     var watch = new Stopwatch();`</div>
<div>`     watch.Start();`</div>
<div>`     CallForEach();`</div>
<div>`     watch.Stop();`</div>
<div>`      var elapsedMs1 = watch.ElapsedMilliseconds;`</div>
<div>`      Console.WriteLine("Foreach Elapsed Ms: " + elapsedMs1);`</div>
<div>`      watch.Restart();`</div>
<div>`      CallFor();`</div>
<div>`      watch.Stop();`</div>
<div>`      var elapsedMs2 = watch.ElapsedMilliseconds;`</div>
<div>`      Console.WriteLine("For Elapsed Ms: " + elapsedMs2);`</div>
<div>`      Console.ReadLine();`</div>
<div>`}`</div>
<div>``</div>
<div>`public static void CallFor()`</div>
<div>`{`</div>
<div>`      for (int i = 0; i &lt; longArray.Length; i++)`</div>
<div>`      {`</div>
<div>`           total += longArray[i];`</div>
<div>`      }`</div>
<div>`}`</div>
<div>``</div>
</div>
<div>`public static void CallForEach()`</div>
<div>`{`</div>
<div>`      foreach (int i in longArray)`</div>
<div>`      {`</div>
<div>`           total += i;`</div>
<div>`      }`</div>
<div>`}`</div></td>
</tr>
</tbody>
</table>
</div>
