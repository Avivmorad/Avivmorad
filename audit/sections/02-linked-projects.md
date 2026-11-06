# Linked projects (from README)

| Project | Visibility | Demo / repo | Stack hints (from README) |
| --- | --- | --- | --- |
| MailPriority | Private repo; public demo | https://mail-priority.vercel.app/ | Next.js, TypeScript, Gmail API, Supabase/PostgreSQL, LLM structured outputs, OAuth, RLS |
| InterviewPilot AI | Public | https://github.com/Avivmorad/InterviewPilot-AI · https://interviewpilot-ai-bice.vercel.app | React, TypeScript, Express, Gemini/Groq fallback, Zod, evals |
| Banger or Bot | Public | https://github.com/Avivmorad/Banger_or_Bot · https://banger-or-bot.vercel.app | Next.js, Supabase Realtime, server-authoritative scoring, Vitest, Playwright |
| Agent-Biz | Private | (no public URL in README) | Python, GitHub Actions, GitHub Issues, six-agent workflow, human approval gates |

## Implication for agents

Agents working **in this directory** should treat README links as the source of truth for where real code lives. Environment builds and plugins on the cloud VM apply to any repo checked out here, but dependency install scripts would be no-ops until application code is added.
