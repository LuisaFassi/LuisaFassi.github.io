# Guida: aggiornare il sito luisafassi.github.io

## Come funziona

Il sito è una cartella di file di testo. Modifichi un file sul PC, lo mandi a GitHub con GitHub Desktop, e dopo 2–5 minuti la modifica è online su [luisafassi.github.io](https://luisafassi.github.io). Non c'è un pulsante "pubblica": mandare il file a GitHub è già la pubblicazione.

| Cosa vuoi cambiare | Dove (dentro la cartella del sito) |
| --- | --- |
| CV | `assets\pdf\LuisaFassi_CV.pdf` |
| Descrizione in home | `_pages\about.md` |
| News | cartella `_news` |
| Pubblicazioni | `_bibliography\papers.bib` |
| PDF degli articoli | cartella `assets\pdf` |
| Immagini delle pubblicazioni | cartella `assets\img\publication_preview` |
| Nome, email, profili social | `_config.yml` |

Tre regole valgono per tutti i file:

- La parte fra i due `---` all'inizio di un file non si tocca (unica eccezione: la data delle news).
- Spazi a inizio riga, `:` e virgole restano come sono: sono la struttura del file.
- Un file nuovo si fa copiando uno esistente, non creandolo dal Blocco note (che lo salverebbe come `.md.txt`).

## GitHub Desktop

Si installa una volta sola; poi ogni modifica segue sempre gli stessi quattro passi.

**Una volta sola**

1. Scarica e installa [GitHub Desktop](https://desktop.github.com) ed entra con il tuo account GitHub.
2. **File → Clone repository** → scegli `LuisaFassi/LuisaFassi.github.io` → **Clone**. Sul PC compare la cartella `Documenti\GitHub\LuisaFassi.github.io`.

**Ogni volta**

1. In GitHub Desktop clicca **Fetch origin** (se compare, poi **Pull origin**) per avere l'ultima versione.
2. Fai le modifiche nella cartella da Esplora risorse. I file `.md`, `.bib` e `.yml` si aprono con il Blocco note (clic destro → Apri con).
3. Torna su GitHub Desktop: a sinistra vedi i file cambiati. In basso scrivi due parole su cosa hai fatto e clicca **Commit to master**.
4. Clicca **Push origin**. Fra 2–5 minuti è online.

## CV

La voce "CV" del menu apre direttamente un PDF: per aggiornarlo basta sostituire il file.

1. Rinomina il nuovo CV esattamente `LuisaFassi_CV.pdf` (maiuscole e trattino basso compresi).
2. Copialo in `assets\pdf`, sovrascrivendo quello vecchio.
3. Commit e Push da GitHub Desktop.

Se dopo qualche minuto vedi ancora il CV vecchio, ricarica con Ctrl+F5: è il browser che ricorda la versione precedente.

## Descrizione in home

Il testo della home è in `_pages\about.md`, tutto quello che sta sotto il secondo `---` (da "Welcome to my page!" in giù).

Si scrive come testo normale, con pochi segni speciali:

| Per ottenere | Scrivi |
| --- | --- |
| Un nuovo paragrafo | una riga vuota fra i due paragrafi |
| Parole cliccabili | `[testo cliccabile](https://indirizzo)` |
| Grassetto | `**parole**` |
| Elenco puntato | `- ` all'inizio della riga |

Nei link non ci vanno spazi fra `]` e `(`, e l'indirizzo va copiato intero con `https://`. Gli stessi segni funzionano nelle news.

## News

Ogni news è un file nella cartella `_news`; la home mostra le 3 con la data più recente, e il titolo "news" porta alla pagina con tutte.

- **Aggiungere:** copia e incolla un file esistente, rinomina la copia `announcement_6.md` (poi 7, 8…), aprila e cambia data e testo.
- **Modificare:** apri il file e cambia il testo. Il numero nel nome non dice nulla: per trovare quella giusta aprile e leggi.
- **Togliere:** cancella il file.

Un file di news è fatto così:

```markdown
---
layout: post
date: 2025-03-15 00:00:00-0000
inline: true
---

Talk at the [ECREA conference](https://ecrea2024ljubljana.eu/) in Ljubljana

***
```

La data si scrive anno-mese-giorno ed è lei a decidere l'ordine. Il `***` finale è la riga di separazione: lascialo.

## Pubblicazioni

Tutte le pubblicazioni sono in un solo file, `_bibliography\papers.bib`: per aggiungerne una copi un articolo esistente in fondo al file e cambi i dati.

```
@article{Fassi2025parolachiave,
  bibtex_show={true},
  preview={fassi2025.jpg},
  title={Titolo completo dell'articolo},
  author={Fassi, Luisa and Orben, Amy and Ford, Tamsin},
  journal={Nome della rivista},
  volume={12},
  pages={100-110},
  year={2025},
  doi={10.1000/xyz123},
  url={https://link-all-articolo},
  pdf={fassi2025.pdf}
}
```

- **Prima riga:** un codice interno, diverso da tutti gli altri e senza spazi.
- **Autori:** `Cognome, Nome` separati dalla parola `and`, non da virgole o `&`.
- **Virgole:** ogni riga finisce con una virgola, tranne l'ultima prima della `}`.
- **Righe che non servono:** cancellale intere.
- **Scorciatoia:** su Google Scholar, sotto l'articolo, **Cita → BibTeX** dà il blocco già pronto; aggiungi a mano solo `bibtex_show`, `pdf` e `preview`.

**PDF dell'articolo.** Mettilo in `assets\pdf` con un nome senza spazi e scrivi quel nome, `.pdf` compreso, nella riga `pdf={...}`.

**Immagine accanto al titolo.** Mettila in `assets\img\publication_preview` (jpg o png, meglio quadrata e sotto i 300 KB) e scrivi il nome nella riga `preview={...}`. Il nome deve essere identico: `.jpg` e `.jpeg` sono diversi. Per toglierla cancelli la riga. Nella cartella ci sono già tre immagini mai usate: `P1.jpg`, `P2.jpeg`, `P3.jpg`.

**Anno nuovo.** La pagina mostra solo gli anni elencati in `_pages\publications.md`, alla riga `years: [2024,2023,2021,2020,2019]`. Per un articolo del 2025 aggiungi `2025,` in testa, altrimenti non compare.

## Impostazioni generali (_config.yml)

Il file `_config.yml` è nella cartella principale del sito e contiene nome, contatti, profili e aspetto; un errore qui ferma tutto il sito, quindi si cambia solo il valore dopo i due punti.

| Riga | Valore oggi | Cosa fa |
| --- | --- | --- |
| `first_name`, `last_name` | Luisa, Fassi | Nome in alto e nella scheda del browser |
| `email` | Luisa.fassi@mrc-cbu.cam.ac.uk | Icona busta in fondo alla home |
| `description` | Luisa Fassi personal page. | Frase che Google mostra sotto il link |
| `icon` | ⚛️ | Icona della scheda del browser (è quella del modello, si può cambiare emoji) |
| `linkedin_username`, `scholar_userid`, `orcid_id`, `github_username` | compilati | Icone dei profili in fondo alla home |
| `twitter_username`, `research_gate_profile`, `osf_id` e simili | vuoti | Compilati, fanno comparire la loro icona |
| `enable_navbar_social` | false | `true` mette le icone dei profili anche nella barra in alto |
| `last_updated` | false | `true` mostra in fondo la data di ultimo aggiornamento |
| `max_author_limit` | 3 | Autori visibili per articolo; gli altri si aprono con un clic |
| `limit` sotto `announcements` | 3 | Quante news in home |
| `enable_darkmode` | true | Pulsante tema chiaro/scuro |

- Cambia solo quello che sta dopo i `:`, mai il nome a sinistra, e lascia gli spazi a inizio riga.
- Tutto quello dopo `#` è un commento e non conta.
- Per svuotare una voce lascia vuoto dopo i `:`, senza cancellare la riga.
- `title: blank` è voluto: vuol dire "usa il nome completo come titolo".
- Le sezioni blog, commenti e `external_sources` sono avanzi del modello al-folio: non si vedono sul sito e si possono ignorare.

## Se qualcosa va storto

Il sito non si rompe mai del tutto: finché una modifica non passa, resta online la versione precedente.

- **Controllare se è andata:** su [github.com/LuisaFassi/LuisaFassi.github.io](https://github.com/LuisaFassi/LuisaFassi.github.io) apri la scheda **Actions**. Pallino verde = online; croce rossa = errore, quasi sempre uno spazio, una virgola o un `---` spostato nell'ultimo file toccato.
- **Ferma in coda (pallino giallo) da più di 15 minuti:** sono i server di GitHub lenti. Apri l'esecuzione "pages build and deployment" → **Cancel workflow** → **Re-run all jobs**.
- **Annullare una modifica:** in GitHub Desktop, scheda **History**, clic destro sul commit → **Revert changes in commit** → **Push origin**.
- **"Docker Image CI"** nella lista delle esecuzioni si può ignorare: non pubblica nulla.
- Altrimenti, scrivi a Francesco.
