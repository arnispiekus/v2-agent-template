# Set up your brain

## 1. Accounts and engines

Use GitHub, its `gh` command-line tool and one or two agent harnesses. Sign in
yourself. Choose two engines from different families: one builds and the other
checks. Claude Code and Codex are possible harnesses. With one engine, a person
checks. Never put credentials in the repository or chat.

Install `python3` before running the fake-key recipe in step 8.

## 2. Create a private brain

Create a private repository from the template, clone it and work from that project
folder. Use `<your-account>` wherever an account is required. The owner approves
each invitation. A person reviews files and metadata before sharing.

Mark the source repository as a template in its settings, then use:

```sh
gh repo create <name> --private --template <your-account>/<template-repo>
```

## 3. Record the available kit

Copy `KIT.example.md` to `KIT.md`. Ping each model with a harmless request. Mark
VERIFIED only after observing it work, with a date and safe evidence. Untested
entries remain REPORTED. Never record credentials, machine paths or hook bodies.
`KIT.md` is ignored by git on purpose, so each machine keeps its own.

## 4. Choose a merge policy

Default: a person approves every merge after independent review at the exact
commit. Replace `<your-account>` in `.github/CODEOWNERS`. Where available, enable
rules under Settings, Rules, Rulesets requiring pull requests, checks and
code-owner review. Require these checks: "Secrets in new commits", "Source rules",
"Generic privacy patterns" and "Workflow security". CODEOWNERS alone does not
enforce review. Check what the account plan supports.

New commits should use the noreply email and UTC dates, because the privacy check
fails on anything else. Set the email with `git config user.email` and commit with
`TZ=UTC`. Commits that GitHub makes itself (the merge and "Update branch" buttons)
are checked for the author email only, so make the noreply address your commit
email in the account's email settings before merging.

Optional: the owner may explicitly authorise small changes after the other engine
checks and a recorded stop window expires. Define small, the window, its monitor
and exclusions first. Agents never merge their own work. Security, access,
deletion and sensitive-data changes require a person.

## 5. Create the first project

Copy `projects/_template/` to `projects/<project>/` and fill all seven files. GOAL
names the person and their own measure of done. Use a role or placeholder in
shared files. Fix reference inputs and expected figures before tuning; check
those figures in the project's code repository.

## 6. Prepare the code repository

Add AGENTS.md, the single-line CLAUDE.md pointer and the pull request template.
Adapt project commands and ownership. Keep product code there and current
decisions and state in the brain.

## 7. Open the first issue

Use the task form: goal, scope, output location, done test and exclusions. The
owner assigns it or names the app allowed to assign agent work. Inspect raw issue
Markdown for hidden comments before starting.

## 8. Run the loop and exercise the secret check

Complete one bounded issue through build, independent check and person approval.
After owner authorisation for a separate disposable test, make a throwaway branch
and pull request. Run this only on that branch. It builds synthetic material at
run time; never print the generated value or paste it into chat.

```sh
git switch -c check-secret-detection
python3 - <<'PY'
from pathlib import Path
from secrets import choice
from string import ascii_letters, digits

prefix = ''.join(chr(code) for code in (103, 104, 112, 95))
payload = ''.join(choice(ascii_letters + digits) for _ in range(36))
Path('secret-check.txt').write_text(prefix + payload + '\n')
PY
git add secret-check.txt
git commit -m "Exercise secret detection"
```

Push the disposable branch and open its pull request only with owner authority.

```sh
git push -u origin check-secret-detection
gh pr create --base main --head check-secret-detection --title "Exercise secret detection" --body "Disposable synthetic secret check. Close unmerged after recording the finding."
```

The gitleaks log redacts the value. Match the planted string by its rule id, file
name and line, not by the value or merely a red status. Record only rule id, file,
line, commit and check result. If the finding is absent, the proof failed; never
weaken the check. Close the pull request unmerged and delete its branch:

```sh
gh pr close check-secret-detection --delete-branch
```

Never merge the test file.

## 9. Prove a fresh start

Start a session on the other harness. With one harness, use a fresh session with
no chat history. Answer [the six questions](playbooks/hand-over.md) from files
alone, citing a file for each. Record gaps and repair files before claiming success.

## 10. Optional helpers and final proof

An always-on server and outside agents are optional. Use the agent-task form and
grant only needed access. The owner handles authentication and consequential acts.

Before sharing, run a private word-list scrub locally; never commit that list.
Check names, projects, hosts, paths, accounts, personal channels, private tool
names and internal working vocabulary. Inspect commit metadata, branch names and
pull request text too. Confirm noreply authorship without silently changing it.

Proof run 1 needs green CI, a clean private scrub, the six-question fresh start
and the observed disposable secret-check failure with the pull request closed
unmerged. Date the README receipt only after all four are evidenced.
