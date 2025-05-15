# Açık Kaynaklı Kur'an-ı Kerim Web Uygulamasına Katkıda Bulunma Rehberi

Öncelikle, Açık Kaynaklı Kur'an-ı Kerim Web Uygulaması projesine katkıda bulunmayı düşündüğünüz için teşekkür ederiz! Bu proje, Diyanet İşleri Başkanlığı Bilgi İşlem Daire Başkanlığı ([@dib-bid](https://github.com/dib-bid/)) öncülüğünde, topluluğun gücüyle daha iyi bir dijital Kur'an deneyimi sunmayı amaçlamaktadır.

Bu rehber, projeye nasıl katkıda bulunabileceğiniz konusunda size yol gösterecektir. Lütfen aşağıdaki adımları ve kuralları dikkatlice okuyun.

## Davranış Kuralları (Code of Conduct)

Tüm katılımcıların projemizin [Davranış Kuralları (CODE_OF_CONDUCT.md)](CODE_OF_CONDUCT.md) belgesine uyması beklenmektedir. Lütfen bu belgeyi okuyarak yapıcı ve saygılı bir topluluk ortamının korunmasına yardımcı olun.

## Nasıl Katkıda Bulunabilirim?

Katkılarınız birçok farklı şekilde olabilir:

*   **Hata Bildirimi (Reporting Bugs):** Uygulamada bir hata mı buldunuz? Lütfen "Issues" bölümünde detaylı bir rapor oluşturun. Raporunuzda şunları belirtmeye çalışın:
    *   Hatayı nasıl tekrarlayabileceğimiz (adımlar)
    *   Beklenen davranış
    *   Gerçekleşen davranış
    *   Kullandığınız tarayıcı ve işletim sistemi bilgileri
    *   Mümkünse ekran görüntüsü
*   **Özellik Önerileri (Suggesting Enhancements):** Uygulamaya eklenmesini istediğiniz yeni bir özellik veya mevcut bir özelliğin geliştirilmesi için bir fikriniz mi var? "Issues" bölümünde "feature request" (özellik isteği) etiketiyle bir konu açın. Fikrinizi ve neden faydalı olacağını düşündüğünüzü açıklayın.
*   **Kod Katkısı (Code Contributions):** En heyecan verici kısım! Eğer kod yazarak katkıda bulunmak isterseniz, aşağıdaki adımları izleyebilirsiniz.
*   **Belgelendirme (Documentation):** README, kurulum rehberi veya kod içi yorumlar gibi belgelerin iyileştirilmesine yardımcı olabilirsiniz.
*   **Tasarım (Design):** UI/UX konusunda önerileriniz veya Figma/XD gibi araçlarla hazırlanmış tasarımlarınız varsa paylaşabilirsiniz.

## İlk Kod Katkınız

Kod katkısında bulunmak istiyorsanız, işte size adım adım bir rehber:

1.  **Projeyi Fork'layın:** Bu depoyu kendi GitHub hesabınıza fork'layın.
2.  **Depoyu Klonlayın:** Fork'ladığınız depoyu yerel makinenize klonlayın:
    ```bash
    git clone https://github.com/SENIN_KULLANICI_ADIN/[KuranAppRepoAdi].git
    cd [KuranAppRepoAdi]
    ```
    *Not: `[KuranAppRepoAdi]` kısmını projenin gerçek repo adıyla değiştirin.*
3.  **Geliştirme Ortamını Kurun:** Projenin ana `README.md` dosyasındaki kurulum adımlarını izleyerek geliştirme ortamınızı hazırlayın.
4.  **Yeni Bir Branch Oluşturun:** Yapacağınız değişiklikler için yeni bir branch oluşturun. Branch adlarınızın açıklayıcı olmasına özen gösterin (İngilizce tercih edilir):
    ```bash
    git checkout -b feature/ayet-paylasma-ozelligi
    # veya hata düzeltmesi için:
    # git checkout -b fix/arama-sonuclari-sorunu
    ```
5.  **Değişikliklerinizi Yapın:** İlgili dosyalarda kod değişikliklerinizi yapın. Projenin kullandığı teknolojilere (Next.js 15+, Redux Toolkit, TypeScript vb.) ve kodlama standartlarına uymaya çalışın.
6.  **Değişikliklerinizi Test Edin:** Yaptığınız değişikliklerin beklendiği gibi çalıştığından ve mevcut özellikleri bozmadığından emin olun.
7.  **Commit'lerinizi Oluşturun:** Değişikliklerinizi anlamlı commit mesajları ile kaydedin. [Conventional Commits](https://www.conventionalcommits.org/) formatını kullanmaya özen gösterin:
    ```bash
    git add .
    git commit -m "feat: Ayetlere sosyal medya paylaşım butonu eklendi"
    # veya
    # git commit -m "fix: Arama sonuçlarındaki nadir bir bug düzeltildi"
    ```
8.  **Branch'inizi Push'layın:** Oluşturduğunuz branch'i kendi fork'ladığınız depoya push'layın:
    ```bash
    git push origin feature/ayet-paylasma-ozelligi
    ```
9.  **Pull Request (PR) Açın:** GitHub üzerinden fork'ladığınız depodan ana projeye ( `dib-bid/[KuranAppRepoAdi]` ) bir Pull Request açın.
    *   PR başlığınızın ve açıklamanızın net ve anlaşılır olmasına dikkat edin.
    *   Yaptığınız değişiklikleri ve nedenlerini açıklayın.
    *   Eğer bir "Issue" ile ilgiliyse, PR açıklamanızda `Closes #123` gibi bir ifadeyle ilgili "Issue"yu referans gösterin.

## Pull Request Süreci

1.  PR'ınız proje yöneticileri tarafından incelenecektir.
2.  Geri bildirimler veya değişiklik talepleri olabilir. Lütfen yapıcı eleştirilere açık olun.
3.  Gerekli düzenlemeler yapıldıktan ve onay alındıktan sonra PR'ınız ana branch'e (genellikle `main` veya `develop`) merge edilecektir.

## Kodlama Standartları

*   **Dil:** Kod içi yorumlar ve değişken isimleri için tutarlı olun. Topluluk projesi olduğu için İngilizce terimler ve yorumlar daha geniş bir kitleye hitap edebilir.
*   **Formatlama:** Projede ESLint ve Prettier gibi araçlar kullanılıyorsa, lütfen bu araçların belirlediği formatlama kurallarına uyun.
*   **Testler:** Eğer projenin test altyapısı varsa, eklediğiniz özellikler veya yaptığınız düzeltmeler için test yazmaya özen gösterin.

## İletişim

Herhangi bir sorunuz veya takıldığınız bir nokta olursa, "Issues" bölümünden soru sormaktan veya "Discussions" (eğer aktifse) bölümünü kullanmaktan çekinmeyin.

Katkılarınız için şimdiden teşekkür ederiz! Bu projeyi birlikte daha iyi bir hale getireceğimize inanıyoruz.
