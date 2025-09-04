# Git PR Workflow (protected main)

Prereqs: branch protection requires status check 'test'.

Workflow:
1) git fetch origin && git reset --hard origin/main
2) git switch -c <branch>
3) commit changes
4) git push -u origin <branch>
5) gh pr create -t "<title>" -b "<why/what>" --base main --head <branch>
6) gh pr checks <number> # wait for Node CI/test
7) gh pr merge <number> --squash --delete-branch
8) git switch main && git fetch origin && git reset --hard origin/main

Notes:
- No direct pushes to main; CI must run on PR.
- Keep branches short-lived.
- If local/remote diverge, save work: git branch backup-main-local
- YAML: generate via base64, CRLF newlines, 2/4/6 indentation.
