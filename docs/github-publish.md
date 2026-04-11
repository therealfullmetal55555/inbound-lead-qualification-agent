# Publish this project to GitHub

I cannot authenticate to or push to your GitHub account from this workspace. These commands publish the local project after you create an empty GitHub repository.

1. On GitHub, create a repository named `inbound-lead-qualification-agent`. Choose **Private** initially if you plan to add real configuration, and do not initialize it with a README.
2. In a terminal, change to this project folder and inspect the files:

   ```bash
   cd inbound-lead-qualification-agent
   git status --short
   find . -maxdepth 3 -type f -print
   ```

3. Initialize and commit the sanitized scaffold:

   ```bash
   git init -b main
   git add README.md compose.yaml .env.example .gitignore docs tests workflows
   git diff --cached --stat
   git commit -m "Add inbound lead qualification agent portfolio scaffold"
   ```

4. Add your repository URL and push. Replace `<YOUR_GITHUB_USERNAME>` with your own username:

   ```bash
   git remote add origin https://github.com/<YOUR_GITHUB_USERNAME>/inbound-lead-qualification-agent.git
   git push -u origin main
   ```

Use Git Credential Manager or GitHub CLI to authenticate. Do not put a personal access token in a command, file, or chat. If you have already created a remote, use `git remote -v` first and avoid adding a second `origin`.

Before making the repository public, confirm `.env` is not tracked (`git status --short --ignored`), scan for secrets, and remove any real lead data or sensitive screenshots. Add the validated n8n exports only after following `workflow-export.md`.
