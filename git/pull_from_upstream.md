
---

# Pulling Changes from Upstream Repository

This guide will help you keep your forked repository updated with changes from the original repository (upstream).

### Step 0: Remove Existing Upstream (if needed)

If you previously added an incorrect or outdated upstream remote, remove it first:

```bash
git remote remove upstream
```

> 💡 You only need to do this if you want to reconfigure the upstream URL. If no upstream is set or it’s correct, skip to Step 1.


### Step 1: Add Upstream Repository

If you haven’t set up the upstream repository yet, add it by using:

```bash
git remote add upstream <URL of the original repository>
```

Replace `<URL of the original repository>` with the actual URL of the upstream repository.

### Step 2: Fetch Upstream Changes

To fetch the latest changes from the upstream repository, use:

```bash
git fetch upstream
```

This will download any new commits, branches, or tags from the upstream.

### Step 3: Merge Changes

Switch to the branch you want to update (typically `dev` or `feature` branch):

```bash
git checkout dev
```

Now, merge the specific tag (e.g., v3.3.12) from the upstream repository into your current branch

```bash
git merge v3.3.12
```

This command merges the upstream `v3.3.12` branch into your dev branch. If conflicts arise, resolve them before committing.

### Step 4: Push Changes to Your Fork

After merging, push the changes to your forked repository:

```bash
git push origin dev
```

Your forked repository is now in sync with the original upstream repository.

---

