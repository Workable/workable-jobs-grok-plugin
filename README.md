# Jobs by Workable

Search published jobs and manage your candidate profile on [Jobs by Workable](https://jobs.workable.com).

Installing the plugin connects Grok to `https://jobs.workable.com/mcp`. Job search, job details, companies, and locations work immediately. Your profile, applications, recommendations, recent searches, and withdrawing an application ask you to sign in once in the browser. There is no API key to paste.

## Tools

No sign-in:

- `search_jobs` — search published jobs
- `get_job` — one job by its id
- `get_company` — a company and its open jobs
- `get_job_locations` — cities and countries where jobs are listed

After you sign in:

- `get_my_profile` — your candidate profile
- `update_my_profile` — update your name, phone, location, education, or experience
- `get_my_applications` — jobs you have applied to
- `get_recommendations` — jobs matched to your profile
- `get_recent_searches` — recent search terms
- `withdraw_application` — withdraw an application that can still be withdrawn

Withdrawing an application cannot be undone from here.
