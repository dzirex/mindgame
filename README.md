# Prší online zdarma (2–5 hráčů)

Tento adresář je připravený pro bezplatné nasazení přes **GitHub + Cloudflare Pages** a pro synchronizaci hry přes **Firebase Authentication + Realtime Database**.

> Bez serverových funkcí je to hra pro přátele. Databázová pravidla a klientské kontroly brání běžným omylům, ale technicky zkušený uživatel může klientské požadavky falšovat. Pro veřejnou soutěžní hru je nutný serverový backend.

## A. Firebase: přibližně 10 minut

1. Otevřete Firebase Console → **Add project** → vytvořte projekt `prsi-online`.
2. V přehledu projektu klikněte na ikonu **Web** `</>` a aplikaci pojmenujte `prsi-web`.
3. Zkopírujte konfiguraci `firebaseConfig` do souboru `firebase-config.js`.
4. **Authentication → Sign-in method → Anonymous → Enable → Save**.
5. **Build → Realtime Database → Create Database**. Vyberte evropský region, pokud jej konzole nabízí. Pro nastavení začněte v uzamčeném režimu.
6. Realtime Database → **Rules**: vložte obsah souboru `database.rules.json` a klikněte na **Publish**.

## B. GitHub: přibližně 5 minut

1. Na GitHubu klikněte **New repository**.
2. Název: `prsi-online`; nastavte **Public**; klikněte **Create repository**.
3. Nahrajte všechny soubory z tohoto adresáře (`index.html`, `style.css`, `app.js`, `firebase-config.js`, `database.rules.json`, `README.md`, `.gitignore`) přes **Add file → Upload files → Commit changes**.

## C. Cloudflare Pages: přibližně 5 minut

1. Založte si účet u Cloudflare a otevřete **Workers & Pages**.
2. **Create application → Pages → Import an existing Git repository**.
3. Propojte GitHub a vyberte repozitář `prsi-online`.
4. Nastavte **Framework preset: None**, **Build command: prázdné**, **Build output directory: /**.
5. Klikněte **Save and Deploy**.
6. Cloudflare vytvoří adresu například `https://prsi-online-abc.pages.dev`.

## D. Hraní

1. Host otevře veřejnou adresu, zadá jméno a klikne **Vytvořit místnost**.
2. Zobrazí se tlačítko **Kopírovat odkaz**.
3. Host odešle odkaz dalším 1–4 hráčům.
4. Každý zadá jméno a klikne **Připojit se**.
5. Host zahájí hru se 2–5 hráči.

## Pravidla v projektu

- 32 karet: 7, 8, 9, 10, J, Q, K, A ve čtyřech barvách
- Každý dostane 4 karty: 3 veřejné a 1 tajnou
- Vrchní karta lízacího balíčku je viditelná
- Hraje se barvou/hodnotou; J mění barvu; 7 přidá dvě karty; A přeskočí dalšího hráče
- Vítězí hráč bez karet

## Důležité omezení

Firebase Spark a Cloudflare Pages jsou zdarma jen v rámci jejich aktuálních limitů. Nesdílejte hru veřejně do velkých skupin a kontrolujte využití v obou konzolích.
