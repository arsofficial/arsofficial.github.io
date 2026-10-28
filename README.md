# Arş web (davet sayfası)

Bu klasör `<hesap>.github.io` adlı public GitHub reposuna olduğu gibi kopyalanır; GitHub Pages kökten yayınlar.

- `index.html` – kısa tanıtım + mağaza düğmeleri
- `davet/index.html` – `?kod=ABC123` (grup hatmi) ya da `?u=kullanici` (arkadaş): uygulama yüklüyse açar, yoksa mağazaya yönlendirir
- `.well-known/apple-app-site-association` – iOS evrensel link doğrulaması (takım YDV586RV75, com.arsapp.app). Uzantısız kalmalı.
- `.well-known/assetlinks.json` – Android app link doğrulaması. `PLAY_IMZA_SHA256_BURAYA` yerine Play Console → Test et ve yayınla → Uygulama bütünlüğü → Uygulama imzalama anahtarı sertifikası → SHA-256 (iki nokta ile ayrılmış, büyük harf).
- `.nojekyll` – Pages'in `.well-known` klasörünü atlamaması için şart.

Yayın: repo → Settings → Pages → Source: Deploy from a branch, Branch: main / (root). Birkaç dakika sonra
`https://<hesap>.github.io/.well-known/apple-app-site-association` adresi JSON döndürmeli.

Uygulama tarafı (app.json): `ios.associatedDomains: ["applinks:<hesap>.github.io"]` ve Android `intentFilters`
(autoVerify, https, host <hesap>.github.io, pathPrefix /davet); `src/lib/links.ts` içinde `DAVET_WEB`.
