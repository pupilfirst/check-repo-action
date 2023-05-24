# Pupilfirst Check Repo Action

When a student submission contains a URL to a GitHub repository, the `check_repo` action can be used to clone it and check for the presence of required files or folders.

To fetch the repo URL, the action makes the assumption that the first question in the target checklist is asking for the GitHub repo URL. The following steps are performed:

1. The action will validate the repo URL (that it is, indeed, a GitHub repo URL), and then clones it. By default, it clones to the root path, but this can be customized using the `repoPath` input.
2. It then checks for the presence of files and folders specified using the `globs` input array.

If any failure occurs during these checks, the student's submission will be rejected with appropriate feedback. To avoid sending any reports to the LMS, set the `testMode` input to `true`.

## How to release

When releasing a new version, you should always push two tags - the full version tag - `v1.2.3` for example, and the corresponding major version tag - `v1`, for `v1.2.3`. You will need to delete the existing major version tag, and push a replacement tag for each release.

```bash
# Delete the old local tag, and create it anew.
git tag -d v1
git tag v1
git tag v1.2.3

# Delete the old tag on origin before pushing updated ones.
git push origin :refs/tags/v1
git push origin v1
git push origin v1.2.3
```
