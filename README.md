# OLX Skills

Publish OLX listings with ChatGPT / Codex. Provide your item details and photos, and let the agent guide you through the listing form, check the preview, submit the listing, and report its actual status.

This repository focuses on practical OLX workflows, starting with sale listings in Polish and English.

## Supported and tested harness

**Supported / tested harness: ChatGPT / Codex**, using browser control through `cua_repl`.

The tested setup uses a signed-in Chrome browser connected to ChatGPT / Codex, with file upload support. A text-only chat or a harness without these browser tools cannot run the complete workflow.

**Tested marketplace: OLX Poland (`olx.pl`).** The skills account for local marketplace differences, but other OLX countries have not been tested. Polish and English identify the conversation language; they do not select a country or automatically translate your listing text. Other harnesses are currently unsupported and untested.

## Choose your language

| Skill | Conversation language | Workflow |
| --- | --- | --- |
| [olx-sell-add-pl](skills/olx-sell-add-pl/SKILL.md) | Polish | Prepare, publish, and verify an OLX sale listing. |
| [olx-sell-add-en](skills/olx-sell-add-en/SKILL.md) | English | Prepare, publish, and verify an OLX sale listing. |

Each version is a separate skill with its own `SKILL.md`. Install the version you prefer, or invoke it explicitly if you install both. The repository contains skill instructions; browser tools are provided by your ChatGPT / Codex environment.

## What the skills handle

- Collect the title, description, price, photos, location, and contact preferences.
- Generate a description when requested, using supplied facts and visible photo details.
- Fill category attributes, select the location, and preserve photo order.
- Check the listing preview and publish within the scope you requested.
- Verify submission and report the listing link, price, and actual status, including pending moderation.

The skills ask for missing information and do not impose a default city, contact method, shipping promise, or currency. Paid promotion, listing fees, automatic renewal, and OLX delivery services require your authorization.

## Example requests

Attach your photos and provide the item details alongside the request.

**Polish**

```text
Użyj $olx-sell-add-pl. Wystaw te felgi na OLX Polska za 800 PLN.
Tytuł: Felgi aluminiowe 16 cali.
Wygeneruj opis na podstawie podanych informacji i zdjęć.
Lokalizacja: Poznań, Stare Miasto. Kontakt: czat OLX.
Odbiór osobisty. Pierwsze zdjęcie ma być główne.
```

**English**

```text
Use $olx-sell-add-en. List these wheels on OLX Poland for 800 PLN.
Title: 16-inch alloy wheels.
Generate a description from the supplied details and photos.
Location: Poznań, Stare Miasto. Contact: OLX chat.
Collection only. Use the first photo as the main photo.
```

This is a community project and is not affiliated with or endorsed by OLX.
