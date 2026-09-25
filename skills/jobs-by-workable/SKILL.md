---
name: jobs-by-workable
description: |
  Search jobs and manage a candidate profile on the Jobs by Workable job board.
  Use this skill when the user asks to find jobs, look up a posting or company,
  see where jobs are located, get job recommendations, view or update their
  candidate profile, list applications, or withdraw an application.
---

# Jobs by Workable

This plugin connects to the official hosted MCP server at `https://jobs.workable.com/mcp`. Prefer its tools over web search for anything on the Jobs by Workable board. Only report jobs, companies, salaries, and locations the tools return. Never invent them. When you mention a job, include its URL when the tool returned one.

## Authentication

`search_jobs`, `get_job`, `get_company`, and `get_job_locations` work without signing in.

`get_my_profile`, `update_my_profile`, `get_my_applications`, `get_recommendations`, `get_recent_searches`, and `withdraw_application` act on the signed-in candidate. The first protected call opens a browser sign-in. If a tool returns 401 or an auth error, ask the user to finish that sign-in, then retry. Never ask for a password, token, or API key in chat.

## Which tool

| Ask | Tool |
| --- | --- |
| Find jobs by keywords, location, workplace, employment type, or recency | `search_jobs` |
| Full posting, requirements, benefits, or apply URL | `get_job` with the job `uid` |
| A company and its open jobs | `get_company` with the company id |
| Cities or countries to narrow a search | `get_job_locations` |
| Jobs matched to the user's profile | `get_recommendations` |
| Popular search terms near the user | `get_recent_searches` |
| The user's candidate profile | `get_my_profile` |
| Change name, phone, location, education, or experience | `update_my_profile` |
| Jobs the user already applied to | `get_my_applications` |
| Cancel one application | `withdraw_application` |

`search_jobs` already returns full details for each match. Call `get_job` when you need one posting, or an apply URL, rather than to re-fetch every result.

Pass `nextPageToken` back with the same filters to page `search_jobs` and `get_recommendations`. `get_my_applications` uses a 1-based `page`.

## Writes

Confirm with the user before `update_my_profile` or `withdraw_application`. Show the fields or the application title you are about to change. Do not run either unprompted.

`withdraw_application` cannot be undone from the MCP. Only call it when `get_my_applications` returned `isWithdrawable: true` for that `applicationId`. If `isWithdrawable` is false, say the application cannot be withdrawn here and can still be withdrawn from the confirmation email sent when applying.

Recruiting-pipeline stages (in review, interviewed, offered, rejected) are not available. Do not infer them.
