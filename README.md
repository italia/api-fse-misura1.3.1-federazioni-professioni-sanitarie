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
├── openapi/          # Specifiche OpenAPI
│   ├── schemas/      # Schemi e modelli dati
│   └── examples/     # Esempi di request/response
└── docs/             # Documentazione aggiuntiva
```

Le specifiche OpenAPI e le risorse semantiche saranno pubblicate progressivamente nella directory `openapi/`. Gli esempi pratici di utilizzo delle API saranno forniti direttamente nelle specifiche OpenAPI.

## 📐 Standard e formati

Le specifiche adotteranno formati e standard riconosciuti a livello nazionale e internazionale. I dettagli specifici sulle risorse semantiche, le annotazioni e le convenzioni adottate saranno documentati progressivamente man mano che vengono definiti e validati.

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

## Formato dati Attestazione digitale (proposta)

Di seguito è riportata la prima versione dello schema dei dati relativi all'attestato digitale.

| CAMPO | DESCRIZIONE SINTETICA CAMPO | OBBLIGATORIETÀ (SI/NO) | TIPOLOGIA | LUNGHEZZA MASSIMA CARATTERI |
|------|----------------------------|------------------------|-----------|----------------------------|
| taxID | Codice Fiscale | SI | ALFANUMERICO |  |
| legalName | Denominazione ESTESA Ordine Territoriale | NO | ALFANUMERICO |  |
| LogoFed | Logo Federazionale Nazionale | NO | MULTIMEDIALE |  |
| LogoOrd | Logo Ordine Territoriale | NO | MULTIMEDIALE |  |
| member (image) | Foto Professionista | NO | MULTIMEDIALE |  |
| member (givenName) | Nome | NO | ALFANUMERICO |  |
| member (familyName) | Cognome | NO | ALFANUMERICO |  |
| birthPlace | Luogo di nascita | NO | ALFANUMERICO |  |
| member (birthDate) | Data di nascita | NO | DATA |  |
| releasedBy | Rilasciato da Ordine di “...” (Denominazione Corta Ordine Territoriale) | NO | ALFANUMERICO |  |
| membershipRegister | Albo di appartenenza (sigla) | NO | ALFANUMERICO |  |
| vatID | Numero di iscrizione all’albo | NO | ALFANUMERICO |  |
| validFrom | Data di Scadenza | NO | DATA |  |
| validThrough | Data di Rilascio | NO | DATA |  |
| identifier | Seriale carta | NO | ALFANUMERICO |  |
| pensionFund | Numero Ente Nazionale di Previdenza | NO | ALFANUMERICO |  |

Lo schema dati sopra riportato è da intendersi come proposta iniziale ed è aperto a modifiche e miglioramenti.
Per suggerire variazioni, integrazioni o correzioni allo schema, si invita ad aprire una issue dedicata nel repository di riferimento.
Il campo relativo alla "LUNGHEZZA MASSIMA CARATTERI" è attualmente lasciato vuoto in quanto si è in attesa dei feedback delle Federazioni, con l’obiettivo di pervenire a uno standard comune e condiviso tra tutti i soggetti coinvolti.

## ⚠️ ATTENZIONE

Quest'area è pubblica: pertanto, nelle segnalazioni **non devono** essere inserite informazioni riservate quali:

- password o credenziali,
- configurazioni di sicurezza,
- log applicativi o documenti contenenti dati sensibili,
- dati personali o informazioni soggette a vincoli di riservatezza contrattuale.

Qualora fosse necessario trasmettere informazioni riservate, dovranno essere utilizzati canali alternativi, previamente concordati con il DTD.
