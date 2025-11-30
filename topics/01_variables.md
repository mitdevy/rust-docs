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

### ```let```
```let``` ifadesi, Rust'ta değişken oluşturmak için kullanılan en yaygın terimdir. Bir değişken oluşturmak için ```let degisken_adi = deger``` yapısı kullanılır.

Örnek vermek gerekirse;
```rust
let x = 10;
let y = 20;
let z = 30
```

```deger``` yerine yazılan ifade illa sayı olmak zorunda değildir, aşağıdaki tanım da bir değişken oluşturur:

```rust
let input = String::new();
```
Henüz ilgili konuyu işlemedik, ancak yukarıdaki kod ```String``` türünde boş bir değişken oluşturur. Yani bir değişken, yalnızca sayı değil, mantık hatası olmadığı sürece her şeyden değer alabilir.

Rust'ta bir değişken oluşturulduğu zaman, çoğu programlama diline ters olarak, o değişken bir daha değiştirilemez. Yani, aşağıdaki kod blokları JavaScript dilinde oldukça normal olmasına rağmen Rust'ta hataya yol açar.
```javascript
let x = 10;
x = 20;
```
Yukarıdaki kodda bir ```x``` değişkeni oluşturulmuş ve bu değişkene ```10``` sayısı değer olarak verilmiştir, ancak bu kod Rust'ta çalışmaz. Bunun sebebi Rust'ta ```let``` ile tanımlanan her değişkenin, varsayılan olarak immutable (değiştirilemez) olmasıdır. Bu duruma ```mutability of variables``` denir, yani ```değişkenlerin değişkenliği```. Bunun anlamı, Rust'ta tanımladığınız bir değişkenin değerini bir kez verdikten sonra, bir daha onu değiştiremezsiniz demektir.

Bu durumun sebebi şu: kod yazım süreci esnasında değişkenlerin yanlışlıkla, istemeden, deneme amaçlı veya kontrol dışı değiştirilme durumu çok sık yaşanır. Bu durum programda tutarsızlıklara sebep olur ve hesaplamalarda hata çıkartır. 27 satır boyunca yazdığınız kodda ```x``` değişkeninin değeri 10 ise, daha sonra yazdığınız 32 satırlık kodda değişkenin değerini 26 yaparsanız; kodların bir kısmı ```x``` değişkeninin 10, diğer kısmı 26 olduğu duruma göre hareket eder.

Bir diğer nedeni ise data race'leri, yani veri yarışlarını önlemek. Örneğin siz ```x``` değişkenini varsayılan olarak değiştirilebilir konumda oluşturursanız, bu durumda ```xyz.rs``` ve ```klm.rs``` dosyalarındaki bazı kodlar bu değişkeni değiştirmeye çalışabilir. Yani bir değişken, aynı anda 2 kontrolcü tarafından değiştirilmeye zorlanabilir. Buna **data race**, yani veri yarışı adı verilir.

Rust bu durumu engellemek amacıyla bir değişkeni varsayılan olarak immutable, yani değiştirilemez konumda oluşturur. Böylece daha sonradan doğabilecek bir müdahale engellenmiş olur ve kod daha güvenli çalışır.

Peki değişkenleri ```değiştirilebilir``` yapmak mümkün değil mi?

Mümkün. Bunu ```mut``` ifadesi kullanarak yaparız. Biraz önce yukarıda verdiğim hataya sebep olan kod, aşağıdaki gibi güncellenirse hata giderilmiş olur;
```rust
let mut x = 10;
x = 20;
```
Yani bir değişkeni mutable, yani değiştirilebilir yapabilmek için ```let mut degisken_adi = deger``` yapısı kullanılır.

Değişken oluşturma aşamasında aşağıdaki kod parçasında olduğu gibi tekrar düşmek yerine daha etkili bir yöntem vardır:
```rust
let x = 10;
let y = 20;
let z = 30;
```
Yukarıdaki kod aynı yapıyı 3 defa tekrar eder, ancak daha efektif bir yöntem olarak ```sıralı değişken oluşturma``` kullanılabilir. Bu yöntemde ```degisken_adi``` yerine parantez içerisinde sıralı şekilde isimler gönderilir. Aynı şekilde ```deger``` ifadesi yerine, parantez içerisinde sıralı şekilde değerler gönderilir. Örnek:
```rust
let (x, y, z) = (10, 20, 30);
```
Yukarıdaki kodda tek satırda 3 değişken aynı anda oluşmuş ve hepsi sıralı bir şekilde değer almıştır, işten tasarruf etmek için tavsiye edilir. Ancak buradaki önemli nokta; her bir sıraya karşılık gelen değerin, ilgili değişkene aktarılacağıdır. Yani sıralama değişirse, değer aktarma sırası da değişir.
