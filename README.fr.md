<div align="center">

<img src="assets/humaux-mark.svg" width="76" alt="Humaux" />

# Humaux

**Conçu autour de l'humain.**

Des outils auxiliaires centrés sur l'humain pour les agents IA — pour bâtir toute la
chaîne d'automatisation *autour des personnes, et non au-dessus d'elles.*

[English](README.md) · [简体中文](README.zh.md) · Français · [Italiano](README.it.md)

[**humaux.com**](https://humaux.com) · [Humaux Memory](https://humaux.com/humauxmemory)

</div>

---

## Qu'est-ce que Humaux

Les agents deviennent compétents. Ce qui leur manque, c'est la **continuité** — à
chaque fin de session, ils oublient qui vous êtes, ce que vous avez décidé et ce
qu'ils avaient déjà appris.

Humaux construit la couche qui demeure. Pas un modèle plus grand, ni un agent de
plus — la **mémoire et les outils à taille humaine** auxquels vos agents se
branchent, pour que toute la chaîne de travail soit bâtie autour de vous.

Notre feuille de route se déroule en trois étapes :

| Étape | Produit | Statut |
|---|---|---|
| **1 · Mémoire** | Une mémoire structurée, partagée par tous les agents | **En ligne** |
| 2 · Pipelines de contenu | Transformer le travail brut en connaissances réutilisables | En cours |
| 3 · Chaîne d'automatisation | Boucler de l'intention au résultat | Prévu |

---

## Humaux Memory

> Le second cerveau que vos agents partagent.

Une mémoire persistante et structurée, à laquelle chaque agent — **Claude Code,
Cursor, Codex, Windsurf, Gemini CLI, Cline** et d'autres — se connecte via
[MCP](https://modelcontextprotocol.io). Enregistrez une fois ; rappelé partout.
Elle retient les **décisions, pas seulement les conversations** — structurées,
corroborées et restituées avec leurs sources.

### Ce qu'elle fait

| | |
|---|---|
| **Une mémoire, tous les agents** | Connectez-vous une fois via MCP. Chaque outil partage le même second cerveau. |
| **Structuration cognitive** | Les notes brutes sont distillées par un pipeline — atomes → scénarios → persona → compétences réutilisables — au lieu de s'empiler en journal plat. |
| **Graphe de connaissances** | Les souvenirs forment un graphe ; les contradictions sont résolues avec un double axe temporel : le fait le plus récent l'emporte, l'historique est conservé. |
| **Graphe de code** | Envoyez le code sur lequel vous travaillez et interrogez sa structure — appelants, dépendances, impact — au lieu de relire des fichiers entiers. Économise des tokens. |
| **Persona automatique** | Humaux apprend qui vous êtes et comment vous travaillez, et l'injecte dans chaque agent connecté — plus besoin de vous réexpliquer. |
| **Bien commun public** | Connaissances partagées sur option, servies uniquement une fois corroborées de façon indépendante. |
| **Votre propre modèle** | Utilisez votre LLM et votre fournisseur d'embeddings. Vos données, chiffrées et exportables. |

### Connexion en une ligne

Claude Code :

```bash
claude mcp add --transport http humaux-memory https://humaux.com/memory/mcp \
  --header "Authorization: Bearer <votre-token>"
```

Tout autre client MCP (Cursor, Codex, Windsurf…) :

```bash
npx -y humaux-memory-mcp --token <votre-token>
```

Récupérez votre token sur **[humaux.com → Connect](https://humaux.com/humauxmemory)**.
Les nouveaux outils arrivent côté serveur : vos agents les récupèrent
automatiquement, sans réinstallation.

### Apprenez à votre agent à l'utiliser

La mémoire donne le meilleur quand l'agent y recourt de lui-même. Collez ceci dans
les règles permanentes de votre agent (`CLAUDE.md`, `AGENTS.md`, `.cursor/rules`…) :

```text
Au début d'une session, cherchez dans la mémoire le contexte pertinent avant de répondre.
Enregistrez décisions, préférences, correctifs et avancées dès que vous les apprenez.
Privilégiez les souvenirs corroborés ; ne demandez pas ce que vous pouvez retrouver.
```

---

## Principes

- **Autour de l'humain.** Les outils vous augmentent ; ils ne remplacent pas votre jugement et ne cachent pas ce qu'ils font.
- **Retenir les décisions, pas les transcriptions.** La structure et les sources avant les journaux bruts.
- **Honnête par défaut.** Le savoir corroboré est signalé ; les affirmations à source unique sont traitées avec prudence.
- **Vos données vous appartiennent.** Votre propre modèle ; export à tout moment.

---

## Liens

- 🌐 Site web — **[humaux.com](https://humaux.com)**
- 🧠 Humaux Memory — **[humaux.com/humauxmemory](https://humaux.com/humauxmemory)**
- 📦 Connecteur — [`humaux-memory-mcp`](https://www.npmjs.com/package/humaux-memory-mcp) sur npm

<div align="center">
<sub>© Humaux · Conçu autour de l'humain.</sub>
</div>
