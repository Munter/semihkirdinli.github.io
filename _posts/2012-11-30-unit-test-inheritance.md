---
layout: post
title: "Unit Test Inheritance"
date: 2012-11-30 00:18
author: semihkirdinli
comments: true
categories: [Unit Testing]
tags: [database, object oriented programming, software unit test, test, test class, test initialize, test method, unit test, unit test framework, unit test inheritance]
---
Günümüzde yazılım geliştirmenin temel unsurlarından biri haline gelen testler, yazılan kodun kalitesini ölçmede önemli rol oynamaktadır. Çok sayıda test yöntemi vardır. Bu test yöntemlerinin yazılım geliştiricileri ilgilendiren tarafı Unit Test’lerdir. Öncelikle şunu belirtmekte fayda var. Unit test kodunu testçi değil, yazılım geliştrici yazar. Çünkü projelerde kullanılan fonksiyonaliteyi bilmek, o kodu anlamak ve kullanmak yazılım geliştiricinin görevidir.

Bu yazıda Unit testler ile ilgili okunaklı ve bakımı kolay kod nasıl yazılır, onu inceleyeceğiz. Yazılan testlerin gitgide kod tekrarına sebep olması, bakımının zorlaşmasını istemiyorsak Unit Test’lere de normal kod yazarken gösterdiğimiz özeni göstermeliyiz. Bir yazılımı geliştirirken nasıl Nesne Yönelimli Programlama’ya uymaya çalışıyorsak aynı şekilde Unit Test’leri de bu şekilde tasarlamamız gerekmektedir.

C# kullanarak yazdığımız kısa bir örnekle yazımızı tamamlayalım:

Örnek projenin, birden fazla database bağlantısını destekleyen bir proje olduğunu düşünelim.

Connection string’lerin doğruluğunu test edelim. Örnekte, Solution’da 2 adet proje yer alıyor. Birisi, projemiz olan class library, diğeri ise Unit Test’leri çalıştıracağımız test projesi.

Uygulamanın class library’sinde bulunan class’lar:


    public abstract class Database
        {
            public abstract string GetConnectionString();
        }
    
        public class SqlServer : Database
        {
            public override string GetConnectionString()
            {
                return @"Data Source=myServerAddress;Initial Catalog=myDataBase;Integrated Security=SSPI;User ID=myDomain\myUsername;Password=myPassword;";
            }
        }
    
        public class PostgreSql : Database
        {
            public override string GetConnectionString()
            {
                return @"Server=127.0.0.1;Port=5432;Database=myDataBase;User Id=myUsername;Password=myPassword;CommandTimeout=20;";
            }
        }
    
        public class Oracle : Database
        {
            public override string GetConnectionString()
            {
                return @"Data Source=(DESCRIPTION=(ADDRESS_LIST=(ADDRESS=(PROTOCOL=TCP)(HOST=MyHost)(PORT=MyPort)))(CONNECT_DATA=(SERVER=DEDICATED)(SERVICE_NAME=MyOracleSID)));User Id=myUsername;Password=myPassword;";
            }
        }</pre>
    
    Bu class’ları normal projemizin class’ları olarak düşünebiliriz.
    
    Test projesinde Test edilecek class’ların başına [TestClass], metotların başına [TestMethod] ve her testten önce çalışmasını istediğimiz metodun başına [TestInitialize] yazılması gerekir. 
    Uyuglamanın ileride büyüyüp 3 database’den fazlasını destekleyebileceği durumunu düşünürsek, bu durumda testleri türeteceğimiz bir base class(DatabaseTestBase) olmalı.
    
    <pre>
        public class DatabaseTestBase
        {
            protected Database _database;
            protected string _expectedConnectionString = string.Empty;
    
            [TestMethod]
            public void GetConnectionStringAssertValue()
            {
                string expectedValue = _expectedConnectionString;
                string currentValue = _database.GetConnectionString();
    
                Assert.AreEqual(expectedValue, currentValue);
            }
        }
    </pre>
    
    Bu class database’den bağımsız bir şekilde connection string’i test edebilmektedir. Ancak bu class’ı kullanabilmek için türetmemiz gerekir. Bu yüzden SqlServer’a ve Oracle’a  beklentimiz olan connection string değerini set ediyoruz ve ardından yeni bir örneğini türetiyoruz. Yeni bir database geldiğinde yine aynı şekilde beklediğimiz connection string değerini set etmek ve yeni bir örneğini türetmek copy-paste, quick replace hızımıza kalmış. :)
    
    <pre>
        [TestClass]
        public class SqlServerDatabaseTest: DatabaseTestBase
        {
            [TestInitialize]
            public void Setup()
            {
                _expectedConnectionString = @"Data Source=myServerAddress;Initial Catalog=myDataBase;Integrated Security=SSPI;User ID=myDomain\myUsername;Password=myPassword;";
                _database = new SqlServer();
            }
        }
    
        [TestClass]
        public class OracleDatabaseTest: DatabaseTestBase
        {
            [TestInitialize]
            public void Setup()
            {
                _expectedConnectionString = @"Data Source=(DESCRIPTION=(ADDRESS_LIST=(ADDRESS=(PROTOCOL=TCP)(HOST=MyHost)(PORT=MyPort)))(CONNECT_DATA=(SERVER=DEDICATED)(SERVICE_NAME=MyOracleSID)));User Id=myUsername;Password=myPassword;";
                _database = new Oracle();
            }
        }
    


Bir dahaki yazıda görüşmek üzere. Hoşçakalın.

Kaynak: http://www.coderecycling.net/
