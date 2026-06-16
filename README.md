# DeepL Minimal

DeepL çeviri sayfasında yalnızca çeviri alanını kullanmak için Chrome eklentisi.

## Nasıl Çalışır

Eklenti `document_start` aşamasında devreye girer. Sayfa `/tr/translator` yolundaysa `main[data-layout-id="mainSection"]` seçicisiyle eşleşen çeviri bloğunu tam genişlikte tutar, diğer tüm DOM öğelerini CSS ile gizler. SPA navigasyonunu da yakalar: `history.pushState`, `replaceState`, `popstate` ve `hashchange` olaylarını dinleyerek URL değiştiğinde durumu günceller; `MutationObserver` ise dinamik yüklenen içerikleri takip eder.

## Dosya Yapısı

```
deepl-minimal/
├── manifest.json   # Manifest V3 tanımı, content script kaydı
└── content.js      # Tüm mantık bu tek dosyada
```

## Kurulum

1. Chrome'da `chrome://extensions` adresini aç.
2. Sağ üstten **Developer mode**'u aktif et.
3. **Load unpacked** butonuna tıkla.
4. `deepl-minimal` klasörünü seç.

## Kullanım

`https://www.deepl.com/tr/translator` adresini aç — eklenti otomatik olarak devreye girer, herhangi bir işlem gerekmez.

## Bakım Notu

DeepL arayüzü köklü bir değişiklik geçirirse `content.js` içindeki `KEEP_SELECTOR` sabitini güncellemek yeterlidir:

```js
const KEEP_SELECTOR = 'main[data-layout-id="mainSection"]';
```
