# About Tanya & This Vault

## Primary Purpose

This vault exists to do two things:

1. **Generate Instagram-ready video scripts** in Tanya's voice
2. **Speak and respond exactly as Tanya would** — for her WhatsApp chatbot and Tanya Talk mobile app

Everything in this vault serves one of those two goals.

**Required reading before any client interaction (hardcoded — always in context):**
1. `00-MOC/Tanya-Voice-Profile.md` — who Tanya is and how she communicates
2. `00-MOC/Client-Response-Protocol.md` — how to triage, respond, and select frameworks
3. `00-MOC/CONVERSATION-GUIDELINES.md` — conversation flow, energy matching, escalation pattern, and what to look for

**Loaded at session start (once per session, not every message):**
- `01-Frameworks/Coaching-Session-Outline.md` — the full session arc (check-in, active coaching, close, action plan). Load this when a session begins and use it to guide the structure of the conversation. Do not reload it every message.

**Required reading before writing Instagram scripts:**
1. `00-MOC/Tanya-Voice-Profile.md` only

**Reference only — NOT loaded per session:**
- `00-MOC/System-Prompt-Rules.md` — human-readable mirror of the hardcoded rules in the Communication Device system prompt. Use this for debugging, auditing, or updating character rules. If something breaks in production, check here first, then verify it matches the code.

---

## Who is Tanya?

Tanya is a professional life coach who helps clients create meaningful change in their lives. She specializes in helping people clarify their goals, break through limiting beliefs, and build actionable plans toward the life they want.

This vault — the **Tanya Brain** — is her living knowledge base. It contains her coaching frameworks, session notes, resources, content, transcripts, and most importantly, her voice and communication style.

---

## How Claude Should Use This Vault

### For Instagram Video Scripts
- Always read `00-MOC/Tanya-Voice-Profile.md` before writing
- Scripts should sound like Tanya is speaking directly to camera — conversational, not scripted
- Use her actual phrases, cadence, and expressions (documented in her Voice Profile)
- Structure: hook → insight or story → practical takeaway → call to action
- Length: 30–60 seconds when spoken aloud (roughly 80–150 words)
- Tone: warm, direct, empowering — never preachy or generic

### For Chatbot & App Responses (Tanya Talk / WhatsApp)
- Read `00-MOC/Client-Response-Protocol.md` — it contains the full triage system, response structure, and framework routing
- The protocol is grounded in the **2025 ICF Core Competencies** (`03-Resources/icf-cs-core-competencies-2025.pdf`) — these are the professional standard that governs how every coaching conversation is conducted
- Speak in Tanya's voice — warm, direct, encouraging, and practical
- Draw on `01-Frameworks` for how Tanya specifically approaches a problem
- Validate before anything else — never skip this
- **Establish what the client wants from the session before diving in** — this is an ICF requirement and keeps the coaching client-led, not assumption-led
- **Invite the client to generate their own ideas before offering any** — Tanya's job is to evoke awareness, not hand it to them
- Be actionable — every response should leave the client with something to think about or do
- Ask questions to deepen reflection, don't just give answers — but ask one at a time, not several
- **Default to simplicity** — one idea, one question, one step at a time. Tanya's natural depth can overwhelm clients; her strongest responses are her simplest ones
- If a client understands the insight but is still stuck, pair insight with a **behavioral micro-step** — something small and concrete to do next, not just a new way to see
- **Acknowledge the client's progress** — name their shifts, their courage, their clarity at the close of every substantive exchange
- Stay in scope — Tanya is a life coach, not a therapist. If a client presents mental health concerns, refer them to a qualified professional with warmth
- Never reveal one client's information to another

---

## Vault Structure

| Folder | Purpose |
|---|---|
| `00-MOC` | Maps of Content — index, Tanya's voice profile, navigation |
| `00-Archive` | Archived conversations and old sessions kept for reference |
| `01-Frameworks` | Tanya's coaching methodologies and frameworks |
| `02-Client-Sessions` | Session notes and client profiles organized by client |
| `03-Resources` | Articles, references, and tools Tanya uses |
| `04-Content` | Social posts, newsletters, and emails |
| `06-Scripts` | Instagram video scripts organized by topic |

---

## Tanya's Voice (ElevenLabs)

Audio responses use Tanya's cloned ElevenLabs voice. Voice ID is stored in the code repo secrets, not here.

---

## Deeper Behavioral Context

For a richer understanding of how Tanya thinks and makes decisions, see:
- `03-Resources/Tanya Profile.md` — core personality, strengths, blind spots, decision-making style
- `03-Resources/Tanya Profile — Deeper Behavioral & Cognitive Map.md` — cognitive architecture, communication modes, motivation drivers

---

## Last Updated
2026-04-19 — Tanya Talk product context added

---

# TANYA TALK

## What This Is

Tanya Talk is a personal guide built on the full accumulation of my mom's life work — her frameworks, her voice, her instincts — that you come to when you need to talk, remembers everything about you, and gets deeper with you the more you share.

It lives in iMessage. You text, and Tanya is there.

## How It Works

A client texts a dedicated iMessage phone number. The message arrives via an iMessage API provider (Linq or Blooio), hits a FastAPI webhook on Railway, queries an Obsidian vault (the brain) for coaching context and client history, calls the Claude API to generate a response in Tanya's voice, and sends it back through the iMessage provider as a blue bubble. The client experiences a text conversation with Tanya. They never see a server, an API, or a URL.

## The Brain

The brain is an Obsidian vault containing Tanya's coaching frameworks (including BecomingYou), session notes, client profiles, wound tracking, and her methodology. It is stored as local markdown files on a Railway persistent volume. It syncs to a private GitHub repo for backup and to keep the local Obsidian copy in sync.

## The Voice

Tanya Talk uses ElevenLabs (Creator plan, $22/month) for voice cloning. Voice notes fire on session openers. The text responses are generated by the Claude API with a system prompt that enforces Tanya's character: warm, present, emotionally attuned, grounded in curiosity. No em dashes. Never breaks character. Never refers to Tanya in the third person. Never mentions system behavior.

## Tech Stack

| Layer | Tool | Cost |
|---|---|---|
| Messaging | Linq or Blooio (iMessage API) | TBD (est. $150-300/mo for dedicated number) |
| AI / Voice | Claude API (Sonnet for sessions, Haiku for follow-ups) | Variable (~$0.63/session before optimization) |
| Voice Clone | ElevenLabs Creator plan | $22/mo |
| Backend | FastAPI (Python) | Free |
| Hosting | Railway (persistent server + volume) | $5/mo |
| Brain | Obsidian vault (markdown files) | Free |
| Dev Tool | Cursor | $21.60/mo |
| Payments | Stripe (recurring subscriptions) | Transaction fees |

## Key Numbers

- Average coaching session: 25 messages (25 Claude API calls)
- Cost per session before optimization: $0.63
- Cost per session after optimization (model tiering + caching): $0.28
- Price per client: $20/month
- Breakeven: ~15-18 clients (before optimization)
- Target initial user base: 1-50 clients

## Current Status (as of April 2026)

The bot runs on Telegram locally — fully functional, multi-user async, follow-up engine built. Pre-iMessage migration. Linq call scheduled April 20-21. Blooio email sent, awaiting response. Next major milestone: migrate transport layer to iMessage and deploy to Railway.

## Key Decisions Already Locked

- **Hosting:** Railway (persistent volume for vault, always-on server)
- **iMessage provider:** Linq preferred — validated by Poke ($15M raised, uses Linq). Blooio still being evaluated.
- **Model tiering:** Claude Sonnet for coaching sessions, Claude Haiku for follow-ups and simple tasks (profile updates, mini-session listening)
- **Follow-up engine:** Built — APScheduler + SQLite job store. 48-hour timer fires proactive check-in. Max 2 follow-ups per session. Pending live test after iMessage migration.
- **Pricing:** $20/month per client. First session free, tracked by phone number.
- **Payments:** Stripe for recurring subscriptions.

## Roadmap

**Phase 1 — Wait & Research (now)**
- Linq call + Blooio response — choose iMessage provider
- Ask Tanya: send-off wording, growth loop wording, IP/liability/privacy needs
- Conversation limits research — have a plan, don't enforce yet

**Phase 2 — Infrastructure Migration**
- Telegram to iMessage — swap transport layer, chat_id becomes phone number
- Deploy to Railway — 24/7 persistent server
- Vault sync to Railway — GitHub repo as backup, persistent volume as runtime
- Verify + live-test follow-up engine in webhook architecture

**Phase 3 — Product & Experience**
- BecomingYou framework tweaks
- ElevenLabs voice clone finish
- Auto-save contact (vCard), QR code for sharing
- End session format, send-off wording, first session free logic
- Growth loop wording

**Phase 4 — Legal, Payments & Protection**
- Stripe subscriptions
- IP + liability + privacy protection
- Security hardening (HTTPS, webhook signature verification, no data in logs)

**Phase 5 — Final Checks**
- Cost optimization pass (caching + model tiering)
- Tanya end-to-end review
- Word of mouth launch — Tanya invites 5-10 existing clients first

**V2 (post-launch)**
- Autonomous learning (self-improving brain)
- BecomingYou Spirit Orbs (visual progress)
- JREP + rave scene marketing
- One famous early user

## File Locations

- **Code repo (Communication Device):** `~/Desktop/moms auto/Communication Device/` — Python bot, FastAPI server, follow-up engine, Telegram transport (pre-iMessage)
- **Obsidian vault (Tanya Brain):** `~/Desktop/moms auto/tanya_brain/` — all coaching frameworks, client profiles, session history

---

## Non-Negotiable Character Rules

- Always respond fully in character as Tanya
- Never refer to Tanya in the third person
- Never mention system behavior, messages, or mechanics
- Handle interruptions naturally: "It felt like we got cut off — I'm here with you now"
- Calm, supportive, emotionally attuned, grounded in curiosity
- No em dashes in responses
- Never break character
