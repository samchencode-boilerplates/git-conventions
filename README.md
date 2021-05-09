# git-conventions

Notes on best practices for using `git` and GitHub.

## Topics
 - [Branching Models](#branching-models)
 - [Versioning Releases with SemVer 2.0.0](#versioning-releases)
 - Pull Request Etiquette
 - Commit Messages
 - Deployment

## Branching Models

### 1. Feature Driven Development

Break up branches by features. Merge into production branch when ready.

Large teams can work in parallel, and features can be tested in isolation. Easily decide which features are included in each release. However, it's hard to keep track of thousands of branches. Branches may conflict so it requires coordination.

Good for large, numerous, dispersed teams on a large codebase.

Bad for small, young projects that need to iterate quickly.

#### Examples

- [Git Flow](https://nvie.com/posts/a-successful-git-branching-model/)

  `main` and `develop` branches are persistent. Feature branches branch off of `develop` and merge into `develop`. Release branches branch off of `develop` and merge into `main` and are then tagged with version number. Hotfix branches branch off of `main` and merge into `main` and `develop`.

- GitLab Flow

  Feature branches come directly off `main` branch. When feature is done, open pull request to merge into `main`. Move code into staging (pre-production) environment for testing. Then move code into production environment. 

### 2. Trunk-Based Development

Generally commiting to master, rarely branching. All branches extend from main branch (the trunk).

Nearly no divergence of branches and little cost of maintaining other branches. Minimizes merge conflicts and allows quicker development, in theory. However, the codebase is very unstable and intentions of commits may be mixed between different features and varying levels of code maturity.

Good for small teams of experienced developers who need to move fast.

#### Examples

- GitHub Flow

  `main` branch is the only peristent branch. Feature branches branch off of `main`. Open pull request to merge feature branch into `main`.

### 3. Team-Based Development

Break up branches by team.

### 4. Stage-Based Development

Break up branches by stage of code maturity.

## Versioning Releases



## References
 - [General Best Practices](https://www.datree.io/resources/github-best-practices)
 - [Version Control](https://ourcodingclub.github.io/tutorials/git/)
 - [SemVer GeeksForGeeks](https://www.geeksforgeeks.org/introduction-semantic-versioning/)
 - Pull Requests: [1](https://gist.github.com/mikepea/863f63d6e37281e329f8), [2](https://github.community/t/best-practices-for-pull-requests/10195)
 - Branching Models: [1](https://www.perforce.com/blog/vcs/best-branching-strategies-high-velocity-development), [2](https://www.perforce.com/blog/vcs/git-branching-model-multiple-releases), [3](https://www.perforce.com/blog/vcs/trunk-based-development-or-feature-driven-development#what-feature)
   - [GitFlow](https://nvie.com/posts/a-successful-git-branching-model/)
 - [Commit Message Conventions](https://www.conventionalcommits.org/en/v1.0.0/)
 - [Managing Secrets outside of Version Control](https://www.datree.io/resources/secrets-management-aws)
 - [TWelve Factor App](https://12factor.net/)