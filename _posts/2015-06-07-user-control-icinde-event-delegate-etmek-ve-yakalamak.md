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
{% highlight c# %}
<UserControl Name="ucTextBox" Loaded="ucTextBox_Loaded">
     <TextBox Name="txtInput" TextWrapping="Wrap"/>
</UserControl>
{% endhighlight %}
**Backend:**
{% highlight c# %}
public partial class Example : Window
{
     public Example()
     {
          InitializeComponent();
          txtInput.TextChanged += new                                     TextChangedEventHandler(this.Audit_TextChanged);
     }
     /// Constructor'da delegate edilen txtInput TextChanged        event'ini bu fonksiyon yakalar.
     private void Audit_TextChanged(object sender,                  TextChangedEventArgs e)
     {
          MessageBox.Show("Sadece TextBox kontrolü içinde                 delegate edilmiştir.");
     }
     /// User Control constructor'da delegate edilir.
     private void ucTextBox_Loaded(object sender,                    RoutedEventArgs e)
     {
          AddHandler(TextBox.TextChangedEvent, new                       RoutedEventHandler(Audit_TextChanged), true);
     }
     /// User Control içinde delegate edilen eventi bu              fonksiyon yakalar.
     private void Audit_TextChanged(object sender,                  RoutedEventArgs e)
     {
          MessageBox.Show("User Control içinde delegate                   edilmiştir.");
     }
}
{% endhighlight %}