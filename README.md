# Dolap Atölyesi

Telefon tarayıcısında çalışan 2D dolap tasarım aracı. Tek dosya, bağımlılık yok,
sunucu yok — çizim `<canvas>`, tasarım tarayıcıda (`localStorage`) saklanıyor.

**→ https://ozergul.dev/dolap-atolyesi/**

## Ne yapıyor

- **Önden görünüş**: iki parmakla yakınlaş, boşluğu sürükleyerek gez, çift dokunuşla sığdır.
- **Doğrudan düzenleme**: rafa/askıya/çekmeceye dokun ve parmakla taşı (10 mm'ye oturur);
  dikmeyi yana sürükle, iki bölme birlikte değişir, toplam en sabit kalır.
- **Kesim listesi**: gövde, raf, çekmece, kapak, arkalık + donatı (menteşe adedi kapak
  boyundan, ray boyu derinlikten türüyor). Altında m², kenar bandı metresi, tahmini
  plaka sayısı ve kaba malzeme maliyeti. Kopyala / CSV.
- **Kontrol**: 18 mm'de 800 mm'yi geçen raf açıklığı, 900 mm'yi geçen askı borusu,
  1000 mm'nin altında kalan askı yüksekliği, 550 mm'nin altında derinlik, 1400 mm'nin
  üstünde çekmece, 2600 mm'yi geçen gövde — hepsi anında uyarı olarak çıkıyor.
- **Rastgele üret**: 5–18 yaş (ya da yetişkin) seç, kullanışlı bir varyant üretsin.
  Yaş sadece etiket değil — çocuğun **erişim yüksekliği** (boy × 1.15) hesaplanıyor,
  askı borusu, çekmece ve günlük raflar o çizginin altına kuruluyor, üstü mevsimlik
  saklamaya kalıyor. Çizimde erişim çizgisi ve o yaşın boyunda siluet görünüyor.
  Uyarı eşikleri de yaşa göre kayıyor: 8 yaşın gömleği 540 mm, ondan 1000 mm askı
  yüksekliği istemek yanlış uyarı olurdu.
- **Cam kapak**: her bölmede ayrı açılıyor. Kesim listesinde 18 mm panel değil,
  40 mm alüminyum profil (metre) + 4 mm temperli cam olarak çıkıyor; kenar bandına
  girmiyor. Çocuk dolabında cam seçilirse temperli cam uyarısı düşüyor.
- Yedi şablon, geri/ileri al, otomatik kayıt, açık + koyu tema.

## Varsayımlar

Kapaklar tam üstten kapaklı ve 3 mm derzli; çekmeceler her yana 13 mm ray paylı.
Plaka sayısı %18 fire payıyla kabadır — kesim optimizasyonu değildir.
Gövde kalınlığı, arkalık, kaide, raf geri çekmesi, plaka ölçüsü ve fiyatlar
Ayarlar'dan değiştirilir.

## Geliştirme

Derleme adımı yok. `index.html` tek başına açılır; yerelde:

```sh
python3 -m http.server 8000
```

Yazı tipleri Google Fonts'tan geliyor (Archivo, IBM Plex Sans/Mono); bağlantı yoksa
sistem yazı tipine düşer, yerleşim bozulmaz.
