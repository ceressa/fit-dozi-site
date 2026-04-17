# fit-dozi-site

Static landing + legal pages for **Fit Dozi** iOS app, hosted on
GitHub Pages at `https://fit.dozi.app`.

Content is plain HTML + inline CSS, no build step. Edit files directly
and push.

## Files

| File | What it is | Linked from |
|---|---|---|
| `index.html` | Landing page | root |
| `privacy.html` | Privacy Policy — required by App Store | `/privacy.html` |
| `terms.html` | Terms of Service | `/terms.html` |
| `CNAME` | Custom domain binding for GitHub Pages | — |

## Setup (tek seferlik)

### 1. Repo'yu GitHub'a push et

```bash
cd C:/Users/Ufuk/AndroidStudioProjects/fit-dozi-site
git init
git add -A
git commit -m "Initial: landing + privacy + terms"
git branch -M main
git remote add origin https://github.com/ceressa/fit-dozi-site.git
git push -u origin main
```

> Önce https://github.com/new adresinden `fit-dozi-site` adıyla **public**
> repo aç (public zorunlu — GitHub Pages free tier private repo'ları
> host etmiyor).

### 2. GitHub Pages'i aç

`fit-dozi-site` repo'da:

1. **Settings → Pages**
2. **Source**: Deploy from a branch
3. **Branch**: `main` · **folder**: `/` (root)
4. **Save**

~1-2 dk sonra sayfa şu adreste çalışır:
`https://ceressa.github.io/fit-dozi-site/`

### 3. Custom domain (fit.dozi.app) bağla

**GitHub Pages settings**'te aynı sayfada:
- **Custom domain**: `fit.dozi.app` → Save
- `Enforce HTTPS` — henüz tıklanamayabilir, DNS propagate olana kadar bekle

**Google Workspace / dozi.app DNS kayıtlarında:**

| Type | Host | Value | TTL |
|---|---|---|---|
| CNAME | `fit` | `ceressa.github.io.` | 3600 (default) |

> Nokta (`.`) sonundaki önemli — tam FQDN olduğunu belirtir.

### 4. Bekle, doğrula

- DNS propagasyonu: 5-60 dk
- GitHub Pages TLS sertifikası: DNS propagate olduktan sonra ~30 dk otomatik
- `https://fit.dozi.app` → landing açılır → privacy/terms linkleri çalışır

### 5. App Store Connect'e URL'i gir

App Store Connect → Fit Dozi → App Information → **Privacy Policy URL**:
```
https://fit.dozi.app/privacy.html
```

## Güncelleme

Privacy policy veya landing page değişirse:
```bash
# Düzenle
git add -A
git commit -m "Update privacy: added X"
git push
```

GitHub Pages ~1-2 dk içinde otomatik yayınlar, cache invalidation manuel.

## Notlar

- `info@dozi.app` email'i privacy + terms + landing'de contact olarak geçiyor
  — bu adres Google Workspace'te aktif mi teyit et
- Site içeriği minimal legal-compliant seviyede tutuldu (Apple approval odaklı).
  Pazarlama sitesi olarak gelecekte genişletilebilir.
- 4 dilli (tr/en/de/es) versiyonlar henüz yok. Apple öncelikli dilde
  (Türkçe) kabul ediyor; diğer diller sonraki phase.
