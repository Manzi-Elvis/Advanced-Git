# Git Basics

# Learn the fundamentals

If you have never used Git before, learn the basics first. You can use one of these resources:

- https://www.w3schools.com/git/default.asp
- https://www.youtube.com/watch?v=8JJ101D3knE
- https://www.youtube.com/watch?v=tRZGeaHPoaw

Or any other resources you find and like.

Git and Github keep changing things as they are continuously developed. If something doesn’t look exactly the same way in the tutorial as it does on your computer, 

- check the comments under the video to spot whether anyone has had the same problem and how they solved it.
- If that doesn’t help google for a solution.
- If that doesn’t yield any results, ask for help in the git discord channel.

# Do exercises to get to a good level

Below, we have put together a collection of git exercises, which are made to help you get a better understanding of git. You need to work through all of these exercises, to make sure you are at a good level.

> For all the exercises below there is a solution playlist on youtube, that Yannick (CTO of Octan Group and Tech Lead at The Gym) recorded for you (https://www.youtube.com/playlist?list=PLnLXJSAQnxY7Kv9BLPh2T2YtcQUkZOkUe). Don’t watch the tutorial videos straight away. First try solving the exercise yourself.
> 

Before starting these exercises, please create one Github repository that you will use to paste your terminal history into after each exercise. Call it “Gym Git Exercise Solutions” or similar. Make sure it has a readme file.

The process for solving the exercises is as follows:

- First try to solve the exercise on your own (without peaking into the solution!). You are allowed google git commands, if you don’t remember them or if you need to read up on them.
- Next watch the solution video for the exercise you just completed.
- If you feel you may have done some things wrong, do the exercise again. But while you are doing it again, don’t peak at the video. Do it from memory.
- Now you can watch the video again (possibly at double speed, or skipping to the bits that you have doubts about) to double check if you did everything right this time.
- If you feel you still had mistakes, do the exercise again. Again, do it from memory, don’t peak at the video. And then afterwards check the video again etc. etc.
- Once you are confident that you have got the right solution, copy the terminal commands you used in your last try and past them in the readme file of the “Gym Git Exercise Solutions” repository you have created. All Solutions to all exercises should be pasted into the readme file of this repository. Even when an exercise requires you to create a Github repository for the purposes of solving the exercise, nevertheless always use the “Gym Git Exercise Solutions” readme file to paste your terminal history into. [Watch this video to learn how to do this](https://www.youtube.com/watch?v=HqttjHDnuFQ&list=PLnLXJSAQnxY7Kv9BLPh2T2YtcQUkZOkUe&index=1).
- Insert the link to the “Gym Git Exercise Solutions” Github repository as well as the link to the Github repository you created for this exercise (if there was such a repository in this exercise) into the appropriate Trello card on the trainee task Trello board your coach has created for you. Please note that there are no peer code reviews for the git exercises. You will only be reviewed by your coaches.

# **Bundle 1**

Exercise 1

- Create a project folder & initialize git
- Make changes to the project (add files and contents)
- Rename your main branch from `master` to `main` (If your branch name is already `main` then rename it to `master` and then back to `main`)
- Stage your changes and commit them
- Create a Github repo and connect it with your project
- Push your changes to GitHub
- Create a new branch `dev`
- From `dev` create another branch `test`
- Go back to the `dev` branch and delete the `test` branch

Exercise 2

- Create a new `home.html` file, add some html changes and save them
- Stash save your current changes
- Repeat the same process for a new `about.html` page and stash save your changes
- Repeat the same process for a new `team.html` page and stash save your changes
- Using stash pop restore the changes of the `about.html` page
- With the help of an index use stash pop bring back the `home.html` page changes
- Commit the current changes and push them
- Using stash pop restore the changes of the `team.html` page index
- Reset the current changes using git reset and go back to the changes without the `team.html` page

# Bundle 2

Exercises 1

- Create a new branch named `ft/bundle-2`
- Add new changes to your project. create a new page named `services.html` and add some changes
- Commit your changes and create a Pull Request against the `main` branch in your github repository
- Request a review and make sure your Pull request gets merged (Look for someone to merge your PR)

Exercise 2

- Checkout your `main` branch and pull the latest changes
- Create a new branch named `ft/service-redesign`
- Add new changes to the `service.html` page
- commit and push them
- create a new PR for your changes
- go back to your `main` branch and add again new changes to your `service.html` page, you can add different changes but make sure to affect the same part(line of code) as you did in the other PR
- Commit and push those changes
- Now go back to the Github PR you had created for the `ft/service-redesign`branch, you will then see that you have conflicts with the `main` branch
- In your project checkout the `ft/service-redesign`branch
- Compare the `ft/service-redesign`with the `main` branch using git diff and observe the changes
- Using git merge, merge the `main` branch with `ft/service-redesign` branch and commit and push you changes again

# Bundle 3

Exercise 1:

- Create a new branch named `ft/team-page`
- Create a new html page named `team.html` and add some changes
- commit and push those changes
- Create a new PR for the changes
- Go back to `main` branch (checkout the `main` branch)
- Create new branch named `ft/contact-page`
- Go back to the `ft/team-page`
- With the help of git log look for the last commit and copy its hash
- Checkout again `ft/contact-page` using git cherry-pick get the changes from the last commit on the `ft/team-page` branch.
- Add new changes for the contact page and commit, push them
- Create a new PR for the contact page
- From the `ft/contact-page` branch create a new branch called `ft/faq-page`
- Create a new `faq.html` page and add some changes there
- Commit and push those changes
- Using git revert, revert the changes of the last commit of the `ft/team-page` branch. (use the commit hash you copied earlier)
- Push the changes and create a new PR

Exercise 2:

- Create new branch from the `ft/faq-page` branch named `ft/home-page-redesign`
- Go back to the `main` branch and make some changes there
- Commit and push them
- go back to the `ft/home-page-redesign` branch
- Using git rebase, rebase your branch to `main`
- Add changes to the home page and commit push them
- Create a PR for the changes.

# Bundle 4

Exercise 1

- Checkout the `main` branch
- Create a new repository on Github
- Using git remote add the repo to your project as second remote named `git-copy`
- Make a new changes on the home page
- Commit the changes
- Push the changes to the both remotes. the `origin` and `git-copy`

Exercise 2

- Checkout a new branch named `ft/footer`
- Add some changes to the branch and commit them
- Add more changes again to the branch and create a second commit
- Push and create a new PR for the branch
- Checkout the `main` branch again
- From there create a new branch named `ft/squashing`
- Using git merge squash, squash the changes on the `ft/footer` branch
- Commit the changes with a different commit message such as `footer changes squashing`
- Push the changes and create a PR

# Bundle 5

Exercise 1:

- On your Github repo enable Github pages
- Check if the link is publicly visible to anyone

Exercise 2:

- Fork this project https://github.com/TheGymRwanda/git-cafe-exercise
- Clone your fork on your machine
- Edit the `index.html` file
- Change the text `Welcome to our place` to `Welcome to our restaurant`
- Commit and push the changes
- Raise a PR to the original Repo

# Bundle 6

> In this exercise, you will be working on the copy of the `git-cafe-exercise` that you have forked on your account in the previous exercise.

Keep in mind that each exercise must be done on a different branch
> 

Exercise1:

- On the `git-cafe-exercise` repo create a new feature branch
- Add new changes related to a new page named `Menu`
- Afterward, raise a new PR
- Request review

Exercise2:

- Create a new bug fix branch
- From there change the title of the `index-4.html` file to “**Contact**”
- Raise a new PR
- Request review

Exercise 3:

- On the `git-cafe-exercise` repo, there is a small hot-fix on the contact page
- Change the telephone on the `index-4.html` page from `+1 800 603 6035` to `+1 800 659 6035`

Exercise 4:

- Review two PRs from your peers and request some changes on those PRs —> your peers need to give you access to their repository for you to review them.
- Once, they have adjusted the requested changes, approve and merge that PR.