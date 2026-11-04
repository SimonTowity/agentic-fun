# agentic-fun

## Daily news digest

Emails a digest on agentic software development every morning at 08:00 Copenhagen time. A GitHub Actions
workflow runs `news_digest.py`, which has Claude search the web and write the
digest, then sends it through Resend.

### Setup

Add these under **Settings > Secrets and variables > Actions > New repository secret**:

| Secret | Value |
|---|---|
| `ANTHROPIC_API_KEY` | API key from console.anthropic.com |
| `RESEND_API_KEY` | API key from resend.com, with "Sending access" permission |
| `DIGEST_TO` | Address to send to. Must be your Resend account's address until you verify a domain |

To test it, open **Actions > Daily news digest > Run workflow**. A manual run
sends straight away.

### Changing it

- **Topics and length:** edit `TOPICS` and `STORIES_PER_TOPIC` in `news_digest.py`.
- **Sender:** once you have a verified domain in Resend, set `DIGEST_FROM` in the workflow.

### Good to know

- GitHub can start scheduled runs late, so the email may occasionally arrive after 08:00.
- GitHub disables scheduled workflows after 60 days without repo activity. Re-enable
  it from the Actions tab if the emails stop.
- If a run fails, no digest is sent and GitHub notifies you of the failed run.
