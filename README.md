# Kampüs Etkinlikleri

Fakültedeki seminer, atölye, söyleşi ve yarışmaları tek yerden takip etmek için React + TypeScript + Vite ile geliştirilmiş bir uygulama.

Havva Nur Yanık · 2416501025
## Özellikler

- React Router ile 10 sayfa (route)
- Context API (`EventProvider` + `useEvents`) ile tüm sayfalar aynı etkinlik verisini kullanır; veriler `localStorage`'da saklanır
- Etkinlik ekleme, güncelleme ve silme; silmeden önce onay sorulur. Değişiklikler ana sayfa, liste ve detay sayfasında hemen görünür
- Başlık/açıklamada arama ve kategoriye göre filtreleme
- Form doğrulama: etkinlik formu, giriş, kayıt ve şifremi unuttum
- Mobil uyumlu tasarım

## Sayfalar

| Yol | Sayfa |
| --- | --- |
| `/` | Ana sayfa (yaklaşan 2 etkinlik) |
| `/etkinlikler` | Tüm etkinlikler, arama ve filtre |
| `/etkinlikler/:id` | Etkinlik detayı |
| `/yonetim` | Etkinlik yönetimi (düzenle / sil) |
| `/yonetim/ekle` | Etkinlik ekle |
| `/yonetim/guncelle/:id` | Etkinlik güncelle |
| `/giris` | Giriş yap |
| `/kayit` | Kayıt ol |
| `/sifremi-unuttum` | Şifremi unuttum |
| `*` | 404 sayfası |

## Repo yapısı

```
frontend/   React + TypeScript + Vite arayüzü (localhost:5173)
backend/    Node.js + Express REST API (localhost:3000)
README.md
```

Backend'in çalıştırma komutları, `PORT` değişkeni ve REST sözleşmesi: [backend/README.md](backend/README.md)

## Frontend klasör yapısı

```
frontend/src/
  components/
    events/   EventCard, EventList, EventFilter, EventDetail
    forms/    EventForm, FormField
    layout/   Header, Navigation, Footer, PageLayout, NotFoundBox
  context/    event-context, EventProvider, useEvents
  data/       başlangıç etkinlikleri
  pages/      10 sayfa bileşeni
  types/      tipler ve route yolları
  utils/      arama/filtre, sıralama, tarih biçimi, doğrulama
```

## Çalıştırma

Frontend:

```bash
cd frontend
npm install
npm run dev      # geliştirme sunucusu (http://localhost:5173)
npm run build    # üretim derlemesi
```

Backend:

```bash
cd backend
npm install
cp .env.example .env
npm run dev      # API (http://localhost:3000)
```

`vercel.json`, sayfa yenilendiğinde de route'ların çalışması için tüm istekleri `index.html`'e yönlendirir.

Sprint 5 yayını: https://sprint5-five.vercel.app
