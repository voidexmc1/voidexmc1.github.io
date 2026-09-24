# Telefonla Yayınlama (Android)

Bu yolla bilgisayarsız Android'e çıkabilirsin. iPhone/App Store için Mac gerekir, telefonla olmaz.

## 1) Oyunu internete koy (ücretsiz, GitHub Pages)
1. github.com'da ücretsiz hesap aç.
2. Yeni repo: adı tam olarak **KULLANICIADIN.github.io** olsun (Public).
3. Add file > Upload files: bu 7 dosyayı yükle: index.html, sw.js, manifest.webmanifest, privacy-policy.html, icon-192.png, icon-512.png, icon-maskable-512.png.
4. Add file > Create new file: adı `.nojekyll` (içi boş) > Commit.
5. privacy-policy.html'i aç, kalem ikonuyla düzenle, [E-POSTA ADRESİNİ BURAYA YAZ] yerine e-postanı yaz.
6. Settings > Pages > Branch: main > Save. 1-2 dakika sonra https://KULLANICIADIN.github.io adresinde oyun açılmalı. Aç ve dene.

## 2) Android paketi üret (PWABuilder)
1. Telefonda pwabuilder.com'u aç, oyun adresini gir.
2. Package for Stores > Android > Google Play. Package ID: com.emre.classicmojo. Signing key: **Create new**.
3. Gelen zip'te .aab dosyası, imza anahtarı (keystore), şifre bilgisi ve assetlinks.json var. **Anahtarı ve şifreyi güvenli yere kaydet**, kaybedersen güncelleme yapamazsın.

## 3) assetlinks.json (adres çubuğunu gizler)
GitHub'da Add file > Create new file. Adına şunu yaz: `.well-known/assetlinks.json` ve zip'teki assetlinks.json'un içeriğini yapıştır. Sonra https://KULLANICIADIN.github.io/.well-known/assetlinks.json adresini tarayıcıda açıp göründüğünü kontrol et.

## 4) Google Play Console
1. play.google.com/console: Chrome'da "Masaüstü sitesi" seçeneğini aç. Hesap: 25 dolar (tek sefer) + kimlik doğrulaması.
2. Uygulama oluştur: **Ücretsiz**. Metinler ve görseller için STORE_LISTING.md dosyasını kullan.
3. Hedef kitle: **13 yaş ve üzeri** (PWA tabanlı uygulamalar çocukları hedefleyemez). İçerik derecelendirmesinde "sohbet var" de. Veri güvenliği formunu doldur, gizlilik URL'si: https://KULLANICIADIN.github.io/privacy-policy.html
4. .aab dosyasını Kapalı test'e yükle.
5. **Olası sorun: hedef API seviyesi.** Google yeni yüklemelerde Android 16'yı (API 36) istiyor. PWABuilder'ın şablonu Temmuz 2026'da hâlâ 35'teydi. Yükleme "hedef API çok düşük" hatası verirse: Play Console'da süre uzatma talebi var mı bak (bildirilene göre 1 Kasım 2026'ya kadar), ya da bir bilgisayarda Android Studio ile paketi yeniden derle.
6. Yükledikten sonra: Kurulum > Uygulama bütünlüğü > Uygulama imzalama: SHA-256 parmak izini kopyala, assetlinks.json'a ikinci parmak izi olarak ekle.
7. Yeni kişisel hesapsa: 12 test kullanıcısı, 14 gün kesintisiz. Sonra Üretim erişimi için başvur.
