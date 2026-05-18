---
title: "Client Hub"
type: hub
---

# Client Hub

> Central connection point for all clients. Links to every profile, session history, and the broader vault.
> Read a client's profile before any conversation. Update it after every session.

---

## Connected To

- [[02-Client-Sessions]] — Full session index + recurring themes → frameworks map
- [[Client-Response-Protocol]] — How to triage and respond
- [[CONVERSATION-GUIDELINES]] — Flow, energy matching, escalation pattern
- [[Tanya-Voice-Profile]] — Tanya's voice, phrases, and coaching style
- [[Framework-Map]] — All frameworks and how they connect

---

## Clients With Profiles

> Full memory layer — read before every conversation. All profiles stored by phone hash.

- [[02-Client-Sessions/Client Profiles/15ee3d91bb9777ac971c208fa739c525e04ac929764b7f08958286f96bbd17da|JC]] — 3 sessions
- [[02-Client-Sessions/Client Profiles/943a56bf2a00e77431161dd528b68d2c31814ada54fbf60be8ded1d93bd4d02d|hazel]] — 1 session
- [[02-Client-Sessions/Client Profiles/0e24a37278641ec18bce45cbb6aa6608b4186c0d1571b3068af2708210168dcc|jesse]] — 1 session
- [[02-Client-Sessions/Client Profiles/13cc5fc365e2fcdc06f903342111f62a78413d357d2fca99c8caa4481886cf88|Lindsay]] — 1 session

---

## All Clients — Session History

| Client | Sessions | Profile |
|---|---|---|
| [[02-Client-Sessions/15ee3d91bb9777ac971c208fa739c525e04ac929764b7f08958286f96bbd17da\|JC]] | 3 | [[02-Client-Sessions/Client Profiles/15ee3d91bb9777ac971c208fa739c525e04ac929764b7f08958286f96bbd17da\|Profile]] |

---

## Adding a New Client

New clients are created automatically when they text in for the first time. The bot:
1. Computes a SHA-256 hash of their phone number
2. Creates `02-Client-Sessions/{hash}/Session 1.md`
3. Creates `02-Client-Sessions/Client Profiles/{hash}.md` after session ends
4. Updates this hub and [[02-Client-Sessions]] automatically

---

*Last updated: 2026-05-18*