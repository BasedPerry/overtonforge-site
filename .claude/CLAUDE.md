# overtonforge-site

Source for https://overtonforge.app (GitHub Pages from `main`, served as-is: `.nojekyll`). Anything pushed to `main` goes live, so cloud sessions never push `main`.

## Cloud sessions

For Claude sessions running in the cloud, without access to Brandon's Mac. Keeps cloud and local work in sync.

- **You can't see** the Mac, its notes, task lists, Xcode, or any hardware. Never say you checked or updated them. Anything that needs a Mac or a device goes in your handoff as "not verified".
- **Branches:** work on `claude/<short-topic>`. If one already exists for this work, continue it. Never commit to or push `main` or a release branch, never force push, never delete branches or files you didn't create. Don't merge, open a PR, publish, or deploy unless Brandon asks in this session.
- **No secrets.** In public repos, no personal paths or names either.
- **Before you stop, write a handoff** and push your branch. One new file per session, never edit an old one:

  `.claude/handoffs/YYYY-MM-DD_<topic>.md` with these sections: **Done** (with commit hashes), **Verified / not verified**, **Decisions** (who decided), **Brandon** (only he can do these: tests, reviews, merges), **Now.md / hub update** (one or two plain lines). Frontmatter: `kind: handoff`, `repo`, `branch`, `created`, `status: open`. Plain bullets for tasks; no `^r-` reminder IDs.

- The Mac's `session-close` reads these handoffs and updates the project notes. Full rules: `cloud/CLOUD_SESSION_RULES.md` in `BasedPerry/claude-os-v2` (private; this section is enough if you can't reach it).
