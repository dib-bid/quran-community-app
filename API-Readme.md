# Diyanet İşleri Başkanlığı Kur'an Portalı API Dokümantasyonu

Bu doküman, Diyanet İşleri Başkanlığı Bilgi İşlem Daire Başkanlığı tarafından sunulan Kur'an Portalı (kuran.diyanet.gov.tr) API endpoint'lerini ve kullanımlarını açıklamaktadır.

## İçindekiler

1.  [Mushaf Sayfa Verisi API (`/mushaf/qurandm/pagedata`)](#1-mushaf-sayfa-verisi-api-mushafqurandmpagedata)
    *   [Endpoint Bilgileri](#endpoint-bilgileri)
    *   [Query Parametreleri](#query-parametreleri)
    *   [İstek Örneği](#istek-örneği)
    *   [Yanıt Yapısı (JSON)](#yanıt-yapısı-json)
    *   [Önemli Notlar (`pagedata` için)](#önemli-notlar-pagedata-için)
2.  [Ses Dosyası (Tilavet) Endpoint'i ve Oluşturulması](#2-ses-dosyası-tilavet-endpointi-ve-oluşturulması)
    *   [URL Yapısı](#url-yapısı)
    *   [Parametreler (URL için)](#parametreler-url-için)
    *   [Kâri Kodları ve `iqr` Eşleşmesi](#kâri-kodları-ve-iqr-eşleşmesi)
    *   [İstek Yöntemi ve Durum Kodu](#istek-yöntemi-ve-durum-kodu)
3.  [Konularına Göre Fihrist API'leri](#3-konularına-göre-fihrist-apileri)
    *   [3.1. Ana Konu Kategorilerini Listeleme (`/getCatList`)](#31-ana-konu-kategorilerini-listeleme-getcatlist)
    *   [3.2. Alt Konu Kategorilerini Listeleme (`/getSubCatList`)](#32-alt-konu-kategorilerini-listeleme-getsubcatlist)
    *   [3.3. Belirli Bir Konuya Ait Ayetleri Listeleme (`/GetFihristItemList`)](#33-belirli-bir-konuya-ait-ayetleri-listeleme-getfihristitemlist)
4.  [Genel Bilgiler ve Kullanım Koşulları](#4-genel-bilgiler-ve-kullanım-koşulları)

---

## 1. Mushaf Sayfa Verisi API (`/mushaf/qurandm/pagedata`)

Bu endpoint, Kur'an-ı Kerim'in belirli bir sayfasındaki ayetleri, mealleri ve ilgili meta verileri getirmek için kullanılır.

### Endpoint Bilgileri

*   **URL:** `https://kuran.diyanet.gov.tr/mushaf/qurandm/pagedata`
*   **HTTP Metodu:** `GET`
*   **Yanıt Formatı:** `JSON`

### Query Parametreleri

| Parametre | Tip     | Zorunlu Mu? | Varsayılan | Açıklama                                                                                                                               | Örnek Değerler        |
| :-------- | :------ | :---------- | :--------- | :------------------------------------------------------------------------------------------------------------------------------------- | :-------------------- |
| `id`      | Integer | Evet        | Yok        | Getirilecek Mushaf sayfa numarası. **Not:** API yanıtındaki `PageNo` değeri, bu `id`'den bir fazla olabilir (örn: `id=128` için `PageNo=129`). | `1`, `128`, `604`     |
| `itf`     | Integer | Hayır       | `0`        | Tefsir ID'si veya interaktif tefsir formatı. `0` tefsirin kapalı veya varsayılan olduğunu gösterir.                                      | `0`                   |
| `iml`     | Integer | Hayır       | `1`        | Mushaf sayfa resim katmanı. `1` sayfanın standart görsel temsilinin aktif olduğunu belirtir.                                               | `1`                   |
| `iqr`     | Integer | Hayır       | `1`        | Kâri (Okuyucu) ID'si. Bu ID, istemci tarafında ses dosyası URL'lerini oluşturmak için kullanılır. (Bkz: [Ses Dosyası Endpoint'i](#2-ses-dosyası-tilavet-endpointi-ve-oluşturulması)) | `1`, `6`, `11`, `13`  |
| `ml`      | Integer | Evet        | Yok        | Meal lisanı veya Meal ID'si. Farklı ID'ler farklı mealleri (çevirileri) temsil eder.                                                    | `4`, `5`              |
| `ql`      | Integer | Evet        | Yok        | Kur'an (Arapça) metninin kaynak/versiyon ID'si.                                                                                        | `7` (Standart Metin)  |
| `iar`     | Integer | Hayır       | `0`        | Arapça metin gösterim modu. `0` metin tabanlı (standart fontlar), `1` istemci tarafında resim tabanlı gösterim (örn: Şeyh Hamdullah hattı) için işaretleyici. | `0`, `1`              |

### İstek Örneği

```
https://kuran.diyanet.gov.tr/mushaf/qurandm/pagedata?id=128&itf=0&iml=1&iqr=1&ml=4&ql=7&iar=0
```

### Yanıt Yapısı (JSON)

Başarılı bir istek (`200 OK`) aşağıdaki gibi bir JSON nesnesi döndürür:

```json
{
    "PointerList": null, // İleriye dönük kullanım veya özel işaretçiler için.
    "CuzNo": 7,
    "PageNo": 129,
    "ArCuzNo": "۷",
    "ArPageNo": "۱۲۹",
    "QuranAyats": [
        {
            "Id": 5586,
            "SureId": 6,
            "AyetId": 9,
            "LanguageId": 7, // 'ql' ile eşleşir
            "AyetNumber": "٩",
            "AyetVisible": true,
            "Page": 129,
            "AyetText": " وَلَوْ جَعَلْنَاهُ مَلَكًا لَجَعَلْنَاهُ رَجُلًا وَلَلَبَسْنَا عَلَيْهِمْ مَا يَلْبِسُونَ",
            "Recitation": "", // Ses URL'si istemcide oluşturulur.
            "AyetMeta": null, // İleriye dönük kullanım veya özel meta veriler için. 
            "RegionList": null, // Kelime bazlı koordinatlar veya işaretlemeler için olabilir.
            "Sure": { // Sadece sayfadaki ilk ayette dolu gelir
                "SureId": 6,
                "MealInfo": "Mekke döneminde inmiştir...",
                "SureNameTurkish": "En'âm",
                "SureNameArabic": "الْاَنْعَامِ",
                "BesmeleVisible": true,
                "HeaderOnBackPage": false, //
                "InisOrder": 55,
                "AyetCount": 165,
                "Cuz": 7,
                "FirstPage": 128
            }
        }
        // ... sayfadaki diğer Arapça ayetler
    ],
    "MealAyats": [
        {
            "Id": 5583,
            "SureId": 6,
            "AyetId": 9,
            "LanguageId": 4, // 'ml' ile eşleşir
            "AyetNumber": "9",
            "AyetVisible": true,
            "Page": 129,
            "AyetText": "Eğer peygamberi bir melek kılsaydık muhakkak ki onu insan sûretine sokar onları yine düşmekte oldukları kuşkuya düşürürdük.",
            "Recitation": "",
            "AyetMeta": null,
            "RegionList": null,
            "Sure": { // Sadece sayfadaki ilk ayette dolu gelir
                // ... QuranAyats.Sure ile aynı yapı
            }
        }
        // ... sayfadaki diğer meal ayetleri
    ],
    "TefsirList": null, // 'itf' ile tefsir istenirse ilgili tefsir verisi burada yer alır.
    "MealSureLabel": "En'âm",
    "QuranSureLabel": "الْاَنْعَامِ",
    "EndPageSure": null // Sayfanın bir surenin son sayfası olup olmadığını belirtebilir.
}
```

### Önemli Notlar (`pagedata` için)

*   **`iar` Parametresinin Etkisi:** `iar=1` parametresi, sunucudan gelen JSON yanıtının yapısını değiştirmez. Arapça ayet metinleri (`AyetText`) her zaman metin olarak gelir. Bu parametre, istemci tarafındaki uygulamaya, bu metni standart fontlar yerine özel hat resimleriyle (örn: Şeyh Hamdullah hattı) göstermesi için bir işaretleyici görevi görür.
*   **Sayfa Numaralandırması (`id` vs `PageNo`):** URL'de kullanılan `id` parametresi ile yanıtta dönen `PageNo` arasında bir fark olabilir. Örneğin, `id=128` istendiğinde yanıtta `PageNo=129` gelebilir. `id` parametresi 0-tabanlı bir indeks veya sayfa çiftlerinden birini temsil ediyor olabilir.
*   **`Sure` Nesnesi:** Hem `QuranAyats` hem de `MealAyats` dizilerindeki ilk ayet objesi, o sayfada başlayan veya devam eden sure hakkında detaylı bilgi içeren bir `Sure` nesnesine sahiptir. Aynı sayfadaki diğer ayetlerde bu `Sure` nesnesi `null` olarak gelir.

---

## 2. Ses Dosyası (Tilavet) Endpoint'i ve Oluşturulması

`pagedata` API'si doğrudan ses dosyası (tilavet) URL'lerini döndürmez. İstemci tarafı, `pagedata` API'sine gönderilen `iqr` (Kâri ID) parametresi ve `pagedata` yanıtındaki `SureId` ile `AyetId` bilgilerini kullanarak ses dosyası URL'lerini dinamik olarak oluşturur.

### URL Yapısı

*   **Temel URL:** `https://webdosya.diyanet.gov.tr/kuran/kuranikerim/Sound/`
*   **Dinamik Kısım:** `{KARI_KODU}/{SURE_NO}_{AYET_NO}.mp3`
*   **Tam Örnek:** `https://webdosya.diyanet.gov.tr/kuran/kuranikerim/Sound/ar_osmanSahin/1_1.mp3`

### Parametreler (URL için)

*   **`{KARI_KODU}`:** Seçilen kâriye karşılık gelen koddur.
*   **`{SURE_NO}`:** `pagedata` yanıtındaki `QuranAyats[].SureId` değeridir.
*   **`{AYET_NO}`:** `pagedata` yanıtındaki `QuranAyats[].AyetId` değeridir.

### Kâri Kodları ve `iqr` Eşleşmesi

Aşağıdaki tablo, arayüzdeki Kâri seçimine, `pagedata` API'sindeki ilgili `iqr` değerine ve URL'de kullanılacak `{KARI_KODU}`'nu göstermektedir. (**Not:** Bu liste tam ve eksiksiz olmalıdır, lütfen kurum içi kaynaklardan doğrulayınız.)

| Kâri Adı                      | `iqr` Değeri (`pagedata`) | `{KARI_KODU}` (URL'de) |
| :------------------------------ | :------------------------ | :----------------------- |
| Hafız Osman Şahin             | `1`                       | `ar_osmanSahin`          |
| Dr. Tayyar Altıkulaç            | `2`                       | `ar_tayyaraltikulac`     |
| İshak Danış                     | `3`                       | `ar_ishakdanis`          |
| Davut Kaya                      | `6`                       | `ar_davutkaya`           |
| Suud İbrahim eş-Şureym          | `8`                       | `ar_suudibrahimesureym`  |
| Mahir el-Muaykili               | `9`                       | `ar_mahirelmuaykili`     |
| Muhammed Sıddık Minşevi         | `10`                      | `ar_muhammedsiddikminsevi`|
| Abdulbasit Abdussamed           | `11`                      | `ar_abdussamet`          |
| Abdullah Al Juhani              | `12`                      | `ar_abdullahaljuhani`    |
| Mehmet Çevik                    | `13`                      | `ar_mehmetcevik`         |
| ... (Diğer kâriler)           | ...                       | ...                      |

### İstek Yöntemi ve Durum Kodu

*   **İstek Yöntemi:** `GET`
*   **Tipik Durum Kodu:** `206 Partial Content` (Sunucu, dosyanın bir kısmını gönderir, bu ses/video akışı için normaldir).

---

## 3. Konularına Göre Fihrist API'leri

Bu endpoint'ler, Kur'an-ı Kerim'deki ayetleri konularına göre listelemek için kullanılır.

### 3.1. Ana Konu Kategorilerini Listeleme (`/getCatList`)

*   **URL:** `https://kuran.diyanet.gov.tr/mushaf/qurandm/getCatList`
*   **HTTP Metodu:** `GET`
*   **Parametreler:** Yok
*   **Yanıt Formatı:** `JSON`
*   **Açıklama:** Kur'an fihristindeki ana konu başlıklarını listeler.
*   **Örnek Yanıt:**
    ```json
    [
        { "Id": 1, "Name": "Ahlak" },
        { "Id": 2, "Name": "Aile Düzeni" }
        // ... diğer kategoriler
    ]
    ```
*   **Yanıt Alanları:**
    *   `Id` (Integer): Kategorinin benzersiz ID'si.
    *   `Name` (String): Kategorinin adı.

### 3.2. Alt Konu Kategorilerini Listeleme (`/getSubCatList`)

*   **URL:** `https://kuran.diyanet.gov.tr/mushaf/qurandm/getSubCatList`
*   **HTTP Metodu:** `GET`
*   **Yanıt Formatı:** `JSON`
*   **Açıklama:** Belirli bir ana kategoriye ait alt konu başlıklarını listeler.
*   **Query Parametreleri:**
    | Parametre | Tip     | Zorunlu Mu? | Açıklama                                 | Örnek Değer |
    | :-------- | :------ | :---------- | :--------------------------------------- | :---------- |
    | `id`      | Integer | Evet        | Ana kategorinin ID'si (`/getCatList`'ten alınır). | `1`         |
*   **Örnek İstek:** `https://kuran.diyanet.gov.tr/mushaf/qurandm/getSubCatList?id=1`
*   **Örnek Yanıt:**
    ```json
    [
        { "Id": 1, "Name": "Adalet" },
        { "Id": 2, "Name": "Adam Öldürmenin Cezası" }
        // ... diğer alt kategoriler
    ]
    ```
*   **Yanıt Alanları:**
    *   `Id` (Integer): Alt kategorinin benzersiz ID'si.
    *   `Name` (String): Alt kategorinin adı.

### 3.3. Belirli Bir Konuya Ait Ayetleri Listeleme (`/GetFihristItemList`)

*   **URL:** `https://kuran.diyanet.gov.tr/mushaf/qurandm/GetFihristItemList`
*   **HTTP Metodu:** `GET`
*   **Yanıt Formatı:** `JSON`
*   **Açıklama:** Belirli bir alt konu kategorisine giren ayetlerin listesini (meal metinleriyle birlikte) döndürür.
*   **Query Parametreleri:**
    | Parametre | Tip     | Zorunlu Mu? | Açıklama                                     | Örnek Değer |
    | :-------- | :------ | :---------- | :------------------------------------------- | :---------- |
    | `id`      | Integer | Evet        | Alt kategorinin ID'si (`/getSubCatList`'ten alınır). | `1`         |
*   **Örnek İstek:** `https://kuran.diyanet.gov.tr/mushaf/qurandm/GetFihristItemList?id=1`
*   **Örnek Yanıt:**
    ```json
    [
        {
            "Id": 746,
            "SureId": 2,
            "AyetId": 100,
            "LanguageId": 4, // Meal dili ID'si
            "AyetNumber": "100",
            "AyetVisible": true,
            "Page": 15,
            "AyetText": "Ne zaman onlar bir antlaşma yaptılarsa, yine kendilerinden bir grup onu bozmadı mı? Zaten onların çoğu iman etmez.", // Meal metni
            "Recitation": "",
            "AyetMeta": null,
            "RegionList": null,
            "Sure": null
        }
        // ... o konudaki diğer ayetler
    ]
    ```
*   **Yanıt Alanları (Her bir ayet nesnesi için):**
    *   `Id` (Integer): Fihristteki ayetin benzersiz ID'si.
    *   `SureId` (Integer): Surenin ID'si.
    *   `AyetId` (Integer): Sure içindeki ayetin ID'si (numarası).
    *   `LanguageId` (Integer): Meal metninin dil ID'si.
    *   `AyetNumber` (String): Ayet numarasının metin temsili.
    *   `AyetVisible` (Boolean): Ayetin görünürlüğü.
    *   `Page` (Integer): Ayetin bulunduğu Mushaf sayfa numarası.
    *   `AyetText` (String): Ayetin meal metni.
    *   `Recitation` (String): Genellikle boş.
    *   `AyetMeta` (Null):
    *   `RegionList` (Null):
    *   `Sure` (Null).

---

## 4. Genel Bilgiler ve Kullanım Koşulları

*   Bu API'ler, Diyanet İşleri Başkanlığı Kur'an Portalı'nın işlevselliğini desteklemek amacıyla sunulmaktadır.
*   API'lerin kullanımı, Diyanet İşleri Başkanlığı'nın belirleyeceği kullanım koşullarına ve politikalarına tabidir.
*   API'ler üzerinde zaman zaman bakım ve güncelleme çalışmaları yapılabilir. Bu tür durumlarda API erişiminde kesintiler yaşanabilir.
*   API'lerin aşırı ve kötü niyetli kullanımı tespit edildiğinde erişim kısıtlamaları uygulanabilir.
*   Teknik destek veya sorularınız için [bim@diyanet.gov.tr].

**Doküman Sürümü:** 1.0
**Son Güncelleme Tarihi:** [2025-05-15]

```
