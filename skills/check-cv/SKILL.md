---
name: check-cv
description: Review one of the user's TakeMeUp CVs with TakeMeUp's free checks — ATS compatibility, GDPR/personal-data risk for the target country, the six-second recruiter skim, and bullets that list duties instead of results — and turn the findings into a short, prioritised fix list. Use when the user asks if their CV is good, ATS-friendly, or ready to send.
argument-hint: "[CV name]"
---

# Check a CV with TakeMeUp

Use the TakeMeUp MCP tools. If the user isn't signed in, tell them to run `/mcp`, choose **takemeup** and sign in.

1. Pick the CV: `list_my_takemeup_cvs`, and ask which one if there are several (or use `$ARGUMENTS`).
2. Run the free checks — they don't use AI and cost nothing:
   - `analyze_takemeup_cv_ats` — the 0–100 score and its findings.
   - `check_takemeup_cv_gdpr` — personal fields that are risky for the CV's country.
   - `check_takemeup_six_second` — the terms a recruiter should see in the top third of page 1; compare them with `get_takemeup_cv_preview`.
   - `find_takemeup_weak_achievements` — bullets that describe duties instead of results.
3. Report in this order: the three changes that matter most, then the rest briefly. Quote the user's own bullet when you suggest a rewrite, and don't invent numbers — ask the user for the real ones.
4. Offer to apply the fixes. If they agree, `get_takemeup_cv`, change only those parts, and `save_takemeup_cv` with the complete CV. Re-run the ATS check and show the new score.

The PRO checks (`check_takemeup_resume_aging`, `detect_takemeup_buzzwords`, `run_takemeup_authenticity`) are optional extras. If one returns a gate, say so in one line and carry on with the free results.
