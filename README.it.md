<div align="center">

<img src="assets/humaux-mark.svg" width="76" alt="Humaux" />

# Humaux

**Costruito attorno all'essere umano.**

Strumenti ausiliari centrati sull'uomo per gli agenti IA — per costruire l'intera
catena di automazione *attorno alle persone, non sopra di esse.*

[English](README.md) · [简体中文](README.zh.md) · [Français](README.fr.md) · Italiano

[**humaux.com**](https://humaux.com) · [Humaux Memory](https://humaux.com/humauxmemory)

</div>

---

## Cos'è Humaux

Gli agenti stanno diventando capaci. Ciò che manca loro è la **continuità** — alla
fine di ogni sessione dimenticano chi sei, cosa hai deciso e cosa avevano già
imparato.

Humaux costruisce lo strato che resta. Non un modello più grande, né un altro
agente — la **memoria e gli strumenti a misura d'uomo** a cui i tuoi agenti si
collegano, così l'intera catena di lavoro è costruita attorno a te.

<div align="center">
<img src="assets/why.png" width="880" alt="Senza una memoria condivisa ogni sessione riparte da zero; con Humaux gli agenti riprendono da dove avevi lasciato." />
</div>

La nostra roadmap si sviluppa in tre fasi:

| Fase | Prodotto | Stato |
|---|---|---|
| **1 · Memoria** | Una memoria strutturata, condivisa da ogni agente | **Attiva** |
| 2 · Pipeline di contenuti | Trasformare il lavoro grezzo in conoscenza riutilizzabile | In corso |
| 3 · Catena di automazione | Chiudere il cerchio dall'intento al risultato | Pianificata |

---

## Humaux Memory

> Il secondo cervello che i tuoi agenti condividono.

Una memoria persistente e strutturata a cui ogni agente — **Claude Code, Cursor,
Codex, Windsurf, Gemini CLI, Cline** e altri — si collega tramite
[MCP](https://modelcontextprotocol.io). Salva una volta; richiamato ovunque.
Ricorda le **decisioni, non solo le chat** — strutturate, corroborate e restituite
con le loro fonti.

<div align="center">
<img src="assets/how-it-works.png" width="920" alt="Come funziona Humaux Memory: gli agenti si collegano via MCP a una memoria condivisa con una pipeline cognitiva, un grafo della conoscenza e un grafo del codice." />
</div>

### Cosa fa

| | |
|---|---|
| **Una memoria, ogni agente** | Collegati una volta con MCP. Ogni strumento condivide lo stesso secondo cervello. |
| **Stratificazione cognitiva** | Le note grezze vengono distillate da una pipeline — atomi → scenari → persona → competenze riutilizzabili — invece di accumularsi in un registro piatto. |
| **Grafo della conoscenza** | I ricordi formano un grafo; le contraddizioni si risolvono con un doppio asse temporale: vince il fatto più recente, la storia resta. |
| **Grafo del codice** | Invia il codice su cui stai lavorando e interrogane la struttura — chiamanti, dipendenze, impatto — invece di rileggere interi file. Risparmia token. |
| **Persona automatica** | Humaux impara chi sei e come lavori, e lo inietta in ogni agente collegato — non devi rispiegarti. |
| **Bene comune pubblico** | Conoscenza condivisa su base volontaria, fornita solo una volta corroborata in modo indipendente. |
| **Il tuo modello** | Usa il tuo LLM e il tuo provider di embedding. I tuoi dati, cifrati ed esportabili. |

### Connessione in una riga

Claude Code:

```bash
claude mcp add --transport http humaux-memory https://humaux.com/memory/mcp \
  --header "Authorization: Bearer <il-tuo-token>"
```

Qualsiasi altro client MCP (Cursor, Codex, Windsurf…):

```bash
npx -y humaux-memory-mcp --token <il-tuo-token>
```

Ottieni il token su **[humaux.com → Connect](https://humaux.com/humauxmemory)**. I
nuovi strumenti arrivano lato server: i tuoi agenti li adottano automaticamente,
senza reinstallare.

<div align="center">
<img src="assets/connect.png" width="880" alt="La schermata Connect di Humaux: endpoint e token, configurazione in un clic per 14+ client e gli strumenti che il tuo agente ottiene." />
<br/><sub>La schermata Connect nel prodotto — un endpoint, ogni client, token mascherato.</sub>
</div>

### Insegna al tuo agente a usarla

La memoria dà il meglio quando l'agente vi ricorre da solo. Incolla questo nelle
regole permanenti del tuo agente (`CLAUDE.md`, `AGENTS.md`, `.cursor/rules`…):

```text
All'inizio di una sessione, cerca nella memoria il contesto rilevante prima di rispondere.
Salva decisioni, preferenze, correzioni e progressi non appena li apprendi.
Preferisci i ricordi corroborati; non chiedere ciò che puoi richiamare.
```

---

## Principi

- **Attorno all'essere umano.** Gli strumenti ti potenziano; non sostituiscono il tuo giudizio né nascondono ciò che fanno.
- **Ricordare le decisioni, non le trascrizioni.** Struttura e fonti prima dei log grezzi.
- **Onesto per impostazione predefinita.** La conoscenza corroborata è segnalata; le affermazioni a fonte unica sono trattate con cautela.
- **I tuoi dati sono tuoi.** Il tuo modello; esporta quando vuoi.

---

## Link

- 🌐 Sito web — **[humaux.com](https://humaux.com)**
- 🧠 Humaux Memory — **[humaux.com/humauxmemory](https://humaux.com/humauxmemory)**
- 📦 Connettore — [`humaux-memory-mcp`](https://www.npmjs.com/package/humaux-memory-mcp) su npm

<div align="center">
<sub>© Humaux · Costruito attorno all'essere umano.</sub>
</div>
