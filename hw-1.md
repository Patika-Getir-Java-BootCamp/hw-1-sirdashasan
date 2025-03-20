## 1) Why we need to use OOP ? Some major OOP languages ?
OOP, Java'nın en çok kullanılan paradigmasıdır. Gerçek dünyadaki nesneleri modelleyerek kod yazmamıza imkan verir. OOP kullanmamızın temel nedeni kodun daha düzenli, tekrar kullanılabilir ve yönetilebilir olmasını sağlamaktır. OOP'nin 4 temel özelliği vardır:
**Encapsulation:** Veriye doğrudan erişimi sınırlandırarak güvenliği artırır ve kontrollü erişim sağlar.
**Abstraction:** Gereksiz detayları gizleyerek yalnızca nesnenin temel özelliklerine odaklanmamızı sağlar.
**Inheritance:** Bir sınıfın başka bir sınıftan özellikleri miras almasını mümkün kılar, kod tekrarını azaltır.
**Polymorphism:** Alt sınıfların, üst sınıftan gelen metotları kendilerine özgü şekilde kullanmalarını sağlar.
**Bazı popüler OOP dilleri:** Java, C++, Python, Ruby, TypeScript, Swift

## 2) Interface vs Abstract class ?
Interface ve Abstract Class, ikisi de soyutlama yapmak için kullanılır ama amaçları farklıdır. 
**Interface:** Bir sınıfın hangi davranışlara sahip olması gerektiğini belirler. İçinde sadece method signature bulunur. Metotların body'si yoktur. Uyguladığımız sınıflarda metotları kendimiz tamamlarız. Bir sınıf birden fazla interface implement edebilir. 
**Abstract Class:** Hem abstract hem concrete metotları içerebilir. Bazı metotları direkt tanımlarken bazılarını alt sınıfta tamamlayabiliriz. Özellikle alt sınıflara miras gelen özellikler sayesinde kod tekrarını azaltır. Bir sınıf sadece bir tane abstract sınıfı extend edebilir. 
Eğer bir sınıfa sadece belirli bir davranış kazandırmak istiyorsak interface kullanırız. Örneğin hayvanlara ses çıkarma yeteneği vereceksek ve her hayvanın farklı sesi olacaksa bunu interface ile tanımlarız. Tüm hayvanların ortak özellikleri yaş, tür, cins gibi olacak ve metotları miras almak gerekiyorsa abstract class kullanırız. Böylece her hayvan için bu ortak özellikleri tekrar yazmamış oluruz. 
-Hem interface'ten hem de abstract class'tan doğrudan bir nesne oluşturulamaz. (instantiate edilemez)

## 3) Why we need equals and hashcode ? When to override ?
**equals metodu:** İki nesnenin içerik olarak aynı olup olmadığını kontrol eder. Eğer override edilmezse Java varsayılan olarak heap memory’de nesnelerin bellek adreslerini karşılaştırır (== operatörü gibi çalışır). Yani içerikleri aynı olsa bile farklı adreslerde oldukları için eşit kabul edilmezler.
**hashCode metodu:** Nesneye özel bir sayısal değer üretir. HashMap, HashSet gibi hash tabanlı koleksiyonlarda nesneleri verimli bir şekilde saklamak ve hızlı erişim sağlamak için kullanılır. Eğer hashCode() düzgün override edilmezse aynı değerlere sahip nesneler farklı hash kodları alabilir ve koleksiyonlarda tutarsız sonuçlar ortaya çıkabilir.
Eğer nesneleri içeriklerine göre karşılaştırmak istiyorsak equals ve hashCode metodlarını birlikte override etmeliyiz. Sadece equals() metodunu override edip hashCode() metodunu olduğu gibi bırakırsak, HashSet ve HashMap gibi veri yapılarında beklenmedik davranışlar olabilir. 

## 4) Diamond problem in Java ? How to fix it?
Eğer bir sınıf birden fazla sınıftan veya interface’ten miras alır ve üst sınıfların içinde aynı isimde bir metot varsa hangi metodun çağrılacağı konusunda bir belirsizlik oluşur. İşte bu duruma Diamond Problem denir. Java'da sınıflar arasında çoklu kalıtım desteklenmediği için bu sorun yaşanmaz ama interface'lerde bir sınıf birden fazla interface’i implement ettiğinde ve bu interface’ler aynı metodu tanımladığında, çakışma olabilir.
-Eğer iki interface aynı metodu tanımlıyorsa, bu metodu override ederek sorunu çözebiliriz.
-Belirli bir interface’in metodunu çağırmak için `InterfaceName.super.methodName();` kullanabiliriz.

## 5) Why we need Garbage Collector ? How does it run ?
Java'da nesneler Heap Memory'de tutulur. Eğer bir nesne artık kullanılmıyorsa yani ona ulaşan bir referans kalmamışsa Garbage Collector bunu algılar ve bellekten otomatik olarak temizler. Kullanılmayan nesneler sürekli bellekte tutulursa bellek sızıntısı oluşabilir ve bu da sistemin performansını olumsuz etkileyebilir. Garbage Collector bu tür sorunları önleyerek bellek yönetimini daha verimli hale getirir. 

## 6) Java ‘static’ keyword usage ?
**Static değişkenler:** Sınıfa aittir tüm nesneler tarafından paylaşılır.
**Static metotlar:** Nesne oluşturmadan doğrudan sınıf üzerinden çağrılabilir.
**Static bloklar:** Sınıf yüklenirken yalnızca bir kez çalışır.
**Static iç sınıflar:** Dış sınıfın nesnesine gerek olmadan kullanılabilir.

## 7) Immutability means ? Where, How and Why to use it ?
Immutability, bir nesnenin oluşturulduktan sonra değiştirilememesidir. Yani içindeki veriler güncellenemez veya değiştirilemez. Verilerin sabit kalmasını istediğimiz durumlarda kullanılır ve özellikle thread safety, hata önleme ve güvenli kod yazımı açısından avantaj sağlar.
Bir sınıfı immutable yapmak için:
-Sınıfı final yaparak miras alınmasını engelleyebiliriz.
-Tüm değişkenleri private ve final olarak tanımlayabiliriz.
-Setter metodlarını tanımlamayarak dışarıdan değişiklik yapılmasını önleyebiliriz.

## 8) Composition and Aggregation means and differences ?
Java’da Composition ve Aggregation, "Has-A" ilişkisini ifade eder, yani bir sınıfın başka bir sınıfı içermesi durumudur.
**Composition:** İki nesne arasında güçlü bir bağlılık vardır. Üst sınıf silindiğinde, alt sınıf da otomatik olarak yok olur. Yani bağımlı nesne tek başına var olamaz. Bir araba ve motoru arasındaki ilişkiyi örnek verebiliriz.
**Aggregation:** İki nesne arasında daha gevşek bir ilişki vardır. Üst sınıf silinse bile alt sınıf varlığını sürdürebilir. Bir kişi ve adresi arasındaki ilişkiyi örnek verebiliriz.

## 9) Cohesion and Coupling means and differences ?
**Cohesion:** Bir sınıfın sorumluluklarının tek bir amaca hizmet etmesiyle alakalıdır. Yüksek cohesion daha iyidir çünkü bir sınıfın tek bir amaca odaklanmasını sağlar. Bu kavram SOLID prensiplerinden "Single Responsibility Principle" ile de doğrudan örtüşür.
**Coupling:** Bir sınıfın diğer sınıflara olan bağımlılığıdır. Düşük coupling daha iyidir, çünkü kodun daha esnek ve bakımının daha kolay olmasını sağlar. Loose Coupling sağlamak için Dependency Injection ve Interface kullanımı tercih edilebilir.

## 10) Heap and Stack means and differences ?
**Heap Memory:** Uygulama çalıştıktan sonra oluşturulan nesneler burada saklanır. Heap içindeki verilere referans değişkenleriyle erişilir. Garbage Collector burayı temizler yani kullanılmayan nesneleri otomatik olarak siler. 
**Stack Memory:** Local değişkenler ve metod çağrıları burada saklanır. Metot bittiğinde buradaki değişkenler otomatik olarak silinir. Stack çok hızlıdır çünkü belirli bir metodun içindeki değişkenleri tutar.

## 11) Exception means ? Type of Exceptions ?
**Exception:** Programın çalışması sırasında beklenmedik bir hata ile karşılaşırsa ortaya çıkan bir durumdur. Java'da hataları yönetmek için Exception Handling kullanılır.
**Checked Exceptions:** Derleme zamanında ele alınması gereken hatalardır. Bu tür hatalar uygun şekilde yakalanmazsa program derlenmez. (IOException, SQLException, FileNotFoundException)
**Unchecked Exceptions:** Çalışma zamanında oluşan hatalardır. Genellikle programcı hatalarından kaynaklanır ve kodun çalışması sırasında ortaya çıkar. (NullPointerException, ArrayIndexOutOfBoundsException)

## 12) How to summarize ‘clean code’ as short as possible ?
**Clean Code:** Readable, reusable ve maintainable kod yazma yaklaşımıdır.

## 13) What is the method of hiding in Java ?
**Method Hiding:** Eğer alt sınıf, üst sınıftaki static metodu aynı imzayla tekrar tanımlarsa üst sınıftaki metot gizlenmiş olur ancak override edilmez. Çünkü static metotlar nesneye değil doğrudan sınıfa bağlıdır. Bu yüzden hangi metotun çağrılacağı compile-time aşamasında belli olur.

## 14) What is the difference between abstraction and polymorphism in Java ?
**Abstraction:** Gereksiz detayları gizleyerek yalnızca nesnenin temel özelliklerine odaklanmamızı sağlar.
**Polymorphism:** Alt sınıfların, üst sınıftan gelen metotları kendilerine özgü şekilde kullanmalarını sağlar.
Örneğin Animal adında bir soyut sınıf oluşturup içine makeSound() metodu tanımlarsak bu abstraction olur. Daha sonra Cat ve Dog gibi alt sınıflar bu metodu kendilerine özgü şekilde “miyav” ve “hav hav” olarak override edersek bu da polymorphism olur.


