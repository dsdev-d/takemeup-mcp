---
name: build-cv
description: Build or update a CV on TakeMeUp.cv — from an attached CV file, from what the user tells you, or from a role starter — in the right format for the country it's for, then preview it and give a download link. Use when the user wants to create, rewrite into, or move their CV to TakeMeUp.
argument-hint: "[target country or job]"
---

# Build a CV with TakeMeUp

Use the TakeMeUp MCP tools. If a tool says the user isn't signed in, tell them to run `/mcp`, choose **takemeup** and sign in to TakeMeUp (they can create a free account there), then try again.

## 1. Where is the CV going?

Ask which country (and language) the CV is for, unless `$ARGUMENTS` or the conversation already says. Call `get_takemeup_locale_cv_rules` for that country and follow it: whether a photo, date of birth, nationality or marital status are expected, and the date format. Tell the user in one line what applies, for example that a German CV usually has a photo and a French one usually doesn't need a date of birth.

## 2. Start from what exists

- Call `list_my_takemeup_cvs`. If the user has a CV there already, ask whether to update it or start a new one.
- **The user attached a CV file:** read it yourself and keep their facts exactly — employers, titles, dates, degrees. Don't invent anything. Then `create_takemeup_cv` (pick a template with `list_takemeup_cv_templates` if the user cares about the look; the default is fine otherwise) and `save_takemeup_cv` with the complete CV.
- **No file:** ask for the essentials (contact details, last roles with dates and 2–4 results each, education, skills, languages). For a common hands-on role (driver, warehouse, healthcare assistant, cleaner, retail, food service), `create_takemeup_cv_from_role` gives a filled starter to edit.
- Updating: `get_takemeup_cv` first, change only what the user asked, and save the complete CV with `save_takemeup_cv`.

Write bullets as results, with numbers where the user gave them. Never add skills, employers or figures the user didn't give you.

## 3. Check and show it

Run `analyze_takemeup_cv_ats` and `check_takemeup_cv_gdpr` (both free). Fix what's clearly fixable with the user's agreement, and mention the rest. Then call `get_takemeup_cv_preview` to show page 1, and give the editor link from the result.

## 4. Download

When the user wants the file, call `get_takemeup_download_link` (format `pdf`, or `docx` for Word). If it returns a gate (a one-time purchase for this CV, or PRO), tell the user that plainly and give them the links from the result. Don't push them to buy. The link works for 10 minutes.
