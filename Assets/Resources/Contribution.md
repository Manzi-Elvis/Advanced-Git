# Contribution rules and git flow

### Branching

- Before making any new changes make sure to go back to the `dev` branch pull and create a new branch from there
- Make sure to follow the branch naming convention specified in the Branching model
- The dev branch is where developers work on
- Always use the dev branch as the base branch of your pull requests
- The staging branch has a public link that is used to show progress to the client
- The main branch is the production branch.
- Change the base branch using other methods like `git rebase` instead of using the pull request merging for the `dev`, `main`, and `staging`

### Commits

- Follow this guideline Conventional Commits for your commit messages
- Try to create a mid-sized every couple of minutes/hours. But more importantly, try to let commits be logically consistent contributions. That means if you have many changes in lines of code you can split them up into multiple commits but each of those commits should have an independent meaning that is described by the commit message.

### PRs, Code Review

- Once you made the first commit just go ahead and push the changes
- Create a Pull request once you pushed your changes to the repository, you don't have to wait to finish the feature in order to create a pull request you can create it as soon as you have the first commit.
- The name of the PR should follow the same naming convention as the commit messages. (Conventional Commits).
    - Eg: `feat: integrate react markdown`
- If a PR is still being worked on add the GitHub tag `Work in progress`
- Before marking a PR as `Ready for review` make sure that the CI (GitHub actions) and the deployment are passing.
- Request code review by adding the code reviewer as a reviewer to your PR
- After requesting for code review make sure to send a slack message to the project channel with the link to the PR and tag the code reviewer
- PRs should cover a set of related changes covering a single feature, bug fix, or other types of changes
- Delete branches once they are merged

### Resolving Conflicts

- Be super careful, involve the others who are working on similar stuff.
- Make sure you understand what you are accepting or refusing.
- Recent changes are not always the relevant ones, always check that you are not dismissing changes that are actually fixing another bug

### Things to avoid in git

- Avoid using the squash commits feature, it tends to bring conflicts especially when people are using other base branches
- Do not use git force push
- Do not merge your PRs unless your code has been reviewed by a code reviewer and the code reviewer has either approved your changes or accepted all the adjustments you have made upon their review.
- Avoid merging other dependencies PRs into the ones you are working on to avoid having duplicate changes into two PRs in case a change is needed to be used in another.
- Avoid committing the  `node_modules` folder (or including it in the version history).
    - Since it usually contains thousands of files. it increases dramatically the size of your project
    - Due to the high number of files included in the `node_modules` folder, it gets harder to review PRs containing such changes.
    - → You should instead add the `node_modules` folder name to the `.gitignore` file to prevent `git` from tracking it