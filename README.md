# Dankort Case - Teknisk Dokumentation

## Projektoversigt

Dette projekt er udviklet som et Astro-baseret redesign af Dankorts website med fokus pa:

1. at kommunikere Dankorts kernefordele
2. at synliggore Dankort Oremærket
3. at kombinere statisk content med dynamisk data fra Supabase

Løsningen er bygget komponentbaseret i Astro med HTML, CSS og vanilla JavaScript.

### Primare funktioner

1. Genbrugelige UI-komponenter (header, footer, hero, knap, kort, counter)
2. Dynamisk datahentning via Supabase REST API (årsdata til donation/counter)
3. Interaktive features (burger-menu, kort-popups, auto-slider, års-faner)
4. Responsivt layout til mobil og desktop

### Sider

1. `src/pages/index.astro` - landing page
2. `src/pages/oremerket.astro` - Oremærket-side med naturkort og counter

### Links

1. GitHub repository: [https://github.com/2-Semester-Eksame-Emne-Dankort/2semester-dankort-kode]
2. Netlify: [dankort-2semester-eksamen.netlify.app]
3. Figma: [https://www.figma.com/design/jyZBgOI53NKgKMPSnKURaQ/2.semester-eksamen?node-id=619-132&t=tmBH2ptchkzgRCPv-1]
4. Trello: [https://trello.com/b/rUBROqAC/2sem-eksamen]

## Projektstruktur

```2SEMESTER-DANKORT-KODE
.
├── astro.config.mjs
├── package.json
├── tsconfig.json
├── public/
│   └── Img/
├── src/
│   ├── assets/
│   ├── components/
│   │   ├── apple-pay.astro
│   │   ├── button.astro
│   │   ├── counter.astro
│   │   ├── footer.astro
│   │   ├── fordel.astro
│   │   ├── header.astro
│   │   ├── hero-forside.astro
│   │   ├── hero-oremerket.astro
│   │   ├── kort.astro
│   │   ├── om-oremerket.astro
│   │   ├── quotes.astro
│   │   ├── sparer.astro
│   │   └── trin.astro
│   ├── layouts/
│   │   └── Layout.astro
│   ├── pages/
│   │   ├── index.astro
│   │   └── oremerket.astro
│   └── styles/
│       └── main.css
└── README.md
```

## Filbeskrivelser

### Layout

`src/layouts/Layout.astro` er den globale wrapper for alle sider:

1. importerer global styling fra `src/styles/main.css`
2. renderer `Header`
3. renderer sideindhold via `<slot />`
4. renderer `Footer`

Det betyder, at alle pages far ens global struktur og navigation.

### Pages

1. `src/pages/index.astro` sammensætter forsiden af hero + indholdssektioner
2. `src/pages/oremerket.astro` sammensætter Oremærket-hero, introtekst, trin forklaring, interaktivt kort og dynamisk counter

### Components

Komponenterne er opdelt efter sektioner og funktionalitet. Nogle er primart statiske content-sektioner, mens andre indeholder JavaScript.

## Dataflow

Projektet har to typer dataflow:

### 1) Statisk dataflow

1. Sider importerer Astro-komponenter
2. Komponenter renderer hardcoded tekst, billeder og markup
3. Styles ligger lokalt i hver komponent + globalt i `main.css`
4. Raleway font bliver importeret globalt i `main.css`

### 2) Dynamisk dataflow (counter)

1. `src/components/counter.astro` kalder Supabase REST endpoint via `fetch(...)`
2. data sorteres pa `year.asc`
3. tredje element (`years[2]`) bruges som initial aktiv visning (2026)
4. ved klik opdateres årstallet, donation, areal, CO2, arter og progress-bar i DOM

## Sidebeskrivelser

### `index.astro`

Importerede sektioner:

1. `Hero`
2. `Fordel`
3. `ApplePay`
4. `OmOremerket`
5. `Sparer`
6. `Quotes`

### `oremerket.astro`

Importerede sektioner:

1. `HeroOremerket`
2. lokal introsektion (inline styles)
3. `Kort` forklaring af Øremærket
4. `Kort` (SVG-kort + popups)
5. `Counter` (Supabase-data)

## Komponentoversigt

1. `header.astro`: sticky header, burger-menu, mobil/desktop nav, klik-udenfor-luk
2. `footer.astro`: footerlinks + language-button + brandkort
3. `hero-forside.astro`: landing hero med CTA-knap
4. `hero-oremerket.astro`: hero-banner for Oremærket-siden
5. `button.astro`: genbrugelig CTA-link-knap
6. `fordel.astro`: 4 fordelskort med ikoner
7. `apple-pay.astro`: guide-sektion med trin og visuals
8. `om-oremerket.astro`: teaser-sektion med link til Oremærket-siden
9. `sparer.astro`: lokalsamfund/besparelses-sektion
10. `quotes.astro`: horizontal slider med auto-scroll
11. `kort.astro`: SVG-Danmarkskort med klikbare punkter og popover-modaler
12. `counter.astro`: årsbaseret donationskort med data fra Supabase
13. `trin.astro`: trin-for-trin komponent

## Stylingstrategi

1. Global reset + design tokens i `src/styles/main.css`
2. CSS custom properties bruges til farver og typography
3. Hver komponent har eget scoped `<style>` for lokal layoutkontrol
4. Billeder/ikoner leveres primart fra `public/Img`
5. Font hentes via Google Fonts (Raleway)

## Responsivt design

Projektet bruger overvejende et breakpoint omkring `900px`:

1. under 900px: mobil layouts (column flow, burger-nav, mindre typografi)
2. over 900px: desktop layouts (grid/rad-opdelinger, synlig desktop-nav)

Responsiv adfærd findes i alle sektioner via lokale media queries.

## Scriptoversigt

### `header.astro`

1. toggler burger-menu
2. lukker menu via close-knap
3. lukker menu ved klik udenfor nav

### `quotes.astro`

1. auto-scroll af quote-slider hvert 3. sekund
2. resetter scroll tilbage til start ved slutning

### `kort.astro`

1. finder alle `.map-point` i SVG
2. binder klik-events
3. matcher punkt-id med popup-id (`popup-<id>`)
4. åbner modal via `showPopover()`

### `counter.astro`

1. fetcher årsdata fra Supabase
2. binder klik pa års-faner
3. opdaterer relevante DOM-felter dynamisk
4. opdaterer progress-bar bredde baseret pa valgt år

## API og integration

### Supabase endpoint

`https://ixghczwghjowmllzbjuk.supabase.co/rest/v1/oermaerketsiden-taeller?select=*&order=year.asc`

### Forventede felter

1. `year`
2. `donation_amount`
3. `progress_percent`
4. `area_number`
5. `co2_amount`
6. `animal_species`

## Kørsel og build

### Kommandoer

1. `npm install`
2. `npm run dev`
3. `npm run build`

## Kendte tekniske forhold

1. enkelte asset paths bruger både `Img/...` og `/public/Img/...`-mønster; de bor standardiseres
2. `header` linker til `/erhverv` og `/privat`, som ikke findes i nuværende pages
3. `quotes` bruger `setInterval` uden lifecycle cleanup (relevant ved mere avanceret navigation/runtime)
4. `trin.astro` ligger i kodebasen men er ikke inkluderet i sideflow

## Forslag til videreudvikling

1. Implementer billeder gennem assets
2. Få CTA-knappen i hero-sektionen på forsiden samt navigations linket til at føre videre til de faktiske sider.
