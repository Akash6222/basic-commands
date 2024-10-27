
---

# Pulling Changes from Upstream Repository

This guide will help you keep your forked repository updated with changes from the original repository (upstream).

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

Switch to the branch you want to update (typically `main` or `dev`):

```bash
git checkout dev
```

Now, merge the upstream changes:

```bash
git merge upstream/dev
```

This command merges the upstream `dev` branch into your local branch. If conflicts arise, resolve them before committing.

### Step 4: Push Changes to Your Fork

After merging, push the changes to your forked repository:

```bash
git push origin dev
```

Your forked repository is now in sync with the original upstream repository.

---

