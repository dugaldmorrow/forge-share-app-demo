# Forge share app demo

## Problem

The Forge manifest.yml contains the ID of the app. Sometimes, however, different developers will want to share a codebase but may want to independently own the apps built from the code so it doesn't make sense for a single app ID to be checked into the code respository since each time developers checkout or pull code, they will be getting someone elses app ID. Running a Forge app development training course is an example where this problem occurs.

## Goal

This project demonstrates how a Forge app codebase can be shared between independent developers, allowing each developer to manage separate apps generated from the code.

# Setup

## Project setup

This project is already setup, but these are the steps to setup a different Forge project.

1. Add "envsub" as a dev dependency with `npm install --save-dev envsub`.
2. Add a script to "package.json";- `"reset-manifest": "node ./node_modules/envsub/bin/envsub.js manifest.yml"`
3. Rename manifest.yml to manifest.template.yml.
4. Edit manifest.yml to substitue the app ID with a suitable environment variable name such as ${FOO_APP_ID}. Your manifest.yml will look something like the following:

```
app:
  id: ari:cloud:ecosystem::app/${FOO_APP_ID}
```

## Developer setup

1. Check out the project.
4. Run `forge register`.
5. Update your environment variable with the real app ID `export SHARE_APP_DEMO_APP_ID=xxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx`.
6. Run `npm run reset-manifest` to re-generate "manifest.yml" with your app ID. 


# Checking out and pulling code

After each time you check out or pull code, run `npm run reset-manifest` to fix your "manifest.yml".

# Pushing manifest.yml changes.

Always remember to only check in `manifest.yml` with the template parameter for the envirnment variable instead of the app ID.

To avoid this, you could use the git filter feature as described [here](https://community.developer.atlassian.com/t/how-do-you-let-multiple-developers-work-on-the-same-forge-app/44876/9).
