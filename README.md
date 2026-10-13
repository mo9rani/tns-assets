# tns-assets

Images for **كويز المسلسلات التونسية** (`com.tunisianseries`).

The app never bundles these — it loads them at runtime through the jsDelivr
CDN, so adding content is a commit here, not an app update.

## Layout

```
questions/<series-slug>/<name>.webp   the still shown above each clue
avatars/<avatar-id>.webp              player avatars
series/<series-slug>.webp             series cover on the Play tab
```

`<series-slug>` and `<avatar-id>` must match the values seeded in the API.
Avatars in this repo, with the tier the API seeds them at:

| id | name | unlock |
|---|---|---|
| abouda | عبودة | free |
| hmouda | حمودة | free |
| kalthoum | كلثوم | free |
| rawdha | روضة | free |
| salih | صالح | level 3 |
| sboui | السبوعي | level 5 |
| slouma | سلومة | level 7 |
| hafa | حفّة | level 9 |
| blinta | بلينطة | level 12 |
| sid_ahmed | سيد أحمد | level 15 |
| sidi_daoud | سيدي داود | 5000 points |
| beji_matrix | الباجي ماتريكس | 12000 points |
| stich | ستيتش | rewarded ad |
| fouchika | فوشيكة | rewarded ad |
| slimen_labyedh | سليمان لأبيض | rewarded ad |

## URLs

Files are served through jsDelivr, not `raw.githubusercontent.com` — raw is not
a CDN, it rate-limits and has no edge caching:

```
https://cdn.jsdelivr.net/gh/mo9rani/tns-assets@main/questions/choufli-hal/q1.webp
https://cdn.jsdelivr.net/gh/mo9rani/tns-assets@main/avatars/ninja.webp
```

The repo must stay **public** for jsDelivr to serve it.

### Caching

jsDelivr caches `@main` aggressively (up to 7 days). **Replacing a file at the
same path will not update the app quickly.** To change an image, either:

- commit it under a new filename (preferred — the app reads paths from the
  database, so you just update the record), or
- pin a tag (`@v2`) and bump it when you publish a batch.

## Image guidelines

| Kind | Size | Notes |
|---|---|---|
| Question | 1080×1080 or 1080×1350 | Shown behind a bottom gradient; keep faces in the upper two-thirds |
| Avatar | 256×256 | Square, centred, readable at 42px |
| Series cover | 512×512 | Rendered at 92px in the series list |

Use `.webp` — roughly a third the size of JPEG at the same quality, which
matters on Tunisian mobile data.

## Rights

Stills from broadcast series are used here for a fan quiz. Prefer cropped or
stylised frames over clean full-frame captures, and remove anything a rights
holder objects to.
