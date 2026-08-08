# झाझवा पहाड़ बाबा मंदिर — PWA Web App

Yeh ek installable PWA (Progressive Web App) hai — mobile pe "app jaisa" install hota hai,
lekin andar se simple HTML/CSS/JS hai, isliye GitHub Pages par free host kar sakte ho.

## Folder me kya hai
```
index.html      -> Pura app (design + config sab isi file me hai)
manifest.json   -> PWA settings (app ka naam, color, icon)
sw.js           -> Offline kaam karne ke liye (service worker)
icons/          -> App icon (abhi placeholder hai — apna logo bhejo, replace kar denge)
images/         -> Hero slider photos + pandit photos (placeholder hain, replace karo)
```

## GitHub Pages par kaise daalein (step by step, mobile se)

1. GitHub app ya browser me apna repo kholo (naya banana ho to "New repository").
2. Is poore folder ke sab files upload karo (index.html, manifest.json, sw.js, icons/, images/)
   — GitHub web editor me "Add file -> Upload files" se seedha upload ho jayega.
3. Repo ke **Settings -> Pages** me jao.
4. "Branch" me `main` select karo, folder `/root` rakho, aur Save daba do.
5. 1-2 minute me link mil jayega: `https://yourusername.github.io/repo-name/`
6. Mobile Chrome me link kholo -> neeche "Add to Home Screen" / center popup se "Install" karo.

## Content edit kaise karein (sab kuch index.html ke andar hai)

`index.html` file kholo, andar `<script>` tag me sabse upar ek section hai jisme likha hai:

```
================  यहां से सारी जानकारी बदल सकते हैं (CONFIG)  ==========
```

Usi jagah ye sab cheezein change kar sakte ho — GitHub web editor (pencil ✏️ icon) se
mobile par bhi seedha edit ho jata hai:

| Kya change karna hai | Kaunsa CONFIG variable |
|---|---|
| Top scrolling festival naam patti | `TICKER_ITEMS` (list me jitne chaho utne items daal sakte ho) |
| Upar wali sliding photos | `HERO_IMAGES` (photo ka link ya `images/` folder ka file naam daalo) |
| Mandir/App ka naam | `APP_TITLE` |
| Pandit list (naam, photo, rating) | `PANDIT_LIST` |
| Pramukh Yajman (HED Member) list | `YAJMAN_LIST` |
| Kul daan / Total kharch ke number | `TOTAL_DONATION`, `TOTAL_EXPENSE` |
| Upcoming Events | `EVENTS` |
| Yajman Registration button ka Google Form | `GOOGLE_FORM_URL` |
| Support/Shikayat button (WhatsApp number) | `SUPPORT_LINK` |
| Footer text | `FOOTER_TEXT` |

### Photo kaise badlein
- Sabse aasan: apni photo `images/` folder me upload karo (jaise `images/hero-1.jpg` ko
  replace kar do same naam se) — code me kuch change karne ki zaroorat nahi.
- Ya phir photo kahin bhi (Google Drive share link, imgbb.com, ImgBB, ya GitHub ke images
  folder) upload karke uska **direct link** copy karo aur CONFIG me us jagah paste kar do.

### Google Form Registration
1. Google Form banao (Naam, Mobile, City, etc.).
2. Form ke upar-right "Send" button dabao -> link 🔗 icon -> link copy karo.
3. Usi link ko `GOOGLE_FORM_URL` variable me paste kar do.
4. "यजमान रजिस्ट्रेशन" button dabate hi form popup me khul jayega (app ke andar hi).

### Install popup (center screen)
- Jab koi user pehli baar site kholega, kuch second baad center me
  "ऐप इंस्टॉल करें" popup aayega, jisme:
  - **डाउनलोड/इंस्टॉल करें** button — app install karega
  - **✕ (cross)** ya **अभी नहीं** — jisko install nahi karna, wo band kar sakta hai
- Yeh popup Chrome/Android par best kaam karta hai (Safari/iOS me thoda alag behave karega,
  yeh normal hai — PWA install ka standard tarika hai).

## Logo
Abhi `icons/icon-192.png` aur `icons/icon-512.png` placeholder hain (maroon-gold circle).
Apna asli logo 512x512px (PNG, transparent ya solid background) bhejo — usi size me bana
kar yahi 2 files replace kar denge, ya khud bhi seedha `icons/` folder me upload kar sakte ho
(bas naam wahi rakhna: `icon-192.png` aur `icon-512.png`).

## ॐ Admin Panel (bina code chhue customize karo)

App ke footer ke neeche ek chhota **ॐ** symbol hai. Usko tap karo:

1. **PIN maangega** — default PIN hai `1234` (isko turant Admin Panel ke andar "🔒 Admin PIN badlein" section se change kar dena, taaki koi aur access na kar sake).
2. PIN daalte hi **Admin Panel** khul jayega, jahan se yeh sab kuch edit kar sakte ho:
   - Top scrolling patti
   - Sliding photos
   - Mandir/App ka naam
   - Pandit list
   - Pramukh Yajman list
   - Kul daan / Total kharch
   - Upcoming Events
   - Google Form link + WhatsApp support link
   - Footer text

### ⚠️ Zaroori baat samajh lo
- **"Save / Preview"** button dabane se changes turant dikhte hain, lekin **sirf usi mobile/browser
  me** jahan se aapne edit kiya (kyunki yeh ek static site hai, ismein koi central database nahi hai).
  Doosre logon ke phone par jo site khulegi, unhe purana/default content hi dikhega.
- Sabke liye (har visitor ke liye) hamesha ke liye change karna ho, to:
  1. Admin Panel me apni saari details bhar do
  2. **"कोड कॉपी करें"** button dabao — ek code block milega
  3. Us code ko copy karo
  4. GitHub par `index.html` file kholo (pencil ✏️ se edit mode), `DEFAULT_CONFIG = {...}` wala
     poora block dhundo, aur naye copied code se replace kar do
  5. Save/Commit kar do — ab yeh sabko dikhega

Isi tarah PIN bhi wahi rahega jab tak aap khud usse change na karo.

## Design theme
Maroon + Gold devotional theme, screenshot design ke mutabik banaya gaya hai. Rang badalne ho
to `index.html` ke `<style>` section me sabse upar `:root { --maroon:...; --gold:...; }`
variables hain, wahan se sab colors ek jagah se control hote hain.
