<p align="center">
  <img src="assets/logo.png" alt="TakeMeUp.cv" width="96" height="96">
</p>

<h1 align="center">TakeMeUp.cv for Claude — CV &amp; Resume Builder</h1>

<p align="center">
  Build, check and tailor real CVs and resumes from Claude — in the right format for the country you're applying in.<br>
  <a href="https://takemeup.cv/en/guides/build-cv-with-claude">How it works</a> ·
  <a href="https://takemeup.cv">takemeup.cv</a> ·
  <a href="https://takemeup.cv/en/privacy">Privacy</a>
</p>

---

[TakeMeUp.cv](https://takemeup.cv) is a CV and resume builder for Europe. It knows each country's CV conventions —
whether a photo, date of birth or nationality belongs on the CV, and how dates are written — in 14 languages. With this
plugin, Claude can:

- **write and edit your CV** from a file you attach or from what you tell it, in ATS-friendly templates, and show a preview;
- **check it for free**: ATS (applicant tracking system) score, GDPR and personal-data risk, the six-second recruiter skim,
  and weak achievement bullets;
- **tailor it to a job ad**, with job matching, an AI rewrite, a cover letter and interview prep (PRO);
- **translate it** into another language as a new CV, export **Europass**, and turn it into a **LinkedIn profile** (PRO);
- **track your job applications** with statuses and follow-up dates, and let verified recruiters find your CV;
- give you a **PDF or Word download link** under your plan.

This plugin connects Claude to TakeMeUp's **hosted** [Model Context Protocol](https://modelcontextprotocol.io) server,
so Claude works on your actual CV on your TakeMeUp account instead of text in a chat. There's nothing to install or run:
the server runs at TakeMeUp. You **sign in to TakeMeUp** (OAuth) the first time; Claude never sees your password.

| | |
| --- | --- |
| **Endpoint** | `https://takemeup.cv/api/mcp` |
| **Transport** | Streamable HTTP |
| **Sign-in** | OAuth with your TakeMeUp account (you can create a free one while signing in) |
| **Plan** | The same as on the website: building, editing, previewing, the free checks and the tracker (5 jobs) are free; downloading a CV needs a one-time purchase for that CV or PRO; the AI features need PRO. Claude never pays or subscribes for you. |

## Skills

| Skill | What it does |
| --- | --- |
| `build-cv` | Builds or updates a CV from an attached file, from what you tell Claude, or from a role starter — in the target country's format — then previews it and gives you a download link. |
| `check-cv` | Runs the free checks (ATS, GDPR, six-second skim, weak achievements) and turns them into a short fix list, then applies the fixes you agree to. |
| `tailor-to-job` | Compares your CV with a job ad, adjusts it without inventing experience, optionally writes a cover letter and interview prep, and adds the job to your tracker. |
| `job-tracker` | Goes through your applications: what's waiting for a reply, which follow-ups are due, and keeps statuses current. |

## Tools

54 tools. Read-only tools are marked; tools that change existing data (marked *changes data*) always ask first.

| Area | Tools |
| --- | --- |
| Guides and conventions (read-only) | `list_takemeup_guides`, `search_takemeup_guides`, `get_takemeup_guide`, `list_takemeup_cv_templates`, `get_takemeup_locale_cv_rules`, `get_takemeup_pricing`, `list_takemeup_addons` |
| Your CVs and plan (read-only) | `list_my_takemeup_cvs`, `get_takemeup_cv`, `get_my_takemeup_billing`, `get_takemeup_ai_consent`, `get_takemeup_download_access`, `get_takemeup_addon_runs`, `get_takemeup_cv_preview`, `export_takemeup_cv_yaml`, `export_my_takemeup_data` |
| Free checks (read-only) | `analyze_takemeup_cv_ats`, `check_takemeup_cv_gdpr`, `check_takemeup_six_second`, `find_takemeup_weak_achievements` |
| Build and edit | `create_takemeup_cv`, `create_takemeup_cv_from_role`, `save_takemeup_cv` *changes data*, `set_takemeup_cv_template` *changes data* |
| AI features (PRO) | `rewrite_takemeup_cv`, `generate_takemeup_cover_letter`, `match_takemeup_cv_to_job`, `run_takemeup_interview_prep`, `explain_takemeup_career_gaps`, `run_takemeup_career_gps`, `check_takemeup_resume_aging`, `detect_takemeup_buzzwords`, `run_takemeup_authenticity`, `generate_takemeup_cv_summary`, `generate_takemeup_linkedin`, `translate_takemeup_cv`, `run_takemeup_market_pulse`, `run_takemeup_one_click_cv`, `roast_takemeup_cv` |
| Jobs | `extract_takemeup_jd_from_url`, `list_my_takemeup_applications`, `get_takemeup_application`, `add_takemeup_application`, `update_takemeup_application` *changes data*, `subscribe_takemeup_job_alerts` |
| Download and export | `get_takemeup_download_link` (a PDF or Word link valid 10 minutes), `export_takemeup_europass` (PRO) |
| Sharing and recruiters | `create_takemeup_share_link` *changes data*, `get_takemeup_qr_code`, `create_takemeup_stealth_cv`, `revoke_takemeup_stealth_cv` *changes data*, `get_takemeup_get_found`, `set_takemeup_get_found` *changes data*, `answer_takemeup_recruiter` *changes data* |

**Not possible through Claude, by design:** paying or changing your plan, deleting a CV or your account, and giving
consent for TakeMeUp's AI processing. Those stay on the website.

## What this plugin runs and sends

- It runs nothing on your computer. It only tells Claude where TakeMeUp's MCP server is (`.mcp.json`) and adds the four
  skills above.
- Claude sends your requests to `https://takemeup.cv/api/mcp`, signed in as you, and gets back the results — which can
  include your CV's personal data. TakeMeUp's own AI features run on TakeMeUp's servers with Anthropic as its processor,
  only after you've given consent on the website.
- What Claude does with those results is handled by Anthropic under its own terms; it's not TakeMeUp's subprocessor and
  acts at your direction.
- TakeMeUp keeps a record of each connected assistant (which one, when it was used, whether it can make changes) —
  never its access tokens. See and disconnect assistants on your TakeMeUp account page under **Connected assistants**.
- Limits: 120 requests per assistant per 10 minutes; the AI features keep their own daily limits.

Full details: [Privacy policy — AI assistants you connect](https://takemeup.cv/en/privacy).

## Install

In Claude Code:

```
/plugin marketplace add dsdev-d/takemeup-mcp
/plugin install takemeup@takemeup
```

Then run `/mcp`, choose **takemeup** and sign in. Without the plugin you can add just the server:
`claude mcp add --transport http takemeup https://takemeup.cv/api/mcp`.

## Support

contact@takemeup.cv · [takemeup.cv](https://takemeup.cv)

## License

[MIT](LICENSE)
