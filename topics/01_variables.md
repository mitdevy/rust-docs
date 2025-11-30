# Değişkenler
Değişkenler, dilden dile farklılık gösterse de her programlama dilinde var olan yapılardır. Esasında değişken dediğimiz olgu, veri barındırmaktan ve bunu kullanmaktan başka bir şey yapmaz (neredeyse). Değişkenler; bilgisayar belleğinde yer kaplar, oluşturulabilir, bekletilebilir, kontrol edilebilir, değiştirilebilir, silinebilir veya daha başka bir çok şey yapılabilir.

Esasında temel görevleri bir bilgi barındırmak, bir kontrol mekanizmasını yönetmek, performans optimizasyonuna katkıda bulunmak gibi basit işlemlerdir.

Örnek vermek gerekirse;

Programın 5 ayrı bölümünde ```26``` sayısını kullandığımızı düşünelim. Bu sayıyı daha sonradan değiştirmek gerektiğinde 5 ayrı bölümü teker teker değiştirmem gerekecek. Eğer programda 5 değil de 100 ayrı bölüm olsaydı, bu durumda 100 defa aynı işlemi tekrar yapmak zorunda kalırdım. Bunu engellemek adına ```26``` sayısını, bilgisini, olgusunu veya daha farklı diğer adları her neyse onu, bir değişken içerisinde saklasaydım yalnızca bu değişkenin içeriğini güncelleyerek bu işin üstesinden gelebilirdim.

Daha gerçekçi bir örnek ise şu şekilde verilebilir;

Örneğin gmail veya outlook üzerinde yeni bir hesap açacak olan Ahmet, kullanmak istediği mail adresini ```ahmetcan@outlook.com``` olarak belirliyor. Ahmet siteye başarıyla kayıt olup hesap ayarları sayfasına gittiğinde, kendi belirlemiş olduğu mail adresini görüyor. Bunun sebebi, kayıt esnasında Ahmet'in girdiği mail adresinin bir değişken içerisinde saklanması. Kayıt işlemi başarılı olur ve kullanıcı kaydedilirse, hesap ayarları sayfasına gidildiğinde bu değişken içerisinde bulunan değer (bu örnekte Ahmet'in mail adresi anlamına gelir) gösteriliyor. Böylece gmail veya outlook siteleri, Ahmet'in mail adresini her seferinde tekrar tekrar yazmak yerine işi tek seferde hallediyor. Eğer Ahmet mail adresini değiştirirse, aynı şekilde ilgili değişken içerisindeki değer de değişir. Bu sayede hem performanstan, hem işten, hem de zamandan tasarruf edilmiş oluyor.

İşte değişkenlerin temel olarak amaçları bu: bilgi barındırmak. Bir bilgiyi yazılımda kullanabilmek için onu bir değişkenin içerisinde barındırıyor, böylece lazım olduğunda kullanabiliyoruz, içini açıp bakabiliyoruz, değiştirip silebiliyoruz veya ```şöyleyse şöyle, böyleyse böyle yap``` gibi komutlar verebiliyoruz. Değişken konsepti budur.

---

Değişkenlerin mantığı aynı olsa da her dilde farklı şekilde tezahür ederler. Bu bağlamda Rust'ta da değişkenlerin farklı biçimleri, kuralları ve yönetimleri vardır.

Rust dilinde değişken oluşturmanın 3 farklı yolu vardır, bunlar;
1. ```let``` anahtar kelimesini kullanmak
2. ```const``` anahtar kelimesini kullanmak
3. ```static``` anahtar kelimesini kullanmak

Yukarıdaki 3 farklı yolun, 3'ü de farklı amaçlara hizmet eder ve oldukça önemli farkları vardır.
