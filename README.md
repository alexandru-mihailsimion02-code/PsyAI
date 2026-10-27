# PsyAI — ghid tehnic

Construit pe același șablon ca PsyInsomnia (aceleași culori, fonturi Fraunces + Inter, structură și reguli de securitate).

| Fișier | Rol |
|---|---|
| `index.html` | Site-ul principal (HTML, CSS, JS și fonturi incluse; fără resurse de la terți) |
| `confidentialitate.html`, `termeni.html` | Pagini juridice |
| `404.html` | Pagina de eroare (GitHub Pages o folosește automat) |
| `.nojekyll` | Oprește procesarea Jekyll; trebuie să rămână |

## Publicare pe GitHub Pages
Încarcă toate fișierele la rădăcina depozitului, apoi *Settings → Pages → Deploy from a branch → main / (root)*. Pentru domeniu propriu: *Custom domain* și *Enforce HTTPS*.

## Testat
Testat în Chromium headless: 0 erori în consolă și 0 încălcări CSP pe toate paginile; fără depășiri orizontale la 23 de lățimi (320–1920 px); meniu, navigare, buton „sus”, bara informativă, trasee pliabile, FAQ, Resurse și linkuri directe; fără suprapuneri în hero la 22 de lățimi; contrast WCAG AA pe 129 de perechi de culori; site-ul rămâne utilizabil fără JavaScript. **Netestat:** dispozitive reale (iOS/Android) și linkurile externe live.

## Reguli la modificare
1. **După orice modificare a `<script>` din `index.html`, recalculează hash-ul din meta CSP** (`script-src 'sha256-…'`): sha256 în base64 al conținutului exact dintre `<script>` și `</script>`. Altfel browserul blochează scriptul (meniul mobil, mesajul informativ, butonul „sus”).
2. Fără scripturi, fonturi sau imagini de la alte domenii și fără atribute `onclick=`: CSP le blochează. Nu există formulare (`form-action 'none'`); lista de așteptare folosește linkuri `mailto:`.
3. `404.html` folosește linkuri absolute (`/`), deci funcționează corect pe un domeniu propriu sau pe `utilizator.github.io`; pe un proiect GitHub Pages (`utilizator.github.io/depozit/`) înlocuiește-le cu căi relative.
4. Singura cheie din localStorage este `psyai_notice_ok`.

## Lista de așteptare
Toate acțiunile de listă de așteptare (butonul din hero, banda de apel la acțiune, cardul din Contact și butonul „Vreau să fiu anunțat” de la fiecare curs) deschid WhatsApp către 0749255366, cu un mesaj pre-completat (la cursuri include numele cursului). Butoanele „Cere o ofertă” de la servicii și aplicații rămân pe email.

## Comunitate și Resurse
- Secțiunile `#comunitate` și `#resurse` urmează structura PsyInsomnia (patru carduri de comunitate, nota „Reguli simple”, resurse pliabile).
- **Linkuri reale:** grupul de Facebook și serverul de Discord duc direct la linkurile lor; cardul Facebook are și butonul „Pagina de Facebook”. În footer sunt Facebook (PsyAI Academy), LinkedIn (PsyAI Consulting), Discord și Linktree.
- Grupul de WhatsApp duce direct la invitația lui. **Încă fără link:** canalul de Telegram, al cărui buton deschide un mesaj WhatsApp către Alex. Când îl creezi, înlocuiește `href`-ul butonului `.btn.join` respectiv.
- **Discord:** verifică în Discord că invitația e setată să nu expire (implicit invitațiile expiră).
- Resursele sunt 4 linkuri oficiale; adaugă altele ca blocuri `<a class="res-link">` în `#resurseBody`.

## Aplicații
Secțiunea `#aplicatii` (tab „Aplicații”) prezintă aplicațiile create cu AI. Acum conține PsyAI Prompt Engineering, cu linkul către pagina ei. Ca să adaugi o aplicație, copiază blocul `<article class="card app">` din `index.html` și schimbă titlul, descrierea și linkul. „Materiale recomandate” rămâne secțiune separată (`#resurse`).

## Evenimente
Secțiunea `#evenimente` are două carduri `.ws`: workshopul pentru psihologi (în fiecare duminică, 19:00–20:30, datele 15.11, 22.11, 29.11, 06.12, 13.12, backup 1 oră) și cel pentru profesori (data se anunță). Când se stabilesc datele pentru profesori, înlocuiește textul „Data și ora se anunță” cu orarul, ca la psihologi.

## De completat înainte de lansare
- [ ] Linkul canalului de Telegram (vezi mai sus).
- [ ] În `confidentialitate.html` și `termeni.html`: cele 3 câmpuri galbene „[de completat: …]” (forma juridică, CUI/CIF, adresa).
- [ ] Cursurile din `index.html` sunt conținut-schiță: verifică titlurile, descrierile și punctele din fiecare card.
- [ ] Când ai datele reale: format, durată, tarif, linkuri de înscriere.
- [ ] Adaugă `<link rel="canonical">`, `og:url` și `og:image` pe domeniul final.
- [ ] Verifică pe telefon (iOS Safari, Android Chrome): meniul, cardurile de curs, linkurile `mailto:`.
- [ ] Dă paginile juridice la citit unui jurist.
