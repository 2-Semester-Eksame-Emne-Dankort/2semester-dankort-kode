Teknisk dokumentation – [Dankort-Case]

Om projektet
Dette projekt er lavet som en del af Tema 10-eksamensprojekt. Vi har lavet et dynamisk website med HTML, CSS og JavaScript bygget i Astro, hvor dele af indholdet bliver hentet fra et Api, lavet i Supabase

Sitet består af følgende sider:

Index.Astro-Landing page
Oremærket.Astro-Øremerket siden

Links
GitHub repository: [https://github.com/2-Semester-Eksame-Emne-Dankort/2semester-dankort-kode]
Netlify link:
Figma: [https://www.figma.com/design/jyZBgOI53NKgKMPSnKURaQ/2.semester-eksamen?node-id=619-132&t=tmBH2ptchkzgRCPv-1]
Trello: [https://trello.com/b/rUBROqAC/2sem-eksamen]

Projektstruktur
Projektet er opdelt i HTML, CSS og JavaScript-filer.

Astro-kode/
├── Pages/
├── index.astro
├── oremerket.astro
├── Components/
│ ├── apple-pay.astro
│ ├── button.astro
│ ├── counter.astro
│ ├── footer.astro
│ ├── frodel.astro
│ ├── header.astro
│ └──hero-forside.astro
│ ├── hero-oremerket.astro
│ ├── kort.astro
│ ├── om-oremerket.astro
│ ├── quotes.astro
│ ├── sparer.astro
└──trin.astro
├── layouts/
│ ├── layout.astro
└── README.md

Filbeskrivelser

Pages – bruges til at bygge de enkelte sider op

Components- Bruges til at bygge elementer som så kan placeres i layout eller pages

Layout- Bruges til at fast placeres de elementer som skal bruges globalt, så de bare kan importes i pages.

Navngivning

Vi har navngivet vores filer, variabler og funktioner, så de er så selvforklarende som muligt. Dette gør det lettere for alle i gruppen at læse og forstå koden.

Eksempler på variabler

Eksempler på variabler
const popId;
const circles;

Eksempler på funktioner
AddEventListener;

Vi har brugt camelCase i JavaScript, fordi det gør koden mere ensartet og lettere at læse.

Kommentarer i koden
Vi har kommenteret de steder i koden, hvor det giver mening. Fx ved funktioner, fetch-kald og steder hvor der sker DOM-manipulation.

Eksempel:

// --- 1. FIND BEHOLDERE ---
const container = document.querySelector(".cards");
const priceSort = document.querySelector("#price-sort"); // Finder dropdown
const filterButtons = document.querySelectorAll(".filter-btn"); // Finder knapper
Data og JSON-struktur
Vi henter data fra et API i JSON-format.

Et objekt kan fx se sådan ud:

{
{
"id": 16,
"title": "Apple",
"description": "Fresh and crisp apples, perfect for snacking or incorporating into various recipes.",
"category": "groceries",
"price": 1.99,
"discountPercentage": 12.62,
"rating": 4.19,
"stock": 8,
"tags": [
"fruits"
],
"sku": "GRO-BRD-APP-016",
"weight": 9,
"dimensions": {
"width": 13.66,
"height": 11.01,
"depth": 9.73
},
"warrantyInformation": "3 year warranty",
"shippingInformation": "Ships in 2 weeks",
"availabilityStatus": "In Stock",
"reviews": [
{
"rating": 5,
"comment": "Very satisfied!",
"date": "2025-04-30T09:41:02.053Z",
"reviewerName": "Sophia Brown",
"reviewerEmail": "sophia.brown@x.dummyjson.com"
},
{
"rating": 1,
"comment": "Very dissatisfied!",
"date": "2025-04-30T09:41:02.053Z",
"reviewerName": "Scarlett Bowman",
"reviewerEmail": "scarlett.bowman@x.dummyjson.com"
},
{
"rating": 3,
"comment": "Very unhappy with my purchase!",
"date": "2025-04-30T09:41:02.053Z",
"reviewerName": "William Gonzalez",
"reviewerEmail": "william.gonzalez@x.dummyjson.com"
}
],
"returnPolicy": "90 days return policy",
"minimumOrderQuantity": 7,
"meta": {
"createdAt": "2025-04-30T09:41:02.053Z",
"updatedAt": "2025-04-30T09:41:02.053Z",
"barcode": "7962803553314",
"qrCode": "https://cdn.dummyjson.com/public/qr-code.png"
},
"images": [
"https://cdn.dummyjson.com/product-images/groceries/apple/1.webp"
],
"thumbnail": "https://cdn.dummyjson.com/product-images/groceries/apple/thumbnail.webp"
},
}
Felter vi bruger
id – bruges til at sende brugeren videre til detaljesiden
title – Produktnavn
tags – Sætter en kategori ind (feks meat eller fruit)
description – En beskrivelse af produktet
price – Produktets pris
Formular og validering
Vi har lavet en formular, hvor brugeren kan indtaste oplysninger.

HTML-validering:

required – feltet skal udfyldes
type="email" – validerer email-format
Det sikrer, at brugeren ikke kan sende formularen, hvis felterne ikke er udfyldt korrekt.

Git og branches
Vi har brugt GitHub til at samarbejde om projektet.

Vi har arbejdet med branches, så vi ikke sad og ændrede i det samme på samme tid.

Vi navngav branchene med feature.

Eksempler på branches
prodcutlister-og-js
JS
Workflow
Lave en branch med feature-navn
Kode en feature
Committe ændringer
Pushe til GitHub
Merge til main når det virkede
Det gjorde det nemmere at holde styr på, hvem der lavede hvad.

Bæredygtighed
Vi har tænkt bæredygtighed ind i projektet.

Tiltag:

Ingen videoer
Ingen tunge frameworks
Genbruge af kode
Udfordringer undervejs
En af vores udfordringer var at få data fra Rest API’et vist korrekt på siderne.

Løsninger:

Console.logge data undervejs
Bruge URLSearchParams
Dele opgaverne mere tydeligt i gruppen
Mulige forbedringer
Hvis vi skulle arbejde videre med projektet, kunne vi forbedre det ved at tilføje:

Søgefunktion
Add to basket knap der virker
Udvide konceptet med mere data
Gruppemedlemmer
Frederik Højvar Bust Hansen
Gregor Pavlik
Isabel Miabom
William Tien Nguyen
