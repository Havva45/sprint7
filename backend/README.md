# Kampüs Etkinlikleri API (backend)

Node.js + Express ile yazılmış REST API. Veriler şimdilik bellekte tutulur (sunucu yeniden başlayınca POST ile eklenenler kaybolur).

## Çalıştırma

```bash
cd backend
npm install
cp .env.example .env
npm run dev     # geliştirme (dosya değişince yeniden başlar)
npm start       # normal çalıştırma
```

API adresi: `http://localhost:3000`

## Ortam değişkenleri

| Değişken | Açıklama | Varsayılan |
| --- | --- | --- |
| `PORT` | Sunucunun dinlediği port | `3000` |

## REST sözleşmesi

| Method | Endpoint | Amaç | Başarılı | Hata | Durum |
| --- | --- | --- | --- | --- | --- |
| GET | `/health` | Sunucu ayakta mı? | 200 | — | Bu sprint |
| GET | `/events` | Listeyi getir (`?category=Atölye` isteğe bağlı) | 200 | — | Bu sprint |
| GET | `/events/:id` | Tek etkinlik | 200 | 404 | Bu sprint |
| POST | `/events` | Yeni etkinlik | 201 | 400 | Bu sprint |
| PATCH | `/events/:id` | Güncelle | 200 | 400, 404 | Sprint 9 |
| DELETE | `/events/:id` | Sil | 204 | 404 | Sprint 9 |

Status kodları: **200** tamam · **201** oluşturuldu · **204** içerik yok · **400** eksik/yanlış veri · **404** bulunamadı

Bütün hatalar aynı biçimde döner:

```json
{ "error": { "message": "Event not found" } }
```

POST için zorunlu alanlar: `title`, `category`, `date`.

## Postman

İstek koleksiyonu: `requests/kampus-api.json` (Postman'de **Import** ile açılabilir).
