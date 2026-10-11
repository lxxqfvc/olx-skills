# agent-skills

Practical skills for AI agents — starting with everyday tasks.

## Available skills

| Skill | Conversation language | Purpose |
| --- | --- | --- |
| [olx-sell-add-pl](skills/olx-sell-add-pl/SKILL.md) | Polish | Publish a sale listing on the user's local OLX marketplace. |
| [olx-sell-add-en](skills/olx-sell-add-en/SKILL.md) | English | Publish a sale listing on the user's local OLX marketplace. |

Each language version is an independently installable skill in its own directory, with a matching frontmatter name. Install the version you use, or select it explicitly if both are installed. The language suffix does not select a country or translate supplied listing text.

Both versions require a browser environment exposing `cua_repl`, its current documentation, and file upload support. Other harnesses need an equivalent browser integration and adapted tool instructions. These workflows have been exercised on OLX Poland; other markets require validation against their current local forms. No default city, shipping promise, contact method, or currency is imposed.

This is a community project, not an official OLX integration.
