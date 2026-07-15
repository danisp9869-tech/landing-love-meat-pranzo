# 🥩 I Love Meat · Landing Menu Pranzo — Pianezza

Landing page **single-file** (`index.html`) per il **menu pranzo** di I Love Meat.
Stesso layout, colori e logica della landing cena ("I Love Meat · Degustazione"),
ma pensata per la **pausa pranzo**: chi lavora, chi ha poco tempo, chi vuole
mangiare bene e in fretta senza spendere troppo.

Nessuna dipendenza, nessun build: si apre con un doppio click.

---

## Le due offerte

La pagina presenta **due formule tra cui scegliere**:

| Formula | Cosa include | Prezzo |
|---|---|---|
| **Tagliere di Carne** | 4 pezzi a scelta direttamente al banco | **19,90 €** |
| **Piatto Tris** | Primo, secondo e contorno + **acqua e caffè inclusi** | **13 €** |

La scelta della formula è integrata anche nel modulo di prenotazione
(campo *"Quale formula"*), così arriva insieme alla prenotazione.

---

## Struttura della pagina

**Hero** (brand + titolo + sottotitolo pausa pranzo) → **Due card offerta**
(Tagliere 19,90€ / Tris 13€) → **Sezione "Due modi di fare pausa"** (copy per
lavoratori / pranzo veloce) → **Form di prenotazione** con gestione capienza →
**Footer** (orari pranzo, contatti) → **CTA sticky**.

---

## Personalizzazione

Tutto ciò che cambia da cliente a cliente è nel blocco `window.LP_CONFIG` in
cima allo `<script>` di `index.html`:

```js
capacity: 60,                       // coperti totali a pranzo
phone: "+393456881360",             // telefono per prenotazioni/chiamate
lunch: ["12:00", … ,"14:30"],       // fasce orarie del pranzo
closedDays: [0,6],                  // 0=Dom … 6=Sab → pranzo chiuso sab e dom
booked: { … },                      // coperti già occupati (demo)
```

- **Prezzi e testo delle offerte**: nelle due `.offer-card` dell'hero e nelle
  `<option>` del campo *"Quale formula"* del form.
- **Orari a footer**: nel blocco `.foot`.

> ⚠️ In produzione, dove indicato con `>>> PRODUZIONE`, va collegata la POST
> che registra la prenotazione nel gestionale / Google Sheet.

---

## Privacy

`privacy.html` è l'informativa GDPR (fac-simile): aggiorna il blocco `DATI`
con i dati reali del ristorante e fai verificare il testo da un legale prima
dell'uso in produzione.

---

## Pubblicazione

Il workflow `.github/workflows/deploy-pages.yml` pubblica il sito su
**GitHub Pages** a ogni push su `main`. Attiva Pages una volta da
**Settings → Pages → Source: "GitHub Actions"**.
