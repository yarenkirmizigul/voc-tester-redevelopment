# Modüller Detaylı Tanımı

## 📊 Modül Özeti

| Modül | Açıklama | Kullanıcılar | Ana Fonksiyon |
|-------|----------|-------------|---------------|
| Dashboard | Sistem özeti | Tüm roller | Kısayol ve istatistikler |
| Adaylar | Aday yönetimi | Firma, Yönetici | Aday kaydı ve takibi |
| Firmalar | Firma yönetimi | Yönetici | Firma bilgisi ve yetkililer |
| Meslekler | Meslek/Yeterlilik | Yönetici | Meslek tanımları |
| Sorular | Soru bankası | Eğitmen, Yönetici | Teorik ve praktik sorular |
| Sınavlar | Sınav yönetimi | Yönetici, Gözetmen | Sınav oluşturma ve uygulanması |
| Performans | Performans değerlendirme | Değerlendirici | İşyerinde gözlem |
| Belgelendirme | Belge yönetimi | Belgelendirme Sorumlusu | Sertifika düzenleme |
| Belgeler | Belge şablonları | Yönetici | PDF ve şablonlar |
| Raporlar | Sistem raporları | Yönetici, Muhasebe | İstatistikler ve analizler |
| Kullanıcılar | Kullanıcı yönetimi | Sistem Yöneticisi | Kullanıcı hesabı ve rol |
| Ayarlar | Sistem ayarları | Sistem Yöneticisi | Konfigürasyonlar |

---

## 1️⃣ DASHBOARD

### Amaç
Sistem kullanıcılarının en sık ihtiyaç duydukları bilgileri tek ekranda sunmak.

### Ana Bileşenler

#### 1.1 İstatistik Kartları (Top Section)
```
┌─────────────────┬─────────────────┬─────────────────┐
│ Toplam Adaylar  │ Beklemede       │ Sertifikalı     │
│     2,451       │      145        │     1,203       │
└─────────────────┴─────────────────┴─────────────────┘
```

**Kartlar:**
- Toplam Adaylar
- Aktif Başvurular
- Bu Ay Sertifikalı
- Beklemede İşlemler

#### 1.2 Grafik ve Çizelgeler

**A) Aylık Sertifika Trendi**
- X Ekseni: Aylar (Son 12 ay)
- Y Ekseni: Adet
- Türü: Line Chart

**B) Meslek Dağılımı**
- Türü: Pie Chart
- Gösterim: Her meslekten kaç aday

**C) Sınav Başarı Oranı**
- Türü: Bar Chart
- Başarılı / Başarısız

#### 1.3 Son İşlemler (Recent Activity)
```
Sıra | İşlem | Tarih | Durum
-----|-------|-------|-------
1    | Aday Kaydı | 08.07.2026 | Başarılı
2    | Sınav Yapıldı | 08.07.2026 | Tamamlandı
3    | Sertifika Verildi | 07.07.2026 | Aktif
```

#### 1.4 Hızlı Linkler (Shortcuts)
- ➕ Yeni Aday Ekle
- 📋 Beklemede Başvurular
- 📝 Yapılacak Sınavlar
- 📊 Raporlar

### Tasarım Özellikleri
- Responsive grid layout
- Real-time veri güncellemesi
- Filtreleme (tarih aralığı, meslek)
- Export (PDF, Excel)

---

## 2️⃣ ADAYLAR (Candidate Management)

### Amaç
Adayların kayıt, takip ve yönetimini merkezi olarak sağlamak.

### 2.1 Aday Listesi Ekranı

#### Üst Bölüm (Toolbar)
```
[Filtre] [Yeni Aday] [Excel] [PDF] [Yazdır] [Yenile]
```

#### Filtreler
- Durum (Tüm, Yeni Kayıt, Beklemede, Başvurulu, Sertifikalı, İptal)
- Meslek (Dropdown)
- Birim (Dropdown)
- Kayıt Tarihi (Date Range)
- Arama (Adı, TC No, E-posta)

#### Tablo Sütunları
```
☑ | Ad Soyad | TC No | Meslek | Durum | Son İşlem | İşlemler
```

**Durum Göstergesi:**
- 🟢 Sertifikalı
- 🟡 Beklemede
- 🔴 Başarısız
- ⚪ Yeni

#### Satır İşlemleri
- Görüntüle (🔍)
- Düzenle (✏️)
- Sil (🗑️)
- Başvuru Yap (📝)

### 2.2 Aday Detay Ekranı

```
┌─────────────────────────────────────────┐
│ Aday Detayları - Ahmet Yılmaz          │
└─────────────────────────────────────────┘

📋 Sekmeler:
├─ Kişisel Bilgiler
├─ İletişim Bilgileri
├─ Eğitim Bilgileri
├─ Belgeler
├─ Başvurular
├─ Sınavlar
├─ Performans
├─ Sertifikalar
└─ Geçmiş
```

#### 2.2.1 Kişisel Bilgiler Sekmesi
```
İnsan İkonu | Ad: Ahmet | Soyad: Yılmaz
            | TC No: 12345678901
            | Doğum Tarihi: 01.01.1990
            | Cinsiyet: Erkek
            | Uyruk: Türkiye
```

**Alanlar:**
- Ad (Zorunlu)
- Soyad (Zorunlu)
- TC Kimlik No (Zorunlu, Unique)
- Doğum Tarihi (Zorunlu)
- Doğum Yeri (Opsiyonel)
- Cinsiyet (Zorunlu)
- Uyruk (Zorunlu)
- Medeni Durum (Opsiyonel)

#### 2.2.2 İletişim Bilgileri Sekmesi
```
📧 E-posta: ahmet@example.com
📱 Cep: +90 555 123 4567
☎️  Telefon: +90 212 555 5555
📍 Adres: Kadıköy, İstanbul
🏘️ İlçe: Kadıköy
🏙️ İl: İstanbul
📮 Posta Kodu: 34700
🌍 Ülke: Türkiye
```

#### 2.2.3 Eğitim Bilgileri Sekmesi
```
Eğitim Geçmişi:

Sıra | Okul Adı | Derece | Mezuniyet Tarihi | Bölüm
----|----------|--------|------------------|------
1   | İTÜ      | Lisans | 01.06.2012      | Elektrik
2   | Acibadem | HS     | 01.06.2008      | Fen
```

**Alanlar:**
- Okul Adı (Zorunlu)
- Derece (Lisans, Yüksek Lisans, Doktora, HS, Lise)
- Bölüm (Zorunlu)
- Mezuniyet Tarihi (Zorunlu)
- Diploma No (Opsiyonel)
- Ortalama (Opsiyonel)

#### 2.2.4 Belgeler Sekmesi
```
Belge Türü | Dosya Adı | Yüklenme Tarihi | İşlemler
-----------|-----------|-----------------|----------
Diploma    | diploma.pdf | 05.07.2026 | İndir | Sil
Sertifika  | sert.pdf   | 04.07.2026 | İndir | Sil

[Belge Yükle] butonu
```

**Desteklenen Dosya Türleri:**
- PDF
- JPG, PNG (Resimleri PDF'e dönüştür)
- DOC, DOCX (PDF'e dönüştür)

**Dosya Kısıtlamaları:**
- Max 10 MB
- Virüs taraması zorunlu

#### 2.2.5 Başvurular Sekmesi
```
Başvuru No | Tarih | Yeterlilik | Durum | İşlemler
-----------|-------|-----------|--------|----------
BAŞV-2026-001 | 01.07 | Elektrikçi | Onaylandı | Görüntüle
```

#### 2.2.6 Sınavlar Sekmesi
```
Sınav No | Tarih | Sorular | Puan | Başarı | İşlemler
---------|-------|--------|------|--------|----------
SINAV-001 | 05.07.2026 | 50 | 85 | ✅ Başarılı | Detay
```

#### 2.2.7 Performans Sekmesi
```
Değerlendirme No | Tarih | Puan | Durum | İşlemler
----------------|-------|------|--------|----------
PERF-001 | 06.07.2026 | 92 | Tamamlandı | Detay
```

#### 2.2.8 Sertifikalar Sekmesi
```
Sertifika No | Meslek | Başlangıç | Bitiş | Durum | İşlemler
-------------|--------|-----------|-------|--------|----------
SER-2026-001 | Elektrikçi | 07.07.2026 | 07.07.2029 | Aktif | İndir | Yenile
```

#### 2.2.9 Geçmiş Sekmesi
```
Tarih | İşlem | Yapan Kullanıcı | Notlar
------|-------|-----------------|-------
08.07 | Aday Kaydı Güncellendi | admin | E-posta değiştirildi
07.07 | Sertifika Düzenlendi | belgele | SER-2026-001
```

### 2.3 Yeni Aday Formu

```
[Adım 1 of 3] Kişisel Bilgiler

Ad *                    [_____________]
Soyad *                 [_____________]
TC No *                 [_____________]
Doğum Tarihi *          [___/___/____]
Cinsiyet *              [Erkek ▼] [Kadın]
Uyruk *                 [Türkiye ▼]

[Devam] [İptal]
```

**Form Özelikleri:**
- 3 adımlı wizard
- Adımlar arası geçişe izin ver
- İlerleme çubuğu göster
- Başarı mesajı

---

## 3️⃣ FIRMALAR (Company Management)

### Amaç
Firma bilgilerini ve yetkililerini merkezi olarak yönetmek.

### 3.1 Firma Listesi

```
Filtre: [Tüm] [Aktif] [Pasif]

Ad | Vergi No | Şehir | Çalışan Sayısı | İşlemler
---|---------|-------|-----------------|----------
ABC İnşaat | 123456 | İstanbul | 45 | Düzenle, Sil, Detay
```

### 3.2 Firma Detay

#### Sekmeler:
1. **Genel Bilgiler**
   - Firma Adı
   - Vergi No / Kuruluş No
   - Kuruluş Tarihi
   - İş Sektörü
   - Telefon
   - E-posta
   - Website

2. **Adres Bilgileri**
   - Merkez Adres
   - İl, İlçe
   - Posta Kodu

3. **Yetkililer**
   ```
   Ad Soyad | Görevi | E-posta | Telefon | İşlemler
   ---------|--------|---------|---------|----------
   Mehmet A. | Müdür | mehmet@.. | 5551234 | Düzenle, Sil
   ```

4. **Çalışan Adaylar**
   - Firma ile bağlantılı aday listesi
   - Başvuru durumları

---

## 4️⃣ MESLEKLER (Professions Management)

### Amaç
Sistem tarafından sunulan meslekler ve yeterliliklerini tanımlamak.

### 4.1 Meslek Listesi

```
Meslek | Yeterlilik Sayısı | Aktif | İşlemler
-------|------------------|-------|----------
Elektrikçi | 3 | ✅ | Düzenle, Detay
İnşaat İşçisi | 2 | ✅ | Düzenle, Detay
```

### 4.2 Meslek Detay

```
📌 Meslek: Elektrikçi
└─ Yeterlilikler:
   ├─ Temel Elektrik (ID: YET-001)
   │  └─ Min Yaş: 18
   │  └─ Süre: 3 ay
   │  └─ Sınav Soru Sayısı: 50
   │
   ├─ İleri Elektrik (ID: YET-002)
   │  └─ Ön Koşul: Temel Elektrik
   │  └─ Sınav Soru Sayısı: 75
   │
   └─ Elektrik Öğretmenliği (ID: YET-003)
      └─ Ön Koşul: İleri Elektrik
```

### 4.3 Birimler (Units)

```
Birim | Meslek | Lokasyon | İşlemler
------|--------|----------|----------
İstanbul Merkez | Elektrikçi | İstanbul | Düzenle
Ankara Şubesi | Elektrikçi | Ankara | Düzenle
```

---

## 5️⃣ SORULAR (Question Bank)

### Amaç
Sınavlar için kullanılacak sorular ve kategorileri yönetmek.

### 5.1 Soru Listesi

```
Filtre: [Tüm] [Teorik] [Performans] [Aktif] [Pasif]

Soru | Kategori | Tip | Zorluk | Kullanılan | İşlemler
-----|----------|-----|--------|-----------|----------
"Elektrik nedir?" | Temel | Teorik | Kolay | 5 | Düzenle, Sil
```

### 5.2 Soru Kategorileri

```
Meslek: Elektrikçi

Kategoriler:
├─ Temel Elektrik (45 soru)
├─ Devre Analizi (32 soru)
├─ Güvenlik (28 soru)
├─ Hesaplamalar (35 soru)
└─ Praktik (50 soru)
```

### 5.3 Teorik Soru Formu

```
Kategori *              [Temel Elektrik ▼]
Soru Metni *            [____________________]
                        [____________________]

Soru Tipi *             [Çoktan Seçmeli ▼]

Seçenekler:
( ) A) Seçenek 1
( ) B) Seçenek 2 ✓ (Doğru)
( ) C) Seçenek 3
( ) D) Seçenek 4

Zorluk *                [Kolay] [Orta] [Zor]
Puan                    [1]

[Kaydet] [Taslak] [İptal]
```

### 5.4 Performans Soru Formu

```
Kategori *              [Praktik Beceri ▼]
Görev Adı *             [____________________]
Açıklama *              [____________________]
                        [____________________]

Beklenen Sonuç:         [____________________]

Kontrol Listeleri:
☑ Güvenlik Tedbirleri
☑ Doğru Teknik
☑ Sonuç Doğruluğu
☑ Zaman Yönetimi

[Kaydet] [İptal]
```

---

## 6️⃣ SINAVLAR (Examination Management)

### Amaç
Sınavları oluşturmak, uygulamak ve sonuçlandırmak.

### 6.1 Sınav Listesi

```
Filtre: [Tüm] [Planlanmış] [Devam Ediyor] [Tamamlandı] [İptal]

Sınav | Meslek | Tarih | Katılımcı | Durum | İşlemler
------|--------|-------|-----------|--------|----------
SINAV-001 | Elektrikçi | 05.07.26 | 25 | Tamamlandı | Detay
```

### 6.2 Sınav Oluşturma Formu

**Adım 1: Genel Bilgiler**
```
Sınav Adı *             [____________________]
Meslek *                [Elektrikçi ▼]
Yeterlilik *            [Temel Elektrik ▼]
Sınav Tarihi *          [___/___/____] [HH:MM]
Sınav Süresi *          [120] dakika
Geçme Notu *            [60] puan

[Devam]
```

**Adım 2: Sorular**
```
Teorik Sorular:
┌─────────────────────────┐
│ ☑ Temel Elektrik (10)   │
│ ☑ Devre Analizi (15)    │
│ ☑ Güvenlik (10)         │
│ Toplam: 35 soru         │
└─────────────────────────┘

Performans Soruları:
┌─────────────────────────┐
│ ☑ Devre Kurma (3 görev) │
│ Toplam: 3 görev         │
└─────────────────────────┘

[Devam]
```

**Adım 3: Salon ve Gözetmen**
```
Sınav Salonu *          [Salon 1 ▼]
Gözetmenler:
[+ Gözetmen Ekle]
- Mehmet Yılmaz (Başgözetmen)
- Fatma Kara

[Tamamla]
```

### 6.3 Sınav Detay Ekranı

#### Sekmeler:
1. **Genel Bilgiler**
2. **Sorular** (Ön izleme)
3. **Katılımcılar**
4. **Sonuçlar**
5. **Değerlendirmeler**

#### 6.3.1 Katılımcılar Sekmesi
```
Durum Filtresi: [Tüm] [Davetli] [Katıldı] [Devamsız]

Ad Soyad | Meslek | Durum | Puan | İşlemler
---------|--------|-------|------|----------
Ahmet Y. | Elektrikçi | Katıldı | 85 | Detay
Fatma K. | Elektrikçi | Devamsız | - | Detay
```

#### 6.3.2 Sonuçlar Sekmesi
```
Toplam Katılımcı: 25
Başarılı: 18 (72%)
Başarısız: 7 (28%)

Ortalama Puan: 78.4
En Yüksek: 95
En Düşük: 42

[Detaylı Rapor] [Excel] [PDF]
```

---

## 7️⃣ PERFORMANS (Performance Evaluation)

### Amaç
Adayların işyerinde performansını değerlendirmek.

### 7.1 Değerlendirme Listesi

```
Filtre: [Tüm] [Başlamış] [Bekleniyor] [Tamamlandı]

Aday | Meslek | Başlangıç | Puan | Durum | İşlemler
-----|--------|-----------|------|--------|----------
Ahmet Y. | Elektrikçi | 06.07 | 92 | Tamamlandı | Detay
```

### 7.2 Değerlendirme Formu

```
📋 Performans Değerlendirmesi
Aday: Ahmet Yılmaz
Meslek: Elektrikçi
Başlangıç: 06.07.2026

Kontrol Listesi: [Elektrikçi Performans Listesi ▼]

Değerlendirmeler:
┌──────────────────────────────────────┐
│ ☑ 1. Güvenlik Tedbirleri              │
│    ( ) Evet  ( ) Hayır  ( ) Kısmen   │
│    Not: ___________________________   │
│                                      │
│ ☑ 2. Doğru Teknik Kullanımı          │
│    ( ) Evet  ( ) Hayır  ( ) Kısmen   │
│    Not: ___________________________   │
│                                      │
│ ☑ 3. Zaman Yönetimi                  │
│    ( ) Evet  ( ) Hayır  ( ) Kısmen   │
│    Not: ___________________________   │
│                                      │
└──────────────────────────────────────┘

Final Puan: [___] / 100

[Kaydet] [Gönder] [Taslak]
```

### 7.3 Kontrol Listeleri

```
Elektrikçi Performans Listesi (24 madde):

Kategori: Teknik Yetkinlik (8 madde)
├─ Güvenlik Tedbirleri
├─ Doğru Teknik
├─ Kalite Kontrol
└─ ...

Kategori: İş Güvenliği (6 madde)
├─ KKE Kullanımı
├─ İşyeri Düzeni
└─ ...

Kategori: Sosyal Beceriler (5 madde)
├─ Müşteri İlişkileri
├─ Takım Çalışması
└─ ...

Kategori: Yönetim (5 madde)
├─ Zaman Yönetimi
├─ Kaynak Yönetimi
└─ ...
```

---

## 8️⃣ BELGELENDİRME (Certification)

### Amaç
Başarılı adaylara sertifika düzenlemek.

### 8.1 Belgelendirme Listesi

```
Filtre: [Tüm] [Taslak] [Aktif] [Yenileme Beklemede] [İptal]

Sertifika No | Aday | Meslek | Düzenlenme | Bitiş | Durum | İşlemler
-------------|------|--------|-----------|-------|--------|----------
SER-2026-001 | Ahmet Y. | Elektrikçi | 07.07 | 07.07.2029 | Aktif | Detay
```

### 8.2 Sertifika Oluşturma

```
📄 Yeni Sertifika

Aday *                  [Ahmet Yılmaz ▼]
Meslek *                [Elektrikçi]
Yeterlilik *            [Temel Elektrik ▼]
Geçerlilik Süresi *     [3] Yıl
Düzenlenme Tarihi *     [08.07.2026]
Sertifika Şablonu *     [Standart ▼]

Notlar:                 [___________________]

[Oluştur] [Taslak] [İptal]
```

### 8.3 Sertifika Detay

```
🏆 Sertifika Detayları

Sertifika No: SER-2026-001
Aday: Ahmet Yılmaz
Meslek: Elektrikçi
Yeterlilik: Temel Elektrik

Düzenlenme: 08.07.2026
Geçerlilik: 08.07.2029

Durum: Aktif

[İndir PDF] [Yazdır] [Yenile] [İptal Et] [Paylaş]
```

---

## 9️⃣ BELGELER (Documents)

### Amaç
Sertifika şablonlarını ve PDF çıktılarını yönetmek.

### 9.1 Şablonlar

```
Şablon Adı | Meslek | Türü | İşlemler
-----------|--------|------|----------
Standart Sertifika | Tüm | Sertifika | Düzenle, Önizle
Başarı Belgesi | Tüm | Belge | Düzenle, Önizle
```

### 9.2 Şablon Düzenleyici

```
📋 Şablon Düzenle: Standart Sertifika

WYSIWYG Editor:
┌───────────────────────────┐
│ [B] [I] [U] [Link] [Image]│
├───────────────────────────┤
│                           │
│   MİLLİ YETERLİLİKLER     │
│      KORUMAYETİ           │
│                           │
│  Bu belge ile {{ADAY_AD}} │
│  {{MESLEK}} yeterlilikle  │
│  belgelendirilmiştir.     │
│                           │
│  Düzenlenme: {{TARIH}}    │
│                           │
└───────────────────────────┘

Kullanılabilir Değişkenler:
- {{ADAY_AD}}
- {{ADAY_SOYAD}}
- {{MESLEK}}
- {{YETERLILIK}}
- {{TARIH}}
- {{SERTIFIKA_NO}}

[Kaydet] [Önizle] [İptal]
```

---

## 🔟 RAPORLAR (Reports)

### Amaç
Sistem üzerindeki tüm verileri analiz etmek ve raporlamak.

### 10.1 Rapor Türleri

```
📊 Mevcut Raporlar:

1. Aday Raporu
   ├─ Toplam Adaylar
   ├─ Meslek Dağılımı
   ├─ Durum Dağılımı
   └─ Aylık Trend

2. Sınav Raporu
   ├─ Sınav Sonuçları
   ├─ Başarı Oranları
   ├─ Kategoriye Göre Başarı
   └─ Zorluk Analizi

3. Performans Raporu
   ├─ Performans Dağılımı
   ├─ Kategoriye Göre Başarı
   └─ Değerlendiriciye Göre

4. Belgelendirme Raporu
   ├─ Verilen Sertifikalar
   ├─ Aktif Sertifikalar
   ├─ Bitiş Yaklaşan
   └─ İptal Edilen

5. Mali Rapor
   ├─ İşlem Sayısı
   ├─ Ücret Toplamı
   └─ Firma Analizi

6. Sistem Raporu
   ├─ Kullanıcı Aktivitesi
   ├─ İşlem Logları
   └─ Performans Metrikleri
```

### 10.2 Rapor Oluşturucu

```
📊 Rapor Oluştur

Rapor Türü *            [Aday Raporu ▼]

Filtreler:
Meslek                  [Elektrikçi ▼]
Tarih Aralığı           [01.01.2026] - [08.07.2026]
Durum                   [Sertifikalı ▼]

Gösterimler:
☑ Grafik (Line Chart)
☑ Tablo
☑ Özet İstatistikler

Çıktı Formatı *         [PDF ▼] [Excel] [CSV]

[Oluştur] [İptal]
```

---

## 1️⃣1️⃣ KULLANICILAR (User Management)

### Amaç
Sistem kullanıcılarını ve rollerini yönetmek.

### 11.1 Kullanıcı Listesi

```
Filtre: [Tüm] [Aktif] [Pasif] [Admin]

Ad Soyad | E-posta | Rol | Durum | Son Giriş | İşlemler
---------|---------|-----|--------|-----------|----------
Mehmet A. | mehmet@.. | Yönetici | Aktif | 08.07.2026 | Düzenle, Sil
```

### 11.2 Kullanıcı Formu

```
Ad *                    [Mehmet]
Soyad *                 [Yılmaz]
E-posta *               [mehmet@example.com]
Telefon                 [5551234567]
Rol *                   [Yönetici ▼]

Birim (Opsiyonel)       [İstanbul Merkez ▼]

Durum *                 [Aktif] [Pasif]

Şifre                   [Generate] [Kendi Şifresi]

Yetkiler:
☑ Aday Görebilir
☑ Aday Ekleyebilir
☑ Aday Silebilir
☑ Sınav Oluşturabilir
☑ Sertifika Verebilir

[Kaydet] [İptal]
```

### 11.3 Rol Yönetimi

```
Roller:

1. Sistem Yöneticisi
   ├─ Tüm modüller
   ├─ Kullanıcı yönetimi
   └─ Sistem ayarları

2. MYK Yöneticisi
   ├─ Tüm modüller
   ├─ Raporlar
   └─ Belgelendirme

3. Eğitmen
   ├─ Sorular
   ├─ Sınavlar
   └─ Raporlar (Kısıtlı)

4. Değerlendirici
   ├─ Performans değerlendirmesi
   └─ Raporlar (Kendi değerlendirmeleri)

5. Firma Temsilcisi
   ├─ Aday kaydı (Kendi firmasının)
   ├─ Başvuru
   └─ Raporlar (Kısıtlı)

6. Aday
   ├─ Kendi bilgilerini görebilir
   ├─ Sınavlara katılabilir
   └─ Sertifikalarını indirebilir
```

---

## 1️⃣2️⃣ AYARLAR (Settings)

### Amaç
Sistem konfigürasyonunu yönetmek.

### 12.1 Genel Ayarlar

```
⚙️ Sistem Ayarları

Temel Ayarlar:
Sistem Adı:             [VOC Tester]
Kurumun Adı:            [MYK]
Logo                    [Dosya Seç]

E-posta Ayarları:
SMTP Sunucusu:          [mail.example.com]
SMTP Portu:             [587]
SMTP Kullanıcı:         [user@example.com]
SMTP Şifre:             [••••••••••]
Gönderici Adresi:       [noreply@example.com]

Sınav Ayarları:
Varsayılan Sınav Süresi: [120] dakika
Varsayılan Geçme Notu:   [60] puan
Maksimum Deneme:         [3]
Bekleme Süresi:          [30] gün

Dosya Yükleme Ayarları:
Max Dosya Boyutu:        [10] MB
İzin Verilen Formatlar:  [PDF, JPG, PNG]
Virüs Taraması:          [✓ Aktif]

[Kaydet] [Varsayılana Dön]
```

### 12.2 E-posta Şablonları

```
Şablon Adı | Konu | İşlemler
-----------|------|----------
Aday Kaydı Onayı | Kayıt Başarılı | Düzenle, Önizle
Sınav Davetiyesi | Sınav Tarihi | Düzenle, Önizle
```

### 12.3 Yetki Matrisi

```
Rol / Modül | Aday | Firma | Sınav | Perf. | Sertifika
------------|------|-------|-------|-------|----------
Admin | R/W | R/W | R/W | R/W | R/W
Yönetici | R/W | R/W | R/W | R/W | R/W
Eğitmen | R | - | R/W | - | R
Değerlendirici | R | - | - | R/W | -
Firma Rep. | R/W* | R | - | - | R*
Aday | R | - | R | R | R
```

---

**Son güncelleme:** 08.07.2026