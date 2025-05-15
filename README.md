<p align="center">
  <!-- Projenizin logosunu veya ilgili bir görseli buraya ekleyebilirsiniz -->
  <img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/book-quran.svg" alt="Kur'an Simgesi" width="100" style="fill: #4CAF50;"/>
</p>

# Açık Kaynaklı Kur'an-ı Kerim Web Uygulaması 📖✨

**Kur'an-ı Kerim'i dijital dünyada en güzel, en doğru ve en erişilebilir şekilde deneyimlemenizi sağlayacak, topluluk destekli açık kaynaklı bir web uygulaması projesi.**

Bu proje, Diyanet İşleri Başkanlığı Bilgi İşlem Daire Başkanlığı ([@dib-bid](https://github.com/dib-bid/)) öncülüğünde, Müslüman yazılımcılar topluluğunun katkılarıyla geliştirilmektedir. Amacımız, herkesin Allah'ın kelamına kolayca ulaşabileceği, modern, kullanıcı dostu ve zengin özelliklere sahip bir web platformu oluşturmaktır.

[![Lisans: MIT](https://img.shields.io/badge/Lisans-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Next.js](https://img.shields.io/badge/Next.js-15+-black?logo=next.js)](https://nextjs.org/)
[![Redux Toolkit](https://img.shields.io/badge/Redux_Toolkit-활용-764ABC?logo=redux)](https://redux-toolkit.js.org/)

---

## 🎯 Projenin Amacı ve Motivasyonu

*   **Evrensel Erişim:** Kur'an-ı Kerim'e herkesin, her yerden, ücretsiz ve engelsiz bir şekilde web üzerinden erişimini sağlamak.
*   **Doğruluk ve Güvenilirlik:** Diyanet İşleri Başkanlığı'nın Mushafları İnceleme ve Kıraat Kurulu'nun onayladığı metinleri ve güvenilir kaynaklardan tefsir/mealleri temel almak.
*   **Modern Deneyim:** **Next.js 15+** ve **Redux Toolkit** gibi güncel teknolojileri kullanarak akıcı, estetik ve kullanıcı dostu bir arayüz sunmak.
*   **Topluluk Gücü:** Gönüllü yazılımcıların, tasarımcıların ve Kur'an ilimlerine vakıf kişilerin katkılarıyla projeyi sürekli geliştirmek ve zenginleştirmek.
*   **Açık Kaynak Felsefesi:** Şeffaflık, işbirliği ve bilgi paylaşımını teşvik etmek.

---

## ✨ Temel Özellikler (Web Uygulaması - Başlangıç Fazı)

*   **Kur'an Okuma:**
    *   Farklı hat seçenekleri (Mushaf-ı Şerif, Medine Hattı vb.)
    *   Sayfa, Cüz, Sure, Ayet navigasyonu
    *   Gece/Gündüz modu ve ayarlanabilir font boyutları
*   **Meal ve Tefsirler:**
    *   Diyanet İşleri Başkanlığı Meali (ve diğer güvenilir mealler)
    *   Seçili tefsirler (örn: Diyanet Tefsiri)
    *   Birden fazla meali/tefsiri aynı anda görüntüleyebilme (isteğe bağlı)
*   **Sesli Kur'an:**
    *   Tanınmış kârilerden farklı kıraat seçenekleri
    *   Ayet ayet veya sure bazında sesli takip
*   **Arama:**
    *   Kur'an metninde, meal ve tefsirlerde temel arama
*   **Kişiselleştirme (Cookie Tabanlı):**
    *   Yer imleri (bookmark) ekleme
    *   Son okunan yeri kaydetme
    *   Tema ve font ayarlarını kaydetme
*   **Erişilebilirlik:** Temel web erişilebilirlik standartlarına (WCAG) özen.

---

## 🛠️ Kullanılan Teknolojiler (Web Uygulaması)

Bu proje **tamamen frontend odaklı bir web uygulaması** olarak geliştirilmektedir.

*   **Ana Çatı (Framework):** **Next.js 15+** (App Router tercih edilebilir)
*   **Durum Yönetimi (State Management):** **Redux Toolkit**
*   **Programlama Dili:** TypeScript (Önerilir) / JavaScript
*   **Stil (Styling):** Tailwind CSS / CSS Modules / Styled Components (Topluluk kararına göre)
*   **API Entegrasyonu:** `fetch` API veya `axios` (Sağlanan [Kur'an API](https://github.com/dib-bid/quran-community-app/blob/main/API.md) ile entegrasyon)
*   **Linting & Formatting:** ESLint, Prettier
*   **Versiyon Kontrol:** Git & GitHub
*   **Paket Yöneticisi:** npm / yarn / pnpm

**Not:** Bu proje başlangıç aşamasında bir backend veya veritabanı içermemektedir. Tüm veriler harici [Kur'an API](https://github.com/dib-bid/quran-community-app/blob/main/API.md)'den çekilecek ve kullanıcıya özel ayarlar cookie'lerde saklanacaktır.

---

## 🚀 Nasıl Başlarım? (Kurulum)

**Detaylı kurulum talimatları ve önkoşullar için lütfen `INSTALLATION.md` (oluşturulacak) dosyasına göz atın.**

---

## 🙌 Nasıl Katkıda Bulunulur?

Bu proje hepimizin! Her türlü katkıya açığız ve minnettarız.

1.  **Fikir ve Öneriler:** "Issues" bölümünde yeni bir konu açarak fikirlerinizi, özellik isteklerinizi veya bulduğunuz hataları bildirebilirsiniz.
2.  **Kod Katkısı:**
    *   "Issues" bölümünden üzerinde çalışmak istediğiniz bir görev seçin veya yeni bir görev önerin. Proje yöneticileriyle iletişime geçerek görevi üstlenebilirsiniz.
    *   Projeyi fork'layın.
    *   Yeni bir branch oluşturun (`git checkout -b feature/yeni-ozellik` veya `fix/hata-duzeltmesi`).
    *   Değişikliklerinizi commit'leyin (Anlamlı commit mesajları kullanın, örn: `feat: Ayetlere yer imi ekleme özelliği geliştirildi`).
    *   Branch'inizi push'layın (`git push origin feature/yeni-ozellik`).
    *   Ana depoya bir Pull Request (PR) açın. PR'ınızda yaptığınız değişiklikleri açıklayın.
3.  **Tasarım Katkısı:** UI/UX tasarımları, ikonlar, görseller konusunda Figma, Adobe XD gibi araçlarla tasarımlar sunabilirsiniz.
4.  **Test ve Geri Bildirim:** Uygulamanın farklı tarayıcılarda ve cihazlarda (responsive tasarım) test edilerek hataların ve geliştirilebilecek yönlerin bildirilmesi.

**Lütfen katkıda bulunmadan önce `CONTRIBUTING.md` (Katkıda Bulunma Rehberi - oluşturulacak) ve `CODE_OF_CONDUCT.md` (Davranış Kuralları - oluşturulacak) dosyalarını okuyun.**

Amacımız saygılı, yapıcı ve işbirlikçi bir topluluk ortamı oluşturmaktır.

---

## 🗺️ Yol Haritası (Roadmap - Web Uygulaması)

*   **Faz 1 (Temel MVP - Minimum Uygulanabilir Ürün):**
    *   [ ] **Next.js 15+** ve **Redux Toolkit** ile proje altyapısının kurulması
    *   [ ] API'den sure listesi ve ayetlerin çekilip gösterilmesi
    *   [ ] Temel Kur'an okuma arayüzü (Sure/Ayet navigasyonu)
    *   [ ] Diyanet Meali'nin API'den çekilip gösterilmesi
    *   [ ] Basit arama özelliği (Ayet metninde)
    *   [ ] Gece/Gündüz modu (Cookie ile saklama)
*   **Faz 2 (İyileştirmeler ve Temel Kişiselleştirme):**
    *   [ ] Font boyutu ayarı (Cookie ile saklama)
    *   [ ] Yer imi ekleme/kaldırma (Cookie ile saklama)
    *   [ ] Son okunan ayeti hatırlama (Cookie ile saklama)
    *   [ ] API'den sesli kıraatlerin entegrasyonu ve oynatılması
    *   [ ] Detaylı UI/UX iyileştirmeleri ve responsive tasarımın güçlendirilmesi
*   **Faz 3 (Gelişmiş Özellikler ve Topluluk Katkıları):**
    *   [ ] Farklı meal ve tefsirlerin API üzerinden entegrasyonu (eğer API destekliyorsa)
    *   [ ] Gelişmiş arama filtreleri
    *   [ ] Tematik fihrist (API desteğine bağlı)
    *   [ ] Kapsamlı erişilebilirlik iyileştirmeleri (WCAG AA uyumu hedefi)

*Bu yol haritası topluluk geri bildirimleri ve katkılarıyla şekillenecektir.*

---

## 📜 Lisans

Bu proje **MIT Lisansı** altında lisanslanmıştır. Detaylar için `LICENSE` dosyasına bakınız. Bu, projeyi özgürce kullanabileceğiniz, değiştirebileceğiniz ve dağıtabileceğiniz anlamına gelir (lisans koşullarına uymak kaydıyla).

---

## 💬 İletişim ve Topluluk

*   **GitHub Issues:** Hata bildirimleri, özellik istekleri ve teknik tartışmalar için.
*   **GitHub Discussions:** Genel sohbet, fikir alışverişi ve duyurular için (Eğer etkinleştirildiyse).
*   **API Bilgileri:** [Kur'an API Dokümantasyonu](https://github.com/dib-bid/quran-community-app/blob/main/API.md)
*   **Diyanet Bilgi İşlem Daire Başkanlığı GitHub:** [@dib-bid](https://github.com/dib-bid/)
*   **Resmi İletişim (Kurumsal):** `bim@diyanet.gov.tr`

---

<p align="center">
  Allah (c.c.) bu hayırlı işte emeği geçen herkesten razı olsun.
</p>
