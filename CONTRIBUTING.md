# Katkı Rehberi

Projeye katkıda bulunmak için bu kuralları lütfen takip edin.

## 🎯 İş Akışı

### 1. Issue Açma

Yeni bir özellik veya hata bildirmeden önce:

1. Mevcut issueleri kontrol edin
2. Uygun şablonu seçin
3. Açıklayıcı başlık yazın
4. Detaylı açıklama sağlayın

### 2. Branch Oluşturma

```bash
# Develop branch'ından yeni branch oluşturun
git checkout develop
git pull origin develop
git checkout -b feature/kisa-aciklama

# Örnek branch isimleri:
# feature/dashboard-yenileme
# bugfix/login-hatası
# hotfix/performans-sorunu
```

### 3. Kod Yazma

- **Okunabilirlik**: Kod açık ve anlaşılır olmalı
- **Yorum**: Karmaşık kısımlara yorum ekleyin
- **Test**: Değişiklik için test yazın
- **Linting**: Stil kurallarına uyun

### 4. Commit İletileri

```
Başlık (50 karakter veya daha az)

Detaylı açıklama (70 karakter wrap)
- Neyi değiştirdiniz
- Neden değiştirdiniz
- Varsa ilgili issue numarası (#123)
```

**Başlık türleri:**
- `feat:` Yeni özellik
- `fix:` Hata düzeltmesi
- `docs:` Dokümantasyon
- `style:` Kod stili (noktalama, boşluk vb)
- `refactor:` Kod yeniden yapılandırması
- `test:` Test ekleme/düzeltme
- `chore:` Araç, bağımlılık güncellemesi

**Örneğin:**
```
feat: Dashboard'a performans widget'ı eklendi

- Haftalık sınav sayılarını gösteren widget
- Real-time veri güncellemesi
- Responsive tasarım
Closes #45
```

### 5. Pull Request

1. Değişikliklerinizi push edin
2. GitHub'da Pull Request oluşturun
3. PR şablonunu doldurun
4. En az bir review bekleyin
5. Merge edin

**PR Başlığı Formatı:**
```
[TÜR] Kısa açıklama (Closes #123)
```

**Örnekler:**
```
[FEATURE] Dashboard performans widget'ı (Closes #45)
[BUGFIX] Login sayfasında CSS hatası (Closes #67)
[DOCS] Kurulum rehberi güncellendi
```

---

## 📋 Kod Standartları

### Dosya Yapısı

```
src/
├── components/        # Tekrar kullanılabilir bileşenler
├── pages/            # Sayfa komponentleri
├── services/         # API çağrıları
├── utils/            # Yardımcı fonksiyonlar
├── styles/           # Stil dosyaları
├── hooks/            # Custom hooks
└── types/            # TypeScript türleri
```

### Adlandırma Kuralları

- **Dosyalar**: `camelCase.ts` veya `PascalCase.tsx`
- **Komponentler**: `PascalCase`
- **Fonksiyonlar**: `camelCase`
- **Sabitler**: `UPPER_SNAKE_CASE`
- **Private**: `_leadingUnderscore`

### Kod Örnekleri

```typescript
// ✅ İyi
interface UserRole {
  id: string;
  name: string;
  permissions: Permission[];
}

function getUserPermissions(userId: string): Promise<Permission[]> {
  // Açıklayıcı fonksiyon
  return apiService.get(`/users/${userId}/permissions`);
}

// ❌ Kötü
function get(u: string): any {
  return api.g(`/u/${u}/p`);
}
```

---

## 🧪 Testing

- Unit testler yazın
- İntegrasyon testlerini çalıştırın
- Test kapsamı en az %80 olmalı

```bash
npm test
npm run test:coverage
```

---

## 📚 Dokümantasyon

Yeni özellik eklerken:
- Kodu açıklayıcı yorumlar ekleyin
- Kullanım örneği verin
- İlgili README kısmını güncelleyin

---

## 🚫 Ne Yapılmamalı

- ❌ `main` branch'ına doğrudan push
- ❌ Node_modules veya `.env` commit'lemek
- ❌ Çok büyük PR'ler (>500 satır)
- ❌ Çalışmayan kod merge'lemek
- ❌ İş akışı veya menüyü değiştirmek

---

## ❓ Sorular

GitHub Discussions'da sorularınızı sorun.

Teşekkürler! 🙏