# Leihbar

**Die Bibliothek der Dinge für deine Nachbarschaft.**

[![Next.js](https://img.shields.io/badge/Next.js-14-000000?logo=next.js&logoColor=white)](https://nextjs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5-3178C6?logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![Prisma](https://img.shields.io/badge/Prisma-5-2D3748?logo=prisma&logoColor=white)](https://www.prisma.io/)
[![Neon](https://img.shields.io/badge/Neon-PostgreSQL-00E599?logo=postgresql&logoColor=white)](https://neon.tech/)
[![Vercel](https://img.shields.io/badge/Deployed%20on-Vercel-000000?logo=vercel&logoColor=white)](https://vercel.com/)
[![License](https://img.shields.io/badge/license-Proprietär-lightgrey)](#10-lizenz)

---

## Inhalt

1. [Projektbeschreibung](#1-projektbeschreibung)
2. [Features](#2-features)
3. [Tech-Stack](#3-tech-stack)
4. [Voraussetzungen](#4-voraussetzungen)
5. [Lokale Entwicklung](#5-lokale-entwicklung)
6. [Datenbank & Prisma](#6-datenbank--prisma)
7. [Projektstruktur](#7-projektstruktur)
8. [Deployment auf Vercel](#8-deployment-auf-vercel)
9. [Datenschutz / DSGVO / Schweiz](#9-datenschutz--dsgvo--schweiz)
10. [Lizenz](#10-lizenz)

---

## 1. Projektbeschreibung

**Leihbar** ist eine hyperlokale Web-App, mit der Nachbarinnen und Nachbarn selten genutzte Gegenstände teilen, statt sie einzeln zu kaufen – eine „Bibliothek der Dinge" für das eigene Quartier. Wer eine Bohrmaschine, einen Raclette-Ofen oder einen Hochdruckreiniger braucht, findet ihn ein paar Häuser weiter, statt ihn neu zu besorgen.

Leihbar ist bewusst für die **Schweiz** gebaut: organisiert entlang von Quartieren, Gemeinden und Nachbarschaften, mit Fokus auf Nachhaltigkeit, gelebte Gemeinschaft und messbare CO₂-Ersparnis. Jedes geteilte Objekt zeigt sichtbar, wie viel CO₂ und wie viel Geld die Nachbarschaft gemeinsam spart.

**Nutzen nach Zielgruppe:**

- **Familien** – teurer Gelegenheitsbedarf (Festzelt, Beamer, Anhänger) wird leihbar statt gekauft; weniger Anschaffungen, weniger Platzbedarf.
- **Nachbarinnen und Nachbarn** – unkomplizierte Hilfe im Alltag und neue Kontakte im eigenen Haus oder Quartier.
- **Gemeinden** – ein niederschwelliges Werkzeug zur Quartierentwicklung und für gelebte Kreislaufwirtschaft.
- **Kirchgemeinden und Vereine** – eine einfache Plattform, um vorhandene Ressourcen innerhalb der Gemeinschaft zu organisieren.

**Warum Leihen statt Kaufen?**

- **CO₂** – Jeder vermiedene Neukauf spart die graue Energie der Produktion. Eine geteilte Bohrmaschine ersetzt viele einzeln gekaufte.
- **Kosten** – Werkzeug, Gartengeräte und Eventausstattung sind teuer und stehen meist ungenutzt herum. Teilen senkt die Kosten für alle.
- **Platz** – Keller und Estrich bleiben frei. Was selten gebraucht wird, muss nicht im eigenen Haushalt lagern.

---

## 2. Features

- **Quartier-Beitrittscodes** – Nutzerinnen und Nutzer treten ihrer Nachbarschaft über einen Code bei (z. B. `GRUEN-42`), der lokal ausgehängt oder verteilt wird. Inhalte sind immer auf das eigene Quartier begrenzt.
- **Pseudonyme statt Klarnamen** – Es werden keine echten Namen, Adressen oder Standorte erfasst. Jede Person erscheint nur unter einem Pseudonym (z. B. `N-7K`) – Datenschutz by Design.
- **Dinge teilen** – Gegenstände werden in klaren Kategorien angeboten: **Werkzeug, Küche, Freizeit, Garten, Elektronik** und Sonstiges.
- **CO₂-Ersparnis pro Gegenstand** – Für jede Kategorie wird die geschätzte Einsparung an CO₂ und Warenwert ausgewiesen und über die Nachbarschaft aufsummiert.
- **Anfragen-Flow** – Über „Leihen anfragen" stellt man eine Anfrage mit Zeitraum und optionaler Nachricht. Die besitzende Person bestätigt, lehnt ab oder markiert die Rückgabe.
- **Pfand-Option** – Optionaler Pfandbetrag (in CHF) je Gegenstand schafft Verbindlichkeit.

**Optionale Erweiterungen (Roadmap):**

- Bewertungen und Vertrauensstufen innerhalb des Quartiers
- Verfügbarkeits- und Reservierungskalender
- Erinnerungen für Rückgaben und anstehende Leihen
- Magic-Link-Login als optionale Alternative zum reinen Pseudonym
- In-App-Nachrichten zwischen Leihenden und Besitzenden

---

## 3. Tech-Stack

| Schicht | Technologie | Begründung |
|---|---|---|
| Framework | **Next.js 14** (App Router) | Frontend und API in einem Projekt, Server Components, Edge-fähig |
| UI | **React 18** | Komponentenmodell, breites Ökosystem |
| Sprache | **TypeScript** | Typsicherheit über die gesamte Codebasis |
| Styling | **TailwindCSS** | schnelles, konsistentes, mobile-first Design |
| ORM | **Prisma** | typsichere Queries und Migrationen |
| Datenbank | **PostgreSQL via Neon** (Region EU / Frankfurt) | serverless, autoscaling, Branching für Previews |
| Hosting | **Vercel** | nahtloses Next.js-Deployment, Preview-Deployments pro Pull Request |

---

## 4. Voraussetzungen

- **Node.js** `>= 18.17` (empfohlen: 20 LTS)
- **npm** `>= 9` oder **pnpm** `>= 8`
- Ein **Neon**-Account ([neon.tech](https://neon.tech)) mit einer Datenbank in der Region **EU (Frankfurt)**
- Ein **Vercel**-Account ([vercel.com](https://vercel.com)) für das Deployment
- Optional: ein **GitHub**-Repository für CI/CD und Preview-Deployments

---

## 5. Lokale Entwicklung

```bash
# 1. Repository klonen
git clone https://github.com/<dein-account>/leihbar.git
cd leihbar

# 2. Abhängigkeiten installieren
npm install

# 3. Umgebungsvariablen anlegen
cp .env.example .env
```

`.env` befüllen (Werte aus dem Neon-Dashboard übernehmen):

```env
# Pooled Connection (Runtime) – Host enthält "-pooler"
DATABASE_URL="postgresql://USER:PASSWORD@ep-xxxx-pooler.eu-central-1.aws.neon.tech/leihbar?sslmode=require&pgbouncer=true&connect_timeout=10"

# Direct Connection (Migrationen) – ohne Pooler
DIRECT_URL="postgresql://USER:PASSWORD@ep-xxxx.eu-central-1.aws.neon.tech/leihbar?sslmode=require"

# Signaturschlüssel für die pseudonyme Session (min. 32 Zeichen)
SESSION_SECRET="mit-openssl-rand-base64-32-erzeugen"

# Öffentliche App-URL
NEXT_PUBLIC_APP_URL="http://localhost:3000"
```

```bash
# 4. Prisma Client generieren
npx prisma generate

# 5. Schema in die Datenbank migrieren
npx prisma migrate dev

# 6. (Optional) Demodaten einspielen
npm run db:seed

# 7. Entwicklungsserver starten
npm run dev
```

Die App läuft anschliessend unter [http://localhost:3000](http://localhost:3000). Beim ersten Aufruf wird ein Beitrittscode abgefragt – mit den Demodaten lautet er `GRUEN-42`.

---

## 6. Datenbank & Prisma

Das Datenmodell ist bewusst **datenminimal**: keine Klarnamen, keine Adressen, kein Geo-Standort. Der Ort ist ausschliesslich der Beitrittscode einer `Neighborhood`.

### Modelle im Überblick

- **`Neighborhood`** – ein Quartier mit eindeutigem Beitrittscode. Klammert alle Inhalte ein.
- **`User`** – eine pseudonyme Person (`alias`), genau einem Quartier zugeordnet.
- **`Item`** – ein geteilter Gegenstand mit Kategorie, optionalem Pfand und Verfügbarkeit.
- **`Loan`** – eine Leihbeziehung zwischen einem `Item` und einer leihenden Person inkl. Status und Zeitraum.

### Beispiel-Schema (`prisma/schema.prisma`)

```prisma
datasource db {
  provider  = "postgresql"
  url       = env("DATABASE_URL") // Pooled, für die Laufzeit
  directUrl = env("DIRECT_URL")   // Direkt, für Migrationen
}

generator client {
  provider = "prisma-client-js"
}

model Neighborhood {
  id        String   @id @default(cuid())
  code      String   @unique
  name      String
  createdAt DateTime @default(now())
  users     User[]
  items     Item[]
}

model User {
  id             String   @id @default(cuid())
  alias          String   // Pseudonym, kein Klarname
  email          String?  @unique // optional, nur für späteren Magic-Link-Login
  neighborhoodId String
  createdAt      DateTime @default(now())
  neighborhood   Neighborhood @relation(fields: [neighborhoodId], references: [id], onDelete: Cascade)
  items          Item[]
  loans          Loan[]   @relation("borrower")

  @@index([neighborhoodId])
}

enum Category {
  WERKZEUG
  KUECHE
  GARTEN
  FREIZEIT
  ELEKTRONIK
  SONSTIGES
}

model Item {
  id             String   @id @default(cuid())
  name           String
  description    String   @default("")
  category       Category @default(SONSTIGES)
  depositCents   Int      @default(0) // Pfand in Rappen
  available      Boolean  @default(true)
  ownerId        String
  neighborhoodId String
  createdAt      DateTime @default(now())
  owner          User         @relation(fields: [ownerId], references: [id], onDelete: Cascade)
  neighborhood   Neighborhood @relation(fields: [neighborhoodId], references: [id], onDelete: Cascade)
  loans          Loan[]

  @@index([neighborhoodId, available])
  @@index([ownerId])
}

enum LoanStatus {
  REQUESTED
  APPROVED
  RETURNED
  DECLINED
}

model Loan {
  id         String     @id @default(cuid())
  itemId     String
  borrowerId String
  fromDate   DateTime
  toDate     DateTime
  message    String     @default("")
  status     LoanStatus @default(REQUESTED)
  createdAt  DateTime   @default(now())
  item       Item @relation(fields: [itemId], references: [id], onDelete: Cascade)
  borrower   User @relation("borrower", fields: [borrowerId], references: [id], onDelete: Cascade)

  @@index([itemId])
  @@index([borrowerId])
}
```

### Migrationen

```bash
# Neue Migration in der lokalen Entwicklung erstellen und anwenden
npx prisma migrate dev --name <beschreibung>

# Migrationen in Produktion anwenden (CI/CD, kein interaktiver Prompt)
npx prisma migrate deploy

# Prisma Client nach Schemaänderungen neu generieren
npx prisma generate

# Datenbank im Browser inspizieren
npx prisma studio
```

### Seed-Daten

Die Datei `prisma/seed.ts` legt das Demo-Quartier `GRUEN-42` sowie Beispiel-Gegenstände wie **Bohrmaschine**, **Raclette-Ofen** und **Hängematte** an.

```ts
// prisma/seed.ts (Auszug)
import { PrismaClient, Category } from "@prisma/client";
const prisma = new PrismaClient();

async function main() {
  const hood = await prisma.neighborhood.upsert({
    where: { code: "GRUEN-42" },
    update: {},
    create: { code: "GRUEN-42", name: "Grünquartier" },
  });

  const owner = await prisma.user.create({
    data: { alias: "N-7K", neighborhoodId: hood.id },
  });

  await prisma.item.createMany({
    data: [
      { name: "Bohrmaschine (Bosch)", category: Category.WERKZEUG, depositCents: 1000, ownerId: owner.id, neighborhoodId: hood.id },
      { name: "Raclette-Ofen für 8", category: Category.KUECHE, depositCents: 500, ownerId: owner.id, neighborhoodId: hood.id },
      { name: "Hängematte mit Gestell", category: Category.FREIZEIT, depositCents: 0, ownerId: owner.id, neighborhoodId: hood.id },
    ],
  });
}

main().finally(() => prisma.$disconnect());
```

Konfiguration in der `package.json`:

```json
{
  "prisma": { "seed": "tsx prisma/seed.ts" },
  "scripts": {
    "db:seed": "prisma db seed",
    "db:studio": "prisma studio"
  }
}
```

Ausführen mit:

```bash
npm run db:seed
```

---

## 7. Projektstruktur

```
leihbar/
├─ app/                  # App Router: Routen, Layout, Seiten
│  ├─ layout.tsx         # Grundlayout, Fonts, Navigation
│  ├─ page.tsx           # Startseite / Feed („Entdecken")
│  ├─ join/              # Quartier beitreten (Beitrittscode)
│  ├─ items/             # Gegenstand teilen & Detailansicht
│  ├─ loans/             # „Meine Leihen" (ein- und ausgehend)
│  └─ api/               # API-Routen (Route Handlers)
│     ├─ items/          # GET Liste · POST anlegen · GET Detail
│     ├─ neighborhoods/  # Beitritt / Quartier-Logik
│     └─ loans/          # GET meine · POST anfragen · PATCH Status
├─ components/           # Wiederverwendbare UI-Bausteine (Cards, Forms, Nav)
├─ lib/                  # Helfer: Prisma-Client, Auth, CO₂-Logik, Validierung
├─ prisma/               # schema.prisma, Migrationen, seed.ts
├─ public/               # statische Assets (Logo, Icons, Bilder)
├─ styles/               # globale Styles, Tailwind-Direktiven
├─ .env.example          # Vorlage für Umgebungsvariablen
├─ next.config.mjs       # Next.js-Konfiguration & Security-Header
├─ tailwind.config.ts    # Tailwind-Konfiguration
└─ package.json
```

---

## 8. Deployment auf Vercel

1. **Projekt importieren** – In Vercel „Add New… → Project" wählen und das GitHub-Repository importieren. Vercel erkennt Next.js automatisch.
2. **Environment Variables setzen** – Unter *Settings → Environment Variables* für die Umgebungen *Production*, *Preview* und *Development*:
   - `DATABASE_URL` → Neon **Pooled** Connection String (`-pooler`-Host, `sslmode=require`, `pgbouncer=true`)
   - `DIRECT_URL` → Neon **Direct** Connection String (für Migrationen)
   - `SESSION_SECRET` → 32+ Zeichen Zufallswert
   - `NEXT_PUBLIC_APP_URL` → die Produktions-URL
3. **Build Command** – `npm run build`. Das Build-Skript muss `prisma generate` enthalten, z. B.:
   ```json
   { "scripts": { "build": "prisma generate && next build" } }
   ```
   Migrationen in Produktion über `prisma migrate deploy` ausführen (eigener Build-Step oder Release-Hook).
4. **Start Command** – wird von Vercel automatisch verwaltet (serverless). Für ein Self-Hosting-Setup: `npm start`.
5. **Redeploy** – Jeder Push auf den Hauptbranch löst ein Production-Deployment aus; jeder Pull Request erhält ein **Preview-Deployment** mit eigener URL. Manuell über *Deployments → Redeploy*.

### Typische Fehler & Troubleshooting

| Symptom | Ursache | Lösung |
|---|---|---|
| `PrismaClientInitializationError` im Build | `prisma generate` fehlt im Build | `prisma generate` ins `build`-Skript oder `postinstall` aufnehmen |
| `Can't reach database server` | falscher Connection String / SSL | Neon-`DATABASE_URL` mit `sslmode=require` verwenden |
| Verbindungen brechen unter Last ab | Serverless ohne Pooling | Pooled-URL (`-pooler`) für `DATABASE_URL`, Direct-URL nur für `DIRECT_URL` |
| Migrationen scheitern auf Vercel | `migrate dev` in CI | in Produktion `prisma migrate deploy` nutzen, nicht `migrate dev` |
| Änderungen erscheinen nicht | Caching der Route | betroffene Routen auf `export const dynamic = "force-dynamic"` setzen |

---

## 9. Datenschutz / DSGVO / Schweiz

Leihbar folgt dem Prinzip der **Datensparsamkeit** und ist auf den Schweizer Markt ausgerichtet.

- **Keine Klarnamen** – Personen erscheinen ausschliesslich unter einem Pseudonym. Es werden keine echten Namen, Adressen oder genauen Standorte gespeichert.
- **Minimale Datenspeicherung** – Erfasst werden nur das Pseudonym, die Quartierzugehörigkeit sowie die geteilten Gegenstände und Leihbeziehungen.
- **Quartier-Scoping** – Inhalte sind technisch auf die eigene Nachbarschaft begrenzt; es gibt keinen öffentlichen Marktplatz.
- **Hosting in EU-Region** – Datenbank (Neon) und Deployment in der Region **EU / Frankfurt**.
- **Kein Tracking, keine Werbung** – keine Analytics-Drittanbieter, kein Profiling.
- **Rechtlicher Rahmen** – Für die Schweiz gilt das revidierte Datenschutzgesetz (**revDSG**); bei Nutzung aus dem EU-Raum zusätzlich die **DSGVO**. Vor einem produktiven Betrieb sind Datenschutzerklärung, Impressum sowie Auskunfts- und Löschfunktionen zu ergänzen.

> **Hinweis:** Dieses Projekt ist ein Demonstrator / Prototyp und stellt **keinen Ersatz für eine rechtliche Beratung** dar.

---

## 10. Lizenz

**Proprietär – privat. Alle Rechte vorbehalten.**

Dieser Code ist nicht zur Weitergabe oder Wiederverwendung freigegeben. Soll das Projekt quelloffen werden, kann diese Sektion durch eine **MIT-Lizenz** ersetzt und eine `LICENSE`-Datei ergänzt werden.

---

© Leihbar – die Bibliothek der Dinge für deine Nachbarschaft.
