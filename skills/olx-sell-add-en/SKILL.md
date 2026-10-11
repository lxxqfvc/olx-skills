---
name: olx-sell-add-en
description: Publish sale listings on the user's local OLX marketplace from a title, description, price, and photos. Use for requests in English or an explicit request for the English version; language does not select the OLX country.
---

# olx-sell-add-en

Publish a listing on the user's OLX account and verify the submission result. Converse in English. The user's explicit settings for the current listing take precedence. Conversation language, OLX country, and listing language are independent settings. Preserve the language of supplied titles and descriptions; when generating a description, establish the listing language if the request does not make it clear.

## OLX market

Determine the country and local OLX website from the user's request or the open listing form. If the market is unclear, ask for the country or website address. Do not select olx.pl based on conversation language. Use the current local form: button labels, currencies, fields, and services may differ between markets. Do not assume features from OLX Poland are available elsewhere.

## Input

For each new listing, collect fresh information: title, description, photos, price, location, and preferred contact method. Determine the currency from the selected market and form; ask if unclear. Do not convert the price on your own. Do not reuse the previous item's price, attributes, description, or photos.

- Location: use the location supplied by the user or their explicitly established preference. Do not assume a default city. Ask if the location or a required district is missing.
- Contact: use the user's preferences and the options available on the local OLX website. If the user selects phone contact, retain the number from their account; do not invent a number. Ask for it if missing. Follow tool requirements for consent to disclose contact information; loading this skill alone does not authorize publication of contact details.
- Shipping: declare shipping only based on user information or explicit preferences. Do not automatically append a shipping or contact sentence. Do not invent costs, a carrier, or a shipping date. Mentioning shipping in the description does not authorize enabling an OLX delivery service.
- A price is required for a sale. Ask if it is missing. Do not estimate a price unless asked. Do not enable negotiable pricing without the user's instruction.
- Preserve the supplied photo order; the first photo is the main photo unless the user specifies otherwise.
- If the user provides only a title, **ask whether to generate a description or use one supplied by the user**. Do not generate it before receiving an answer. You may ask for the price and photos in the same question.
- When the user chooses a generated description, use supplied facts and visible photo details. Ask for material missing information. Do not invent working condition, history, dimensions, origin, or delivery terms.
- Preserve the user's title and description wording. Agree any material change required by OLX limits or validation with the user.
- If photos are missing, ask the user to attach them or identify the files. If the user wants a listing without photos, continue if the local OLX allows it.

## OLX form

Use the available OLX interface. For browser interaction, use `cua_repl` and its current API documentation. Reuse an open form if one exists; do not create a second listing for the same task. Do not store tab identifiers, form element identifiers, or login details in this skill.

1. Open the correct local OLX website and choose its add-listing action (for example, “Dodaj ogłoszenie” on OLX Poland). If login is required and cannot be completed in an authorized way, preserve the tab with `markHandoff()` and ask the user to log in. Return to the same form after confirmation. Changing extension settings can renew the connection and browser identifier; if the connection is unavailable, inspect the current inventory and recover the form tab without reloading it.
2. Enter the title, proceed, and check the suggested category. Change it if it does not match the item.
3. Enter the description, price, and required category attributes using user information and photos. Do not guess material unknown attributes.
4. Select the location **from the suggestions list**. Merely typing can leave the account's previous location selected. Verify the selected city and district in the form or preview.
5. Set available contact options according to the user's preference. If phone contact was selected, retain the number from the account. If the tool requires consent, ask for the specific number and local OLX website, without repeating consent already given.
6. Add photos. Read the `file-uploads` documentation before uploading. Start waiting for `filechooser` before clicking the upload button, then use `setFiles()` with absolute paths. Check multiple-file support and preserve the order. Verify the photo count and the local main-photo marker (for example, “GŁÓWNE” on OLX Poland) on the correct file.
7. If Chrome upload requires “Allow access to file URLs,” read `chrome-file-upload-troubleshooting` and provide the tool-required instructions. Preserve the form and resume upload after the user's confirmation. Do not publish without photos the user instructed you to include.
8. Check the preview: title, description, price and currency, main photo, attributes, and location. Do not enable paid promotion, automatic renewal, or a local OLX delivery service (for example, Przesyłki OLX in Poland) unless requested. Mentioning shipping in the description does not select such a service.

## Publication and result

An instruction to “list this on OLX” authorizes publication of the prepared listing within the requested scope. Do not add a generic publication confirmation if all required information and consents are available.

Choose the publication button in the local form (for example, “Dodaj ogłoszenie”). If OLX offers promotion, choose the option without promotion and confirm free publication. The Polish labels “Nie promuj” and “Tak, dodaj” are examples; identify their equivalents in the current interface. If publication requires a fee, stop before payment and report the exact amount and currency; do not purchase a package or promotion without authorization.

After submission, check the activation confirmation or the account's listings page (for example, “Twoje ogłoszenia”). If the result is uncertain, first check locally available statuses, including active, pending, and unpaid listings; do not submit again until you establish whether the listing already exists.

A confirmation message does not always mean public visibility: on OLX Poland, “Ogłoszenie aktywowane” may still correspond to a listing under “Oczekujące.” Report the actual status instead of claiming the listing is publicly visible. Do not wait unnecessarily for moderation after submission has been confirmed.

In the final response, provide the listing link from the interface, the price with currency, and its actual status on the local OLX website. Briefly confirm the market, location, contact method, and main photo. Save and embed a confirmation screenshot according to browser documentation, without unnecessary private information. Preserve the result tab with `markDeliverable()`.
