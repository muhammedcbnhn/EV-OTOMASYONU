#  Akıllı Ev Otomasyon Sistemi (Smart Home Automation)

Bu proje, **Nesne Yönelimli Programlama (OOP)** prensiplerini kullanarak geliştirilmiş bir akıllı ev simülasyonudur. Farklı türdeki elektronik cihazların (Televizyon, Klima vb.) merkezi bir sistem üzerinden yönetilmesini, açılıp kapatılmasını ve enerji tüketimlerinin hesaplanmasını simüle eder.

## Proje Hakkında

Bu uygulama, Java'nın temel yapı taşları olan **Interface**, **Abstract Class** ve **Inheritance** (Kalıtım) yapılarını pratik bir senaryo üzerinde uygular. Sistem, yeni cihaz türlerinin kolayca eklenmesine olanak tanıyan esnek bir yapıya sahiptir (Polymorphism).

### Özellikler
* ✅ **Merkezi Yönetim:** Tüm cihazlar tek bir liste (`ArrayList`) üzerinden yönetilir.
* ✅ **Polimorfizm:** Farklı cihazlar (TV, Klima) aynı komutlarla (`ac`, `kapat`) yönetilebilir.
* ✅ **Enerji Hesabı:** Her cihazın kendine özgü enerji tüketim katsayısı vardır ve toplam tüketim hesaplanabilir.
* ✅ **Durum Kontrolü:** Cihazların açık/kapalı durumu kontrol edilir, gereksiz işlemler engellenir.



## Kullanılan Teknolojiler ve Kavramlar

Bu projede aşağıdaki Java ve OOP kavramları kullanılmıştır:

* **Java (JDK 21+)**
* **Abstraction (Soyutlama):** `AkilliCihaz` soyut sınıfı ve `Kumanda` arayüzü.
* **Encapsulation (Kapsülleme):** `private` değişkenler ve `getter/setter` metotları.
* **Inheritance (Kalıtım):** `extends` anahtar kelimesi ile özellik aktarımı.
* **Polymorphism (Çok Biçimlilik):** `ArrayList<AkilliCihaz>` içinde farklı nesneleri tutabilme.



## Proje Mimarisi

Sistemin sınıf hiyerarşisi aşağıdaki gibidir:

```mermaid
classDiagram
    class Kumanda {
        <<interface>>
        +ac()
        +kapat()
    }
    class AkilliCihaz {
        <<abstract>>
        -String isim
        -boolean acikMi
        +enerjiTuketimiHesapla(saat)
    }
    class Televizyon {
        -int ekranBoyutu
    }
    class Klima {
        -int sogutmaDerecesi
    }
    
    Kumanda <|.. AkilliCihaz : implements
    AkilliCihaz <|-- Televizyon : extends
    AkilliCihaz <|-- Klima : extends
