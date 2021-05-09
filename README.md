# git-conventions

Notes on best practices for using `git` and GitHub.

## Topics
 - [Branching Models](#branching-models)
 - [Versioning Releases with SemVer 2.0.0](#semantic-versioning)
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

## Semantic Versioning

### Version number

```
x.y.z
```

 - Increment `x` (aka `MAJOR`) for breaking changes, for `x` >= 1 
 - Increment `y` (aka `MINOR`) for new backward-compatible functionality
 - Increment `z` (aka `PATCH`) for bug fixes

### Major Version Zero

```
0.y.z
```

Major version zero is rapid development phase, very unstable API.First release is `0.1.0`.
First stable release is `1.0.0`. SemVer does not apply until `1.0.0`.

### Version Metadata

For example, `x.y.z-alpha` or `x.y.z-alpha.1`. 

From semver.org:
> 1.0.0-alpha < 1.0.0-alpha.1 < 1.0.0-alpha.beta < 1.0.0-beta < 1.0.0-beta.2 < 1.0.0-beta.11 < 1.0.0-rc.1 < 1.0.0.

 - `alpha.x` - Project is documented, but unstable. Serious known issues remain. No thorough testing, so there may be unknown bugs. Not suitable for production; for contributors.
 - `beta.x` - Critical data loss and security bugs resolved. API is frozen. Not suitable for production; for contributors and API consumers.
 - `rc-x` - Release candidate. All critical bugs are fixed. Developer believes it's ready for production use. Should remain `rc` for at least 1 month for bug reporting before official `.0` release. If critical bug is found, fix in new release.

### Tagging in `git`

#### Annotated Tag

```
$ git tag -a v1.0.0 -m "Release version 1.0.0"
```
Contains extra metadata like author name, release notes, tag-message. Important for public release. Sign commit to verify its source using `-s` flag if you have GPG private key set up.

Note that "v1.0.0" is a tag name and the SemVer is "1.0.0".

#### Lightweight Tag

```
$ git tag v1.0.0
```
Contains only hash of referenced commit.

## References
 - [General Best Practices](https://www.datree.io/resources/github-best-practices)

 - [Version Control](https://ourcodingclub.github.io/tutorials/git/)

 - [SemVer 2.0.0](https://semver.org/)
   - [SemVer GeeksForGeeks](https://www.geeksforgeeks.org/introduction-semantic-versioning/)
   - [Range Spec Cheatsheet](https://devhints.io/semver)
   - [Tagging in Git](https://dev.to/neshaz/a-tutorial-for-tagging-releases-in-git-147e)
   - [Pre-releasing Conventions](https://drupal.stackexchange.com/questions/99612/what-does-rc-stand-for-when-to-use-alpha-beta-and-dev-instead/99614)

 - Release Notes:
   - [Keep a Changelog](https://keepachangelog.com/en/1.0.0/)
   - [Opinions on Release Notes](https://www.mehdi-khalili.com/better-git-release-notes)

 - Pull Requests: [1](https://gist.github.com/mikepea/863f63d6e37281e329f8), [2](https://github.community/t/best-practices-for-pull-requests/10195)

 - Branching Models: [1](https://www.perforce.com/blog/vcs/best-branching-strategies-high-velocity-development), [2](https://www.perforce.com/blog/vcs/git-branching-model-multiple-releases), [3](https://www.perforce.com/blog/vcs/trunk-based-development-or-feature-driven-development#what-feature)
   - [GitFlow](https://nvie.com/posts/a-successful-git-branching-model/)

 - [Commit Message Conventions](https://www.conventionalcommits.org/en/v1.0.0/)

 - [Managing Secrets outside of Version Control](https://www.datree.io/resources/secrets-management-aws)
 
 - [Twelve Factor App](https://12factor.net/)