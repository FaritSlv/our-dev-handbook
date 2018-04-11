<img src="./git-flow.png">

# Rules

Master branch must always be ready to deploy.

Review code with "Pull request" function. Work Branch => Master Branch.
If the pull request pass reviewing.
Reviewer may set an "approve" status on the pull request.
But don't merge.

After the code pass test. Merge it.

# Step

```bash
# Pull new code for master branch.
git checkout master
git pull

# Create new branch for developing a feature or fixing a bug.
# Name of the branch should contain keywords of the featuer or bug.
# e.g. create a branch for new feature "teacher show". 
git branch teacher-show
git checkout teacher-show
# Or simplified to:
git checkout -b teacher-show

# Develop and commit.
git add teacherShow.js
# Recommend to check all changes before commit.
git diff
# Or use GUI.
git gui
# Commit changes.
git commit
# Or simplified to:
git commit -m "New data struct for teacher show."
# DO NOT USE "-a". Because there is no reasons.

# Push your development branch to offical repository.
git push origin teacher-show:teacher-show
# DO NOT USE "--force" UNLESS YOU EXACTLY KNOW WHAT YOU ARE DOING.

# Then you can create a pull request for reviewing.

# Get ready for test.
# Do this on your local machine. Because it is good for solving conflicts.
git checkout test
git pull
git merge teacher-show
# Solve all conflicts if exists.
# Push test branch.
git push

# Deploy test branch on test server.
git checkout test
git pull
# Build, restart service or any other works.

# Testing successed. Received signal for online.
# Tagging only before doing online.
npm version major | minor | patch
# Or manual operation. Edit version in package.json(and package-lock.json if exists). Then use command like "git tag v1.2.3"
# Push code and tags.
git push && git push --tags
```
