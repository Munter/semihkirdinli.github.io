---
layout: post
title: "User Control İçinde Event Delegate Etmek ve Yakalamak"
date: 2015-06-07 11:42
author: semihkirdinli
comments: true
categories: [C#]
tags: [.net, c#, C#4.0, CodeProject, delegate, event, textbox, user control, wpf]
---
WPF üzerinden .net EventHandler yapısına ufak bir örnek vermeye çalıştım.

**UI:**
`&lt;UserControl Name="ucTextBox" Loaded="ucTextBox_Loaded"&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;TextBox Name="txtInput" TextWrapping="Wrap"/&gt;
&lt;/UserControl&gt;`
<div id="highlighter_654976">
<table border="0" width="800">
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
<div>32</div></td>
<td>
<div>
<div>`public partial class Example : Window`</div>
<div>`{`</div>
<div>`      public Example()`</div>
<div>`      {`</div>
<div>`          InitializeComponent();`</div>
<div>`          txtInput.TextChanged += new                                     TextChangedEventHandler(this.Audit_TextChanged);`</div>
<div>`      }`</div>
<div></div>
<div>`     /// Constructor'da delegate edilen txtInput TextChanged        event'ini bu fonksiyon yakalar.`</div>
<div>`     private void Audit_TextChanged(object sender,                  TextChangedEventArgs e)`</div>
<div>`     {`</div>
<div>`          MessageBox.Show("Sadece TextBox kontrolü içinde                 delegate edilmiştir.");`</div>
<div>`     }`</div>
<div></div>
<div>`      /// User Control constructor'da delegate edilir.`</div>
<div>`      private void ucTextBox_Loaded(object sender,                    RoutedEventArgs e)`</div>
<div>`      {`</div>
<div>`           AddHandler(TextBox.TextChangedEvent, new                       RoutedEventHandler(Audit_TextChanged), true);`</div>
<div>`      }`</div>
<div></div>
<div>`      /// User Control içinde delegate edilen eventi bu              fonksiyon yakalar.`</div>
<div>`      private void Audit_TextChanged(object sender,                  RoutedEventArgs e)`</div>
<div>`      {`</div>
<div>`           MessageBox.Show("User Control içinde delegate                   edilmiştir.");`</div>
<div>`      }`</div>
<div>`}`</div>
</div></td>
</tr>
</tbody>
</table>
</div>
