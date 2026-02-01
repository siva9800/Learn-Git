
#
git
Git Workflow is a recipe or recommendation for how to use Git to accomplish work consistently and productively.

The topmost workflows present nowadays are:

Git flow
GitHub flow
GitLab flow
Today, we're gonna talk about "Git flow" the most popular and widely used one.

Table of content:
What is Gitflow?
Gitflow diagram branches.
How does Gitflow works?
Conclusion
References
What is Gitflow?
It is a successful git branching model that depends on isolating your work into different types of branches. it was introduced in June 2010 by Vincent Driessen, and it's become the most popular workflow as it achieved the maximum benefit from using git.

Gitflow branching diagram
Gitflow branching diagram image

the image above shows the branching model of a repo created with Git flow workflow; we can notice that the repo consists of 2 kinds of branches :

1. Permanent branches:
Are branches created at the start of any project, they are always existing branches. (like; master and develop branches)

2. Temporary branches:
are branches created from the permanent one and it's used to perform specific development tasks, then we can delete them (like; hotfixes, release, and features branches).

3. How does Gitflow work?
As mentioned before, in git-flow workflow there are 5 different branches:

Main
Develop
Feature
Release
Hotfixes
3.1 Main branch
Please note: the main branch is commonly referred to as “master”; we have made an intentional decision to avoid that outdated term and have chosen to use “main” instead.

After initializing a new repo, the main branch is created as a default branch, it will hold only the production-ready code that can be released. It is considered a red line which means we shouldn't push directly into it.

3.2 Develop branch
As the main branch is a red line, we create another branch called develop branch. It is considered the single source of truth used to hold pre-production code.

inside this branch, we integrate and test new features and most bug fixes before they are merged into the main branch.

now our repo has both main and develops permanent branches; now let's say we need to add a new feature to our code, so we create a feature branch to add it.

3.3 Feature branch
Is a branch created from the develop branch in which, we add our new feature code then pull a request to develop branch and ask to merge? after merging is done successfully we don't need this branch anymore so we delete it.

Don't add more than one feature inside the same branch [remember: one branch for one feature]

Don't make another branch from the feature branch

3.4 Release branch
Assume that we add all necessary features and our project now is ready to release to the public, in that time release branch comes into the picture. this branch is created for testing purposes like deployment in the server.

During this time if we discovered any bugs we solve them directly in the same branch then merge the changes back to develop branch then push finally it to the main as a live code.

3.5 hotfixes
if any bugs appear after publishing we can fix them quickly by creating a hotfixes branch from the main then merge the changes with develop branch and push it back to the main one.

Conclusion
In this pattern, we can notice that both main and develop branches are identical, that is to make sure bugs which fixed in the main branch don't back again.

