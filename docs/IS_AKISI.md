# İş Akışı ve Süreçler

## 📊 Genel İş Akışı

```
┌─────────────┐
│   ADAY      │ (Candidate Registration)
│ (Adaylar)   │
└──────┬──────┘
       │
       ▼
┌─────────────────┐
│  BAŞVURU        │ (Application)
│ (Adaylar Modülü)│
└──────┬──────────┘
       │
       ▼
┌──────────────────┐
│   SINAVLAR       │ (Examination)
│ (Sınav Yönetimi) │
└──────┬───────────┘
       │
       ▼
┌────────────────────────┐
│   PERFORMANS           │ (Performance Evaluation)
│ (Performans Değerleme) │
└──────┬─────────────────┘
       │
       ▼
┌──────────────────┐
│   KARAR          │ (Decision)
│ (Raporlama)      │
└──────┬───────────┘
       │
       ▼
┌────────────────────────────┐
│   BELGELENDİRME            │ (Certification)
│ (Belgelendirme Yönetimi)   │
└────────────────────────────┘
```

---

## 🎯 Detaylı Modül İş Akışları

### 1️⃣ ADAY YÖNETİMİ (Candidate Management)

#### 1.1 Aday Kaydı Oluşturma

```
Kullanıcı: Firma Temsilcisi / Yönetici

Adımlar:
1. "Adaylar" modülüne gir
2. "Yeni Aday" butonuna tıkla
3. Formu doldur:
   - Kişisel Bilgiler (Ad, Soyad, TC No, Doğum Tarihi)
   - İletişim Bilgileri (E-posta, Telefon, Adres)
   - Eğitim Bilgileri (Okul, Mezuniyet Tarihi)
   - Meslek Seçimi
4. "Kaydet" butonuna tıkla
5. Sistem: Aday ID oluştur
6. Sistem: Onay e-postası gönder
7. Durum: "Yeni Kayıt" → "Beklemede"
```

**Validasyonlar:**
- TC No benzersiz olmalı
- E-posta formatı doğru olmalı
- Zorunlu alanlar doldurulmalı
- Minimum yaş kontrolü

#### 1.2 Aday Bilgisi Güncelleme

```
Kullanıcı: Aday / Firma Temsilcisi

Adımlar:
1. Aday listesinden adayı bul (filtre/arama)
2. Aday detaylarını aç
3. "Düzenle" butonuna tıkla
4. Bilgileri güncelle
5. "Kaydet" butonuna tıkla
6. Sistem: Değişiklikleri logla
7. Sistem: Başarı mesajı göster
```

**Loglama:**
- Kimin tarafından değiştirildiği
- Ne değiştirildiği
- Değişim tarihi ve saati

#### 1.3 Aday Belgesi Yükleme

```
Kullanıcı: Aday / Firma Temsilcisi

Adımlar:
1. Aday detaylarını aç
2. "Belgeler" sekmesine git
3. "Belge Yükle" butonuna tıkla
4. Belge türü seç (Diploma, Sertifika, CV vb.)
5. Dosyayı seç (PDF, JPG, PNG)
6. "Yükle" butonuna tıkla
7. Sistem: Dosyayı valide et
8. Sistem: Virüs taraması yap
9. Sistem: Depolama alanına kaydet
10. Sistem: Başarı mesajı göster
```

**Kısıtlamalar:**
- Max dosya boyutu: 10MB
- İzin verilen formatlar: PDF, JPG, PNG, DOC
- Virüs taraması zorunlu

---

### 2️⃣ BAŞVURU (Application Process)

#### 2.1 Başvuru Oluşturma

```
Kullanıcı: Firma Temsilcisi / Yönetici

Adımlar:
1. Aday detaylarını aç
2. "Başvurular" sekmesine git
3. "Yeni Başvuru" butonuna tıkla
4. Formu doldur:
   - Başvuru Tarihi
   - Başvuru Türü (İlk / Yenileme)
   - Yeterlilik Seçimi
   - Birim Seçimi
5. "Gönder" butonuna tıkla
6. Sistem: Başvuruyu kaydet
7. Sistem: Başvuru No oluştur
8. Sistem: Onay e-postası gönder
9. Durum: "Yeni Başvuru" → "Kabul Beklemede"
```

#### 2.2 Başvuru Onaylama

```
Kullanıcı: MYK Yöneticisi

Adımlar:
1. "Başvurular" listesine git
2. Filtrele: Durum = "Kabul Beklemede"
3. Başvuruyu seç
4. Detayları incele
5. Belgeler eki kontrol et
6. "Onayla" veya "Reddet" butonuna tıkla
7. Sistem: Durumu güncelle
8. Sistem: Aday'a bildirim gönder
9. Eğer Onayla:
   - Durum: "Onaylandı"
   - Sınava kaydı otomatik başlat
10. Eğer Reddet:
    - Durum: "Reddedildi"
    - Red nedeni belirtilmeli
```

---

### 3️⃣ SINAV YÖNETİMİ (Examination Management)

#### 3.1 Sınav Oluşturma

```
Kullanıcı: MYK Yöneticisi / Eğitmen

Adımlar:
1. "Sınavlar" modülüne git
2. "Yeni Sınav" butonuna tıkla
3. Formu doldur:
   - Sınav Adı
   - Meslek / Yeterlilik
   - Sınav Tarihi ve Saati
   - Sınav Yeri (Salon)
   - Sorular (Teorik + Performans)
   - Sınav Süresi
   - Geçme Notu (Min puan)
4. "Kaydet" butonuna tıkla
5. Sistem: Sınav ID oluştur
6. Durum: "Taslak" → "Hazır"
```

#### 3.2 Sınav Katılımcı Ekleme

```
Kullanıcı: Gözetmen / MYK Yöneticisi

Adımlar:
1. Sınav detaylarını aç
2. "Katılımcılar" sekmesine git
3. "Katılımcı Ekle" butonuna tıkla
4. Onaylanmış adayları listeden seç
5. "Ekle" butonuna tıkla
6. Sistem: Katılımcıyı kaydet
7. Sistem: Sınav e-postası gönder
8. Katılımcı Durumu: "Davetli"
```

#### 3.3 Sınav Uygulaması

```
Kullanıcı: Aday (Sistem üzerinden test)

Adımlar:
1. Sınav saatinde sisteme gir
2. "Sınavlarım" sekmesine git
3. Sınava başla
4. Soruları cevapla (Teorik)
5. Performans görevini tamamla
6. "Bitir" butonuna tıkla
7. Sistem: Yanıtları kaydet
8. Sistem: Otomatik puanlama (Teorik)
9. Durum: "Tamamlandı"

Kullanıcı: Değerlendirici (Performans Puanlama)

Adımlar:
1. "Sınavlar" → "Değerlendirme Beklemede" filtresine git
2. Sınavı seç
3. Aday performansını incele (Video/Not)
4. Puanlama formunu doldur
5. "Gönder" butonuna tıkla
6. Sistem: Final puanı hesapla
7. Sistem: Başarı/Başarısızlık belirle
```

#### 3.4 Sınav Sonuçları

```
Sistem Otomatik:
1. Tüm puanları topla
2. Geçme notunun üstünde mi kontrol et
3. Sonuç belirle: "BAŞARILI" / "BAŞARISIZ"
4. Adaya sonuç e-postası gönder
5. Durum: "Sonuçlandırıldı"
```

---

### 4️⃣ PERFORMANS DEĞERLENDİRMESİ (Performance Evaluation)

#### 4.1 Performans Değerlendirmesi Başlatma

```
Kullanıcı: Firma Yöneticisi

Adımlar:
1. Başarılı adayların listesine git
2. Aday seç
3. "Performans Değerlendirmesi" sekmesine git
4. "Yeni Değerlendirme" butonuna tıkla
5. Formu doldur:
   - Değerlendirme Tarihi
   - Değerlendiriciler (seç)
   - Kontrol Listeleri (seç)
6. "Başlat" butonuna tıkla
7. Sistem: Değerlendiricilere bildirim gönder
8. Durum: "Başlamış"
```

#### 4.2 Performans Değerlendirmesi Yapma

```
Kullanıcı: Değerlendirici (İşyerinde gözlem)

Adımlar:
1. "Performans Değerlendirmeleri" listesine git
2. Beklemede olanları filtrele
3. Değerlendirmeyi seç
4. Kontrol listesini aç
5. Her madde için:
   - Gözlem yap
   - "Evet/Hayır/Kısmen" seç
   - Not ekle (isteğe bağlı)
6. Puanlama yap (0-100)
7. "Kaydet" butonuna tıkla
8. Sistem: Puan hesapla
9. Durum: "Tamamlandı"
```

**Kontrol Listeleri:**
- Teknik Yetkinlik
- İş Güvenliği
- Müşteri İlişkileri
- Zaman Yönetimi
- Takım Çalışması
- Inovasyonu Çalışması

---

### 5️⃣ KARAR SÜRECİ (Decision Making)

#### 5.1 Nihai Karar Verme

```
Kullanıcı: MYK Yöneticisi

Adımlar:
1. Değerlendirme tamamlanan adayları git
2. Rapor oluştur (otomatik)
3. Detayları incele:
   - Sınav Puanı
   - Performans Puanı
   - Final Puan Hesaplaması
4. "Karar Ver" butonuna tıkla
5. Seç:
   - "Belgelendirme Yapılsın"
   - "Başarısız - Yeniden Sınava Gir"
   - "Reddedildi - İş Akışını Sonlandır"
6. "Kaydet" butonuna tıkla
7. Sistem: Adaya bildirim gönder
8. Sistem: İş akışını devam ettir
```

---

### 6️⃣ BELGELENDİRME (Certification)

#### 6.1 Sertifika Oluşturma

```
Kullanıcı: Belgelendirme Sorumlusu

Adımlar:
1. "Belgelendirme" modülüne git
2. "Yeni Belge" butonuna tıkla
3. Adayı seç (Belgelendirmeye Uygun olanlar)
4. Formu doldur:
   - Belge Türü
   - Yeterlilik
   - Geçerlilik Süresi
   - Düzenlenme Tarihi
5. "Oluştur" butonuna tıkla
6. Sistem: Belge No oluştur
7. Sistem: PDF belge oluştur
8. Sistem: Adaya e-posta ile gönder
9. Durum: "Aktif"
```

#### 6.2 Sertifika Yenileme

```
Kullanıcı: Aday / Firma Temsilcisi

Sertifika bitiş tarihi 30 gün kala:
1. Sistem: Aday'a hatırlatma e-postası gönder
2. Aday: "Yenileme Başvurusu" yapar
3. Sistem: "Yenileme Beklemede" durumuna geçer
4. Süreç: Sınav / Performans tekrarlanır
5. Başarılı olursa: Yeni sertifika düzenlenir

Kullanıcı: Belgelendirme Sorumlusu

Adımlar:
1. Yenileme Başvurusu Beklemedileri görüntüle
2. Başvuruyu seç
3. "Yenile" butonuna tıkla
4. Yeni belge oluştur (eski belge arşivlenir)
5. Sistem: Yeni belge numarası oluştur
6. Sistem: Adaya gönder
```

#### 6.3 Sertifika İptal

```
Kullanıcı: MYK Yöneticisi / Belgelendirme Sorumlusu

Adımlar:
1. İptal edilecek sertifikayı bul
2. "İptal Et" butonuna tıkla
3. İptal Nedeni seç:
   - Adli Karar
   - Etik İhlali
   - Hilenin Tespit Edilmesi
   - Diğer
4. Açıklama ekle
5. "Onayla" butonuna tıkla
6. Sistem: Sertifikayı "İptal Edildi" olarak işaretle
7. Sistem: Arşiv'e taşı
8. Sistem: Adaya bildirim gönder
9. Sistem: Loglama yap
```

---

## 📋 Paralel Süreçler

### Adayın Birden Fazla Yeterlilik Almak İstediği Durumda

```
Aday: Adı Yusuf
Yeterlilikler: [Elektrikçi, Tesisatçı, Boyacı]

İş Akışı:
1. Elektrikçi sertifikasını alır
2. Tesisatçı için başvuru yapar (Paralel başlayabilir)
3. Her yeterlilik için ayrı sınav ve değerlendirme
4. Her biri tamamlanır tamamlanmaz sertifika verilir
5. Tüm yeterlilikler için ayrı dosya tutulur
```

### Sınavı Başarısız Adayın Tekrar Sınava Girmesi

```
Aday: İlk Sınavda Başarısız

Adımlar:
1. Sistem: 30 gün bekleme süresi koyar
2. 30 gün sonra: Adaya yeniden başvuru hakkı verilir
3. Aday: Yeniden başvuru yapar
4. Durum: "Yeniden Başvuru"
5. Süreç: Sıfırdan başlangıç (1. Başvuru adımından)
6. Maksimum deneme: 3 kez
7. 3 kez başarısız: İş akışı sonlandırılır
```

---

## 🔄 Durum Akışları

### Aday Durumları
```
YENİ KAYIT
    ↓
BEKLEMEDE (Başvuru bekleniyor)
    ↓
BAŞVURU YAPILDI
    ├─→ ONAY BEKLEMEDE
    │       ├─→ ONAYLANDI
    │       │       ↓
    │       │   SINAVA KATILACAK
    │       │       ↓
    │       │   SINAVDA
    │       │       ├─→ BAŞARILI
    │       │       │       ↓
    │       │       │   PERFORMANS DEĞERLENDİRMESİ
    │       │       │       ↓
    │       │       │   BELGELENDİRME
    │       │       │       ↓
    │       │       │   SERTİFİKALI
    │       │       │
    │       │       └─→ BAŞARISIZ
    │       │               ↓
    │       │           YENİDEN SINAVA KATILACAK (Max 3)
    │       │               ↓
    │       │           [BAŞARILI veya TERMİNATE]
    │       │
    │       └─→ REDDEDİLDİ
    │
    └─→ İPTAL
```

### Başvuru Durumları
```
YENİ BAŞVURU
    ↓
KABUL BEKLEMEDE
    ├─→ ONAYLANDI → SINAVDA → SONUÇLANDI
    └─→ REDDEDİLDİ → TERMİNATE
```

### Sertifika Durumları
```
AKTIF
    ├─→ YENİLENME AŞAMASINDA
    │       └─→ AKTIF (Yenilendi)
    │
    └─→ İPTAL EDİLDİ (Arşiv)
```

---

## 📧 Bildirim Türleri

### Otomatik E-posta Bildirimleri

| Olay | Alıcı | Mesaj |
|------|-------|-------|
| Aday kaydı yapıldı | Aday | Kayıt başarılı, sonraki adımlar |
| Başvuru onaylandı | Aday | Sınav tarihi ve saati |
| Sınav sonucu | Aday | Başarılı/Başarısız |
| Sertifika düzenlendi | Aday | Sertifika indirme linki |
| Sertifika sona eriyor | Aday | Yenileme hatırlatması (30 gün öncesi) |
| Başvuru reddedildi | Aday | Red nedeni ve başvuru hakkı |

---

## ⏰ Zaman Aşımları ve Hatırlatıcılar

| İşlem | Zaman Aşımı | Hatırlatma |
|--------|-----------|-----------|
| Başvuru Onay Bekleme | 7 gün | 3. gün |
| Sınava Kayıt | Sınav tarihine kadar | 1 gün öncesi |
| Performans Değerlendirme | 14 gün | 7. gün |
| Sertifika Bitişi | - | 30 gün öncesi |
| Başarısız Sınav (Tekrar hakkı) | 30 gün bekleme | Hemen sonra |

---

**Son güncelleme:** 08.07.2026