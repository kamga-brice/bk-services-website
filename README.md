# BK Services Website

Sito web vetrina e piattaforma di prenotazione servizi sviluppata con **React** e **TypeScript**, progettata per offrire un'esperienza utente fluida, internazionale e moderna. L'applicazione gestisce dinamicamente un portfolio di servizi digitali e multimediali, integrando un flusso completo di prenotazione, carrello e pagamenti.

## Tecnologie Utilizzate

* **Frontend Framework:** React 18, TypeScript
* **Build Tool:** Vite (per un HMR estremamente rapido e build ottimizzate)
* **Styling & UI:** Tailwind CSS, Framer Motion (per animazioni fluide), Lucide React (icone)
* **State Management:** Zustand (gestione globale e modulare di Carrello, Pagamenti, Temi e Codici Sconto)
* **Internationalization (i18n):** `i18next` e `react-i18next` con rilevamento automatico della lingua del browser (`i18next-browser-languagedetector`).
* **Servizi Esterni / BaaS:**
* **EmailJS:** Per l'invio asincrono di email transazionali (conferme d'ordine e moduli di contatto).
* **Supabase:** Integrato per la gestione del database (es. salvataggio ordini o validazione promozioni).


* **Routing:** React Router v6

## Funzionalità Principali

### 1. Internazionalizzazione Completa (i18n)

L'applicazione è completamente tradotta e supporta nativamente 4 lingue:

* Inglese (`en`) - Lingua di fallback
* Francese (`fr`)
* Tedesco (`de`)
* Italiano (`it`)

### 2. Vetrina Servizi Multimediali

L'architettura a componenti (es. `ServicesList`, `ServiceCard`) renderizza dinamicamente il catalogo dei servizi offerti da BK Services:

* *Photography*
* *Video Production*
* *Graphics*
* *General Production*
* *Drone Shooting*
* *Web Development*

### 3. Flusso di Prenotazione e Gestione Stato (Zustand)

Il sistema implementa un vero e proprio e-commerce di servizi:

* **Gestione Carrello (`cartStore`):** Aggiunta/rimozione di servizi con calcolo dinamico dei prezzi.
* **Gestione Promozioni (`promoStore` & `promoValidation`):** Inserimento e validazione di codici sconto al checkout.
* **Integrazione Pagamenti (`paymentStore` & `paypal.ts`):** Selezione del metodo di pagamento, gestione dello stato di transazione (`isProcessing`) e catch degli errori.

### 4. Notifiche Email Transazionali

Tramite il modulo `emailService.ts` (basato su EmailJS), il sistema invia comunicazioni dettagliate in tempo reale senza necessitare di un server backend dedicato:

* **`sendBookingRequest`:** Invia un recap completo della prenotazione (servizi, prezzi, data, location, durata e dati del cliente) utilizzando template configurati.
* **`sendContactRequest`:** Gestisce il form di contatto generico del sito.
* Feedback visivi immediati all'utente tramite `react-hot-toast`.

## Guida all'Avvio (Sviluppo Locale)

**Passaggio 1: Clonare il repository e installare le dipendenze**

```bash
git clone <inserire-url-del-repo>
cd bk-services-website
npm install

```

**Passaggio 2: Configurazione Variabili d'Ambiente**
Creare un file `.env` nella root del progetto e inserire le chiavi necessarie per far funzionare EmailJS e Supabase:

```env
VITE_EMAILJS_SERVICE_ID=your_service_id
VITE_EMAILJS_TEMPLATE_ID_CMD=your_template_id_cmd
VITE_EMAILJS_TEMPLATE_ID_CONTACT=your_template_id_contact
VITE_EMAILJS_PUBLIC_KEY=your_public_key

```

**Passaggio 3: Avviare il server di sviluppo Vite**

```bash
npm run dev

```

L'applicazione sarà disponibile all'indirizzo locale indicato nel terminale (es. `http://localhost:5173`).

## Linting e Qualità del Codice

Il progetto utilizza una rigida configurazione di **ESLint** specifica per TypeScript e React (inclusi i React Hooks) per garantire un codice pulito e privo di type errors. Per lanciare il linting:

```bash
npm run lint

```
