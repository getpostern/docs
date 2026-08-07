# The Postern docs dictionary

**One term per concept. One concept per term.**

This is rule W1 of the docs house style, and it is the highest-leverage rule we
have: before this file existed, the running software was called *the gateway /
Postern / the app service / the stack / two containers / the published image*
inside a single section, and the record of agent requests had **seven** names
across two pages.

**The one exception:** a string that appears on a screen is quoted exactly as it
appears, in code font or bold, even when it breaks a rule here. The reader must be
able to match our words to their screen. `Poll cadence` stays `Poll cadence`
because that is what the Console prints.

---

## 1 · The terms

| concept | use this | never |
|---|---|---|
| the running software | **Postern** | the gateway, the app service, the stack, this gateway, your gateway, two containers, the published image |
| the computer Postern runs on | **the machine Postern runs on** | the box, the host, the server, the target machine |
| the computer the reader is sitting at | **your computer** | your laptop, the client machine, this end |
| port 8787 | **the Console port** | the admin surface, the REST edge, that admin group, the admin group |
| port 8788 | **the agent port** | the agent edge, the MCP edge, the agent-facing edges, the remote MCP edge |
| the per-agent credential | **the agent key** | bearer, the bearer token, the secret, a credential, a fresh secret, the token |
| to encrypt a stored credential | **encrypt** | seal, re-seal, sealed |
| the credential store | **the vault** | the encrypted store, the secret store |
| the record of agent requests | **the record** | the ledger, the audit log, the audit trail, the gate's memory, the log |
| a source's own credential | **your source password** | provider credential, upstream credential |
| how often Postern checks a source | **how often Postern checks** | cadence, the poll interval, the schedule |
| a computer with no screen | **a computer with no screen** | headless, a headless box |
| bound to 127.0.0.1 | **it only answers on the machine it runs on** | binds loopback, published on loopback, loopback-bound |
| to open a port to this computer only | **opened to this computer** | published, publishes that port |
| a port open to nothing | **not opened at all** | published nowhere |
| to create an agent key | **create** | mint (keep **Mint a key** where it is the button) |
| the AI program connecting to Postern | **the agent** | the client, the consumer, the harness |
| an AI program running on a company's servers | **a hosted agent** | hosted client, cloud client, a vendor cloud |
| one area of life Postern covers | **a sector** | a domain, an area, a scope |
| permission for one agent to reach one sector | **a grant** | permission, access, entitlement |
| the settings file beside `docker-compose.yml` | **`.env`** | the environment file, the config |
| Postern's web interface | **the Console** | the UI, the admin UI, the dashboard, the Gatehouse |

## 2 · Words banned outright

| banned | why | use |
|---|---|---|
| publish / published (of a port) | reads as *made public* — the opposite of what Compose does | opened to this computer |
| the box | jargon, and ambiguous with the machine you sit at | the machine Postern runs on |
| headless | most readers do not know it | a computer with no screen |
| quiesce | nobody says this | stop |
| idempotent | jargon | running it twice is safe |
| no-op | jargon | delete the sentence |
| opaque blob | jargon | unreadable |
| tenant | SaaS vocabulary; Postern has no tenants | delete |
| green / start green | not a word the Console shows | **ok** — the word the Console shows |
| drill / one-row drill | invented | row detail |
| detective rather than preventive | jargon | it records what happened; it never stops anything |
| egress | jargon | connect out |
| bring the Console to yourself | the banned lift-and-carry register | open it over SSH |
| poppy | a brand ink name; meaningless to a reader and to a screen reader | name the thing, or delete |
| simply, just, easy, don't worry, unfortunately, please note | softeners — R28, untouched by any amendment | delete |
| № · field guide · specimen · plate · the gate (as metaphor) · admission · the keeper · raising · bring one up · Fig. *n* | the founder's voice ruling, 2026-08-04 | plain English |

**Delete on sight, or reduce to one plain clause** — none of these changes a
reader's action, and the crypto detail belongs in `SECURITY.md`:
percent-encode · PID 1 · mDNS · CGNAT · KDF · S256 · RFC 9728 · PKCE-bound token
exchange · jsonb · oracle · constant-time · AES-256-GCM byte counts.

## 3 · Explained once, then reused verbatim

These carry a load a synonym would lose. Write the sentence once. Paste it
unchanged wherever it is needed. Do not improve it in one place only.

| term | the canonical sentence |
|---|---|
| **loopback / localhost / 127.0.0.1** | Only this computer can reach these addresses. Nothing on your Wi-Fi, and nothing on the internet, can. |
| **sector** | A sector is one area of your life: finance, mail, calendar, contacts, health, home. It is the smallest thing you can grant. |
| **MCP** | MCP is the standard way AI assistants connect to outside tools. Postern speaks it, so Claude, ChatGPT and Cursor connect the same way. |
| **tailnet** | Your tailnet is the private network Tailscale builds between the devices signed into your account. Nothing else can reach it. |
| **the key is shown once** | Postern cannot show you this key again. It keeps a scrambled copy it can check against, never the key itself. |
| **default-deny** | A new key can reach nothing until you tick a sector. |
| **the two volumes** | Docker keeps two storage areas outside the containers: your data, and the key that unlocks every account you connect. `docker compose down -v` deletes both, permanently. |
| **single-use setup token** | You can use a setup token one time. Postern uses it up when you press **Connect**. |
| **200 / 401 / 404** | 200 means it answered. 401 means it answered and wants a key. 404 means nothing is there. |
| **a curl command** | This prints only the three-digit answer code. Paste it into a terminal on your computer. |
| **bare origin** | The address only — `https://` and the machine name, with nothing after it. |
| **redirect URI** | The address the provider sends you back to after you approve. They match it exactly, character for character. |
| **scopes** | Permissions — the list of things your app may read. |
| **app-specific password** | This is a separate password, made just for Postern. Your real Apple password is never asked for and never stored — and pasting it here fails. |
| **push vs poll** | Your phone sends data to Postern when it decides to. Postern cannot ask for it, so there is no **Sync now** button. |
| **envelope** | Postern stores who sent it, the subject, the dates and the preview line. It never stores the message text. |
| **`.env`** | `.env` is the settings file beside `docker-compose.yml`. Create it if it is not there. The leading dot makes it invisible in Finder and File Explorer. |
| **a hosted agent** | An AI app that runs on a company's servers, like claude.ai or ChatGPT. It can never reach your home network on its own. |
| **Certificate Transparency** | A public list of every secure-website certificate ever issued. Anyone can read it, and entries cannot be removed. |
| **fail-closed boot** | If Postern cannot open the vault at start-up, it refuses to start rather than starting broken. |
| **`raw`** | `raw` is the untouched copy of what the source sent. Its names, units and signs differ from the columns beside it. |
| **rows the source deleted** | rows the source has deleted — never "tombstone" |
| **Item / Link** | Item and Link are Plaid's words. An Item is one bank connection at Plaid. Link is Plaid's connect-your-bank window. |
| **key custody** | Either you hold the master key or Postern does. Which one it is decides half of this page. |

## 4 · How this is enforced

- **W1** — any concept with two names in the built site fails review.
- **W9** — every quoted control traces to a `file:line` in `apps/web/src`, or to a
  dated witness for a third-party screen.
- A term added to column 1 of §1 must be added here **before** it is used, not
  after.
