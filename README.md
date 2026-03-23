# Repository condiviso per le API delle Federazioni delle Professioni Sanitarie nell'ambito della Misura 1.3.1

## Introduzione

Questo repository contiene le specifiche OpenAPI condivise per le API relative alla **Misura 1.3.1** nell'ambito degli Accordi con le Federazioni Nazionali delle Professioni Sanitarie.

L'obiettivo è fornire un **minimo comune denominatore** per l'esposizione di servizi sanitari attraverso:
- Specifiche OpenAPI di riferimento
- Risorse semantiche condivise
- Annotazioni standardizzate

Le specifiche, le risorse semantiche e le annotazioni sono in fase di realizzazione e saranno progressivamente pubblicate e aggiornate in questo repository.

## 📋 Contesto normativo e obiettivi

Il **DM del 7 settembre 2023** prevede l'accesso dei professionisti sanitari a **FSE 2.0** con specifiche funzionalità per la parte di competenza. Per abilitare tale accesso in modo sicuro ed efficiente, nella riunione del **4 luglio 2025** convocata dal **Ministero della Salute** con la presenza del DTD, è stato proposto alle Federazioni Nazionali l'utilizzo dei fondi **PNRR M1C1-1.3.1-PDND** per identificare tramite uno standard sicuro i professionisti sanitari.

La **Piattaforma Digitale Nazionale Dati (PDND)** assume un ruolo centrale abilitando la possibilità di verificare automaticamente l'**appartenenza** di un professionista sanitario al relativo Albo e il suo **stato professionale corrente**. Questo avviene mediante l'erogazione di **e-service (API)** relativi agli **Albi Unici Nazionali** da parte delle Federazioni Nazionali.

La PDND assicura così la messa a disposizione del patrimonio informativo della PA, in linea con il **CAD** e la normativa vigente, superando i controlli su dati autocertificati e rendendo i processi più snelli ed efficienti.

## 🏥 Federazioni coinvolte

Il progetto coinvolge le seguenti Federazioni degli Ordini delle Professioni Sanitarie:

- **FNOMCEO** - Federazione Nazionale degli ordini dei medici chirurghi e degli odontoiatri
- **FNOPI** - Federazione Nazionale Ordini Professioni Infermieristiche
- **FNO TSRM e PSTRP** - Federazione Nazionale Ordini Tecnici Sanitari di Radiologia Medica e delle Professioni Sanitarie Tecniche, della Riabilitazione e della Prevenzione
- **CNOP** - Consiglio Nazionale Ordine degli Psicologi
- **FOFI** - Federazione Ordini Farmacisti Italiani
- **FNOFI** - Federazione Nazionale Ordini dei Fisioterapisti
- **FNOB** - Federazione Nazionale Ordini dei Biologi
- **FNOVI** - Federazione Nazionale Ordini Veterinari Italiani
- **FNOPO** - Federazione Nazionale Ordini della Professione di Ostetrica
- **FNCF** - Federazione Nazionale Ordini Chimici e Fisici

### Esperienza pregressa

Il Dipartimento per la Trasformazione Digitale ha già avviato da tempo i lavori con **FNOMCEO** (Federazione Nazionale degli Ordini dei Medici Chirurghi e degli Odontoiatri), da cui si è maturata un'esperienza che costituirà un riferimento metodologico e tecnico per tutte le Federazioni.

## 📁 Struttura del repository

Il repository è organizzato nelle seguenti directory:

```
.
├── openapi/          # Specifiche OpenAPI (versione di riferimento 3.1.0)
│   ├── schemas/      # Schemi e modelli dati
│   └── examples/     # Esempi di request/response
│       └── govway/   # Specifiche ottimizzate per GovWay/ModI (versione 3.0.0)
└── docs/             # Documentazione aggiuntiva
```

Le specifiche OpenAPI e le risorse semantiche saranno pubblicate progressivamente nella directory `openapi/`. Gli esempi pratici di utilizzo delle API saranno forniti direttamente nelle specifiche OpenAPI.

### Compatibilità GovWay / ModI

Per l'integrazione con il gateway **GovWay** e la relativa validazione dei pattern di sicurezza **ModI**, è disponibile una versione dedicata delle specifiche nella cartella `openapi/examples/govway/`. 

Queste versioni:
- Utilizzano lo standard **OpenAPI 3.0.0**.
- Risolvono le incompatibilità note del validatore ModI (es. errore 107 su campi `examples`, `contentMediaType`, `contentEncoding`).
- Mantengono la piena compatibilità semantica con la versione di riferimento.

## 📐 Standard e formati

Le specifiche adotteranno formati e standard riconosciuti a livello nazionale e internazionale. I dettagli specifici sulle risorse semantiche, le annotazioni e le convenzioni adottate saranno documentati progressivamente man mano che vengono definiti e validati.

### Note tecniche e di business

- **Estensibilità degli e-service**: Gli e-service pubblicati possono essere estesi dalle singole Federazioni per rispondere a specifiche esigenze territoriali, a condizione che venga garantita la piena **retrocompatibilità** con lo standard qui definito. Tale facoltà di estensione **non si applica** all'e-service relativo a **IT-Wallet**, il cui schema deve rimanere rigorosamente conforme.
- **Accertamento status (FPROF-02)**: Il campo `status` nella risposta indica lo stato dell'iscrizione (es. `ATTIVO`, `SOSPESO`, `NON_ISCRITTO`, etc.). In caso di professionista non trovato, il servizio restituisce **HTTP 200** con status **`NON_ISCRITTO`**.
- **Verifica status (FPROF-03)**: Il campo `is_active` nella risposta è di tipo booleano e certifica che il professionista è iscritto all'Albo e che la sua posizione risulta attiva (non sospesa, radiata o cancellata). In caso di professionista non trovato, il servizio restituisce **HTTP 200** con `is_active: false`.
- **Accertamento iscrizione (FPROF-01)**: Restituisce un elenco di professionisti corrispondenti ai criteri di ricerca. In caso di nessuna corrispondenza, il servizio restituisce **HTTP 200** con un array vuoto (`result: []`).

In sintesi, per tutte le API, l'assenza di un professionista nei registri viene gestita con un esito di business negativo restituito con stato **HTTP 200**, evitando l'uso del codice HTTP 404.

---

## ✅ Validazione delle specifiche

Le specifiche OpenAPI pubblicate in questo repository sono **validate e conformi** alle linee guida italiane per le API REST.

**Strumento di validazione ufficiale**: [OAS Checker Italia](https://italia.github.io/api-oas-checker/)

### Requisiti per le modifiche

Se vengono proposte modifiche alle specifiche, queste **devono essere ri-validate** e devono riportare:
- ✅ **0 errori**
- ⚠️ Possibilmente **0 warning**

### Come validare

Lo strumento OAS Checker Italia è disponibile come:
- **Interfaccia web**: https://italia.github.io/api-oas-checker/
- **CLI e GitHub Action**: https://github.com/italia/api-oas-checker

💡 **Raccomandazione**: utilizzare il profilo **"Italian Guidelines Full"** per garantire la massima conformità agli standard nazionali.

# 📣 Discussions e Issues

Questo repository utilizza **GitHub Discussions** e **GitHub Issues** per la gestione delle comunicazioni. Ecco come utilizzarli:

## 📋 GitHub Discussions

Utilizza le **Discussions** come spazio di confronto collaborativo per:

- **💡 Proporre nuove funzionalità** - Condividi idee o miglioramenti sull'evoluzione delle API
- **❓ Porre domande** - Chiarimenti su utilizzo, formati, best practice, interpretazione delle specifiche
- **📘 Discutere la documentazione** - Suggerimenti su esempi, spiegazioni o parti poco chiare
- **🗣️ Confronto generale** - Discussioni aperte su scelte architetturali, pattern da adottare, esperienze

## 🐞 GitHub Issues

Utilizza le **Issues** per:

- **Segnalare bug confermati** nelle specifiche OpenAPI
- **Errori tecnici** nella documentazione o negli schemi
- **Problemi di validazione** specifici e riproducibili

**Nota**: Se non sei sicuro che si tratti di un vero bug o errore, ti consigliamo di aprire prima una **Discussion** per confrontarti con la community e i maintainer.

## Formato dati Attestazione digitale

Di seguito è riportata la versione definitiva dello schema dei dati relativi all'attestato digitale.

| CAMPO | DESCRIZIONE SINTETICA CAMPO | OBBLIGATORIETÀ | TIPOLOGIA | LUNGHEZZA MASSIMA CARATTERI |
|------|----------------------------|------------------------|-----------|----------------------------|
| taxID | Codice Fiscale | OBBLIGATORIO | ALFANUMERICO |  |
| LogoFed | Logo Federazionale Nazionale | FACOLTATIVO | MULTIMEDIALE |  |
| LogoOrd | Logo Ordine Territoriale | FACOLTATIVO | MULTIMEDIALE |  |
| member (givenName) | Nome | OBBLIGATORIO | ALFANUMERICO |  |
| member (familyName) | Cognome | OBBLIGATORIO | ALFANUMERICO |  |
| releasedBy | Rilasciato da Ordine di “...” (Denominazione Ordine Territoriale) | OBBLIGATORIO | ALFANUMERICO |  |
| membershipRegister | Albo o Sezione o Settore di appartenenza | FACOLTATIVO | ALFANUMERICO |  |
| vatID | Numero di iscrizione all’albo | OBBLIGATORIO | ALFANUMERICO |  |
| validThrough | Data di Rilascio | OBBLIGATORIO | DATA |  |
| status | Stato di iscrizione del professionista (VALID, INVALID) | OBBLIGATORIO | ALFANUMERICO |  |




## ⚠️ ATTENZIONE

Quest'area è pubblica: pertanto, nelle segnalazioni **non devono** essere inserite informazioni riservate quali:

- password o credenziali,
- configurazioni di sicurezza,
- log applicativi o documenti contenenti dati sensibili,
- dati personali o informazioni soggette a vincoli di riservatezza contrattuale.

Qualora fosse necessario trasmettere informazioni riservate, dovranno essere utilizzati canali alternativi, previamente concordati con il DTD.
