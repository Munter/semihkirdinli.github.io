---
layout: post
title: "&quot;ref&quot; ve &quot;out&quot; Parametre Kullanımı"
date: 2015-04-02 07:38
author: semihkirdinli
comments: true
categories: [C#]
tags: [c#, parameter, ref]
---
**ref** parametresi, bir metoda parametre geçişinde kullanılırsa nesnenin bellekteki adresi üzerinde değişiklik yapar. int, bool gibi tiplerde durum böyle değildir, nesnenin bir kopyası alınarak işlem yapılır, orijinal nesne üzerinde işlem yapılmaz. Kendi yazdığım çok basit bir örnekle açıklamak gerekirse:

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
</td>
<td>
<div>
<div>`static int a;`</div>
<div>`static void Main(string[] args)`</div>
<div>`{`</div>
<div>`　　a = 5;`</div>
<div>`　　tempFunction(a);`</div>
<div>`　　Console.WriteLine("without ref parameter: {0}", a);`</div>
<div>` `</div>
<div>`　　tempFunction(ref a);`</div>
<div>`　　Console.WriteLine("with ref parameter: {0}", a);`</div>
<div>`　　Console.Read();`</div>
<div>`}`</div>
<div>`  
`</div>
<div>`public static void tempFunction(ref int a) { a++; }`</div>
<div>`public static void tempFunction(int a) { a++; }`</div>
</div></td>
</tr>
</tbody>
</table>
</div>

**out** parametresi de ref parametresinin aynısıdır, tek farkı: parametre fonksiyonun içine girdikten sonra bir değer ataması yapılması gerekir. Onun dışında bir farkı yoktur. Yani şu şekilde olacak:

<div id="highlighter_654977">
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
</td>
<td>
<div>
<div>`static int a;`</div>
<div>`static void Main(string[] args)`</div>
<div>`{`</div>
<div>`　　a = 4;`</div>
<div>`　　tempFunction(a);`</div>
<div>`　　Console.WriteLine("without out parameter: {0}", a);`</div>
<div>` `</div>
<div>`　　tempFunction(out a);`</div>
<div>`　　Console.WriteLine("with out parameter: {0}", a);`</div>
<div>`　　Console.Read();`</div>
<div>`}`</div>
<div>`  
`</div>
<div>`public static void tempFunction(out int a) { a = 5; a++; }`</div>
<div>`public static void tempFunction(int a) { a++; }`</div>
</div></td>
</tr>
</tbody>
</table>
</div>
