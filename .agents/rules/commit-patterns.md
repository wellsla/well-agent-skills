---
trigger: model_decision
description: When generating commit message
---

# Commit Patterns 📜

According to the Conventional Commits documentation, semantic commits are a simple convention to be used in commit messages. This convention defines a set of rules for creating an explicit commit history, which makes it easier to build automated tools.

These commits will help you and your team easily understand what changes were made in the committed code snippet.

This identification happens through a word and emoji that indicates whether the committed change relates to a code modification, package update, documentation, visual change, test, and so on.

---

## Type and Description 🦄

A semantic commit has the structural elements below (types), which communicate the intent of your commit to anyone reading your code.

- **feat** – Commits of type `feat` indicate that your code snippet is including a new feature (relates to the MINOR in semantic versioning).
- **fix** – Commits of type `fix` indicate that your committed code snippet is solving a problem (bug fix), (relates to the PATCH in semantic versioning).
- **docs** – Commits of type `docs` indicate that there were changes in documentation, such as in your repository's README. (Does not include code changes).
- **test** – Commits of type `test` are used when changes are made to tests, whether creating, modifying, or deleting unit tests. (Does not include code changes).
- **build** – Commits of type `build` are used when modifications are made to build files and dependencies.
- **perf** – Commits of type `perf` serve to identify any code changes related to performance.
- **style** – Commits of type `style` indicate that there were changes related to code formatting, semicolons, trailing spaces, lint, etc. (Does not include code changes).
- **refactor** – Commits of type `refactor` refer to changes due to refactoring that do not alter functionality, such as a change in how a part of the screen is processed but maintaining the same functionality, or performance improvements from a code review.
- **chore** – Commits of type `chore` indicate updates to build tasks, admin configurations, packages, etc., such as adding a package to gitignore. (Does not include code changes).
- **ci** – Commits of type `ci` indicate changes related to continuous integration.
- **raw** – Commits of type `raw` indicate changes related to configuration files, data, features, and parameters.
- **cleanup** – Commits of type `cleanup` are used to remove commented-out code, unnecessary snippets, or any other form of source code cleaning, aiming to improve readability and maintainability.
- **remove** – Commits of type `remove` indicate the deletion of obsolete or unused files, directories, or features, reducing the size and complexity of the project and keeping it more organized.

---

## Recommendations 🎉

- Add a type consistent with the title of the content.
- We recommend that the first line should have a maximum of 4 words.
- Use the commit description to describe things in detail.
- Use an emoji at the beginning of the commit message representing what the commit is about.
- Links must be added in their most authentic form, i.e., without URL shorteners or affiliate links.

---

## Commit Complements 💻

- **Footer:** information about the reviewer and the card number in Trello or Jira. Example: `Reviewed-by: Elisandro Mello Refs #133`
- **Body:** more precise descriptions of what is contained in the commit, presenting impacts and the reasons why the changes were made to the code, as well as essential instructions for future interventions. Example: `see the issue for details on typos fixed.`
- **Descriptions:** a succinct description of the change. Example: `correct minor typos in code`

---

## Emoji Patterns 💈

|Commit Type|Emoji|Keyword|
|---|---|---|
|Accessibility|♿ `:wheelchair:`||
|Adding a test|✅ `:white_check_mark:`|`test`|
|Updating a submodule version|⬆️ `:arrow_up:`||
|Rolling back a submodule version|⬇️ `:arrow_down:`||
|Adding a dependency|➕ `:heavy_plus_sign:`|`build`|
|Code review changes|👌 `:ok_hand:`|`style`|
|Animations and transitions|💫 `:dizzy:`||
|Bugfix|🐛 `:bug:`|`fix`|
|Comments|💡 `:bulb:`|`docs`|
|Initial commit|🎉 `:tada:`|`init`|
|Configuration|🔧 `:wrench:`|`chore`|
|Deploy|🚀 `:rocket:`||
|Documentation|📚 `:books:`|`docs`|
|In progress|🚧 `:construction:`||
|Interface styling|💄 `:lipstick:`|`feat`|
|Infrastructure|🧱 `:bricks:`|`ci`|
|Ideas list (tasks)|🔜 `:soon:`||
|Move/Rename|🚚 `:truck:`|`chore`|
|New feature|✨ `:sparkles:`|`feat`|
|Package.json in JS|📦 `:package:`|`build`|
|Performance|⚡ `:zap:`|`perf`|
|Refactoring|♻️ `:recycle:`|`refactor`|
|Code Cleanup|🧹 `:broom:`|`cleanup`|
|Removing a file|🗑️ `:wastebasket:`|`remove`|
|Removing a dependency|➖ `:heavy_minus_sign:`|`build`|
|Responsiveness|📱 `:iphone:`||
|Reverting changes|💥 `:boom:`|`fix`|
|Security|🔒️ `:lock:`||
|SEO|🔍️ `:mag:`||
|Version tag|🔖 `:bookmark:`||
|Approval test|✔️ `:heavy_check_mark:`|`test`|
|Tests|🧪 `:test_tube:`|`test`|
|Text|📝 `:pencil:`||
|Typing|🏷️ `:label:`||
|Error handling|🥅 `:goal_net:`||
|Data|🗃️ `:card_file_box:`|`raw`|

---

## 💻 Examples

|Git Command|Result on GitHub|
|---|---|
|`git commit -m ":tada: Initial commit"`|🎉 Initial commit|
|`git commit -m ":books: docs: README update"`|📚 docs: README update|
|`git commit -m ":bug: fix: Infinite loop on line 50"`|🐛 fix: Infinite loop on line 50|
|`git commit -m ":sparkles: feat: Login page"`|✨ feat: Login page|
|`git commit -m ":bricks: ci: Dockerfile modification"`|🧱 ci: Dockerfile modification|
|`git commit -m ":recycle: refactor: Switching to arrow functions"`|♻️ refactor: Switching to arrow functions|
|`git commit -m ":zap: perf: Improved response time"`|⚡ perf: Improved response time|
|`git commit -m ":boom: fix: Reverting inefficient changes"`|💥 fix: Reverting inefficient changes|
|`git commit -m ":lipstick: feat: CSS styling of the form"`|💄 feat: CSS styling of the form|
|`git commit -m ":test_tube: test: Creating new test"`|🧪 test: Creating new test|
|`git commit -m ":bulb: docs: Comments about the LoremIpsum() function"`|💡 docs: Comments about the LoremIpsum() function|
|`git commit -m ":card_file_box: raw: RAW Data for year yyyy"`|🗃️ raw: RAW Data for year yyyy|
|`git commit -m ":broom: cleanup: Removing commented code blocks and unused variables in the form validation function"`|🧹 cleanup: Removing commented code blocks and unused variables in the form validation function|
|`git commit -m ":wastebasket: remove: Removing unused files from the project to maintain organization and continuous updates"`|🗑️ remove: Removing unused files from the project to maintain organization and continuous updates|

---

## Main Git Commands 📜

- `git clone repository-url-on-github` – Clones an existing remote repository from GitHub to your local environment.
- `git init` – Initializes a new Git repository in the current directory.
- `git add .` – Adds all files and changes in the current directory to the staging area (preparing them for commit).
- `git commit -m "commit message"` – Records the changes added to the staging area with a descriptive message about what was modified.
- `git branch -M main` – Renames the current branch (master) to main. The `-M` flag is used to force the rename, moving the branch if necessary.
- `git remote add origin https://github.com/user/repository-name.git` – Adds a remote repository called origin to the local repository. Use `https://github.com/user` to configure with HTTPS or `git@github.com:user` to configure with SSH.
- `git push -u origin main` – Sends commits from the local main branch to the remote origin repository and sets main as the default branch for future push and pull. The `-u` (or `--set-upstream`) configures the upstream branch to simplify future `git push` and `git pull` commands.
- `git remote add origin git@github.com:user/project.git && git branch -M main && git push -u origin main` – When you already have a local repository and want to connect it to a remote GitHub repository, this adds the remote, renames the main branch to main, and sends the initial commits.
- `git fetch` – Fetches all updates from the remote repository without integrating them into the current branch. This updates the remote references.
- `git pull origin main` – Updates the local main branch with changes from the remote origin repository. Combines `git fetch` and `git merge`.
- `git push --force-with-lease` – A safer way to force-push local changes to the remote repository. It checks whether no changes have been made by other collaborators since your last local update, avoiding accidentally overwriting others' work.
- `git revert commit_id_to_be_reverted` – Creates a new commit that undoes the changes made by the specified commit, preserving history. Useful for safely undoing changes without rewriting history.
- `git reset --hard id_of_commit_before_the_one_to_be_deleted` – Resets the repository to the state of the specified commit, deleting all changes made after that commit. Ideal for local use. To sync remotely, use `git push --force-with-lease` afterward.
- `git commit --amend -m "rewritten_message"` – Changes the message of the last commit. After using this command, sync remotely with `git push --force-with-lease`.
- `git cherry-pick COMMIT_HASH` – Used to grab a specific commit. Example: imagine you have two branches (main) and (develop) and the second has 3 commits but you only want to grab the first one — with cherry-pick you can.
- `git switch <branch>` – Switches to a different branch in the local repository. Use `git switch -c <branch>` to create and switch to a new branch.