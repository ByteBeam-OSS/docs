# Moving Changes to a Different Branch

If you've made changes to a branch and realized that you should have made those changes on a different branch, follow these steps to move your changes without losing them:

## 1. Stash Your Changes

First, stash your changes so that you can apply them to another branch.

```
git stash
```

## 2. Create or Checkout the Desired Branch

If your desired branch doesn't exist yet, create and checkout the branch:

```
git checkout -b [branch_name]
```

If the branch already exists, simply checkout:

```
git checkout [branch_name]
```

## 3. Apply Your Stashed Changes

Now, apply the changes you stashed:

```
git stash apply
```

## 4. Commit Your Changes

Once you've applied your changes to the correct branch, commit them:

```
git add .
git commit -m "Your commit message"
```

## 5. Optional - Clean Up

If everything looks good and you've committed your changes, drop the stash:

```
git stash drop
```

**Note**: Always double-check which branch you're on before making changes.

---

To push these changes to a remote repository:

```
git push origin [branch_name]
```

