# UpcastingAndDowncastingNesnelerinTipDonusumleriKonuAnlatimi
Nesne tip dönüşümleri (object type casting), Swift ve diğer birçok programlama dilinde farklı türdeki nesneleri birbirine 
dönüştürmek için kullanılan bir kavramdır. Bu kavramı daha iyi anlamak için "downcasting" ve "upcasting" terimlerini 
açıklayalım:

Upcasting:

Upcasting, bir alt sınıfın (subclass) bir üst sınıfın (superclass) bir örneğine dönüştürülmesini ifade eder. Yani, 
daha özel bir tür olan alt sınıfın bir örneğini, daha genel bir tür olan üst sınıfın bir örneğine atarsınız. Bu tür 
dönüşüm güvenli ve otomatik olarak gerçekleşir.

Örnek:
class UstSinif {
    var adi: String = ""
}

class AltSinif: UstSinif {
    var altSinifOzelligi: String = ""
}

let altSinifInstance = AltSinif()
altSinifInstance.adi = "AltSınıf Adı"
altSinifInstance.altSinifOzelligi = "Özel Özellik"

let ustSinifInstance: UstSinif = altSinifInstance // Upcasting

print(ustSinifInstance.adi) // "AltSınıf Adı" olarak çıktı verir


Yukarıdaki örnekte, altSinifInstance önce AltSinif türünden oluşturulur ve ardından ustSinifInstance olarak 
UstSinif türüne yükseltilir (upcast). ustSinifInstance üzerinden adi özelliğine erişebiliriz, ancak altSinifOzelligi 
özelliğine erişemeyiz çünkü üst sınıf bu özelliği tanımaz.

Downcasting:

Downcasting, bir üst sınıfın bir örneğini, alt sınıfın bir örneğine dönüştürmeyi ifade eder. Bu işlem daha önce
upcasting ile yukarı çıkarılan bir nesnenin, aslında alt sınıfa ait olduğunu belirtmek için kullanılır. Ancak bu 
işlem güvenli değildir ve dönüşümün başarılı olup olmadığını kontrol etmek için "as" anahtar kelimesi veya "if let" 
veya "guard let" gibi kontrol ifadeleri kullanılır.

Örnek:
let ustSinifInstance: UstSinif = AltSinif()
if let altSinifInstance = ustSinifInstance as? AltSinif {
    print(altSinifInstance.altSinifOzelligi) // "Özel Özellik" olarak çıktı verir
}

Yukarıdaki örnekte, ustSinifInstance önce UstSinif türünden bir örnek olarak oluşturulur, ancak daha 
sonra downcasting ile AltSinif türüne dönüştürülür. "as?" anahtar kelimesi, bu dönüşümün güvenli olup olmadığını kontrol 
eder. Eğer güvenliyse, altSinifInstance kullanılarak alt sınıfın özelliklerine erişebiliriz.

Downcasting yaparken dikkatli olmalısınız, çünkü yanlış bir dönüşüm hataya yol açabilir (örneğin, uygun olmayan bir
türü dönüştürmeye çalışmak). Bu nedenle, güvenli downcasting için "if let" veya "guard let" gibi kontrol ifadelerini 
kullanmak önemlidir.

