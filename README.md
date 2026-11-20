# Bufete for Claude

Bufete is a legal work platform for law firms. This plugin connects Claude to your Bufete account. Claude can research Dominican, Colombian, Mexican and United States law, read court rulings and Dominican bills, read your firm's matters and documents, and keep your tasks current. Every answer cites the sources Claude read.

You need a Bufete account in a firm. Claude sees only what your role in the firm lets you see.

## What it includes

| Part | What it does |
|---|---|
| Bufete connector | Connects to `https://api.bufete.ai/mcp`. You sign in to Bufete and choose a firm the first time. |
| `legal-research` skill | Researches enacted law, court rulings and Dominican bills, and answers with citations and the in-force status of each article. |
| `matter-brief` skill | Builds a brief of one case or project from its record, court cases, documents and your tasks. |
| `task-follow-up` skill | Lists your tasks, and creates or updates them after you confirm. |

### Tools of the connector

| Tool | Kind |
|---|---|
| `search_law_library`, `read_law_library` | Read |
| `search_case_law`, `read_case_law` | Read |
| `search_legislation`, `read_legislation` | Read |
| `list_matters`, `get_matter` | Read |
| `search_documents`, `read_document` | Read |
| `find_my_tasks` | Read |
| `create_task`, `update_task` | Write, your own tasks only |

## Set up

1. Install the plugin from the Claude directory in Claude, Cowork or Claude Code. In Claude Code you can also run:

   ```
   /plugin install bufete --marketplace Bitzer-AI/bufete-claude-plugin
   ```

2. The first time Claude calls a Bufete tool, a browser window opens. Sign in to Bufete.
3. When you belong to more than one firm, choose the firm. Then approve the access that Claude asks for.

To disconnect, open Bufete, go to **Settings › Connections › Assistants** and remove the connection. Claude loses access at its next call.

## Example prompts

- "¿Qué dice el Código de Trabajo dominicano sobre el preaviso? Cita los artículos."
- "Busca jurisprudencia de la Corte Constitucional de Colombia sobre estabilidad laboral reforzada y resume las tres sentencias más relevantes."
- "Is there a bill in the Dominican Senate about personal data protection? What is its status?"
- "Dame un resumen del caso Pérez contra Inversiones del Caribe antes de la audiencia."
- "What is overdue on my plate this week?"
- "Turn these meeting notes into tasks on the Pérez matter: …"

## Data and privacy

The connector reads only the data you ask about, inside the firm you chose, and within your permissions in that firm. Bufete records which tool was called, by whom and when, but not the content that Claude receives. Bufete does not use your documents or conversations to train AI models. Claude processes what the tools return under Anthropic's own terms.

- Privacy policy: https://bufete.ai/en/privacy-policy/
- Terms of service: https://bufete.ai/en/terms-of-service/

## Support

Email anthony@bufete.ai. Tell us the prompt, the tool that failed and the time.

## License

The files in this repository are under the MIT license. Using the Bufete service needs a Bufete account and follows the Bufete terms of service.
