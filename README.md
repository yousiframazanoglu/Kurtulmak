# Diriliş — Android Uygulaması

Porn izleme alışkanlığını bırakmak için kanıta dayalı bir refakatçi uygulama.
Türkçe, koyu tema, hem kadın hem erkek için cinsiyet-nötr içerikle yazıldı.

## Özellikler

- **Streak sayacı** — gün/saat/dakika hassasiyetinde, dairesel ilerleme halkası
- **Günlük check-in** — "temiz" / "düştüm" tek dokunuşla
- **Panik butonu** — anlık dürtü için 6 farklı dikkat dağıtma aktivitesi + 4-7-8 nefes animasyonu
- **Tetikleyici günlüğü** — duygu, tetikleyici etiketleri, not
- **İzin günü** — opsiyonel olarak haftalık veya aylık planlı izin (bilinçli karar)
- **Tasarruf hesabı** — geri kazanılan zaman ve para
- **Rozetler** — 1 / 3 / 7 / 14 / 30 / 60 / 90 / 180 / 365 gün
- **Veri ekranı** — en sık tetikleyiciler, düşüş sayısı, kazanç
- **Günlük motivasyon kartı** — nörobilim temelli 12 kart, her gün biri
- **Günlük bildirim** — WorkManager ile saat 09:00 (ayardan değişir)

## Mimari

- Kotlin + Jetpack Compose (Material 3)
- Tek Activity + Navigation Compose
- Room (SQLite) — journal & check-in
- DataStore Preferences — ayarlar ve streak başlangıcı
- WorkManager — günlük bildirim

## APK nasıl alınır?

### YOL 1 — GitHub Actions (önerilen, sıfır kurulum, ~5 dk)

Bilgisayarına hiçbir şey kurman gerekmez. GitHub bulutta derler, APK'yı indirirsin.

1. github.com'a gir (hesabın yoksa aç, ücretsiz)
2. Sağ üstte **"+"** → **"New repository"** → ismi `dirilis` ver → **Create**
3. Yeni reponun sayfasında **"uploading an existing file"** linkine tıkla
4. Bu zip'in **içeriğini** (Dirilis klasörünün **içindekileri**, klasörün kendisini değil) sürükleyip bırak — `app/`, `gradle/`, `.github/`, `build.gradle.kts`, `settings.gradle.kts`, `gradle.properties`, `.gitignore`, `README.md` hepsi olmalı
5. Aşağıda **"Commit changes"** butonuna bas
6. Üst menüden **"Actions"** sekmesine geç → "Build APK" workflow'u otomatik başlamış olacak (sarı nokta = çalışıyor, yeşil tik = bitti)
7. ~3-5 dakika bekle. Yeşil olunca workflow'a tıkla → en altta **"Artifacts"** kutusunda **`Dirilis-APK`** linkine tıkla → zip iner → içinde `Dirilis-v1.0-debug.apk` var
8. APK'yı telefonuna at, "bilinmeyen kaynaklar"a izin verip kur

### YOL 2 — Android Studio (yerel)

1. **Android Studio Ladybug (2024.2.1)** veya üstü indir: https://developer.android.com/studio
2. Bu klasörü Android Studio'da aç (`File > Open` → `Dirilis` klasörünü seç)
3. Sağ altta "Gradle Sync" başlayacak; kütüphaneleri indirsin (5-10 dk, ilk seferlik)
4. Sync bitince üst menüden: **Build > Build App Bundle(s) / APK(s) > Build APK(s)**
5. Hazır olunca sağ altta "locate" linkine tıkla → `app/build/outputs/apk/debug/app-debug.apk` çıkar
6. Bu APK'yı telefona at (kablo/Bluetooth/Telegram) ve "bilinmeyen kaynaklardan yüklemeye" izin ver

### Komut satırı ile (Android SDK kuruluysa)

```bash
cd Dirilis
./gradlew assembleDebug
# APK: app/build/outputs/apk/debug/app-debug.apk
```

İlk derlemede Gradle wrapper otomatik kendini kurar.

## Sürüm bilgisi

- Min SDK: 24 (Android 7.0)
- Target SDK: 34 (Android 14)
- versionCode: 1, versionName: "1.0"
- Paket adı: `com.yusuf.dirilis`

## Notlar

- Tüm veri telefonda yerel kalır; sunucuya hiçbir şey gitmez.
- DB ve preferences uygulamayı silersen kaybolur.
- Bildirim izni Android 13+ için otomatik istenir.
- Bu uygulama tıbbi tavsiye yerine geçmez. Uzman desteğine ihtiyacın olursa bir psikoloğa danışmanı öneririz.
