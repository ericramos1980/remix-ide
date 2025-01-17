This document includes:
 - how to update remix.ethereum.org.
 - how to update remix-alpha.ethereum.org.
 - how to release remix IDE.

# remix IDE release

 - git fetch origin master
 - git checkout origin/master
 - git checkout -b bumpVersion
 - update package.json version
 - remove package-lock/json version and generate a new one with `npm install`
 - merge PR
 - git fetch origin master
 - git checkout origin/master
 - git tag v(version-number)
 - git push --tags
 - github-changes -o ethereum -r remix-ide -a --only-pulls --use-commit-body --only-merges --between-tags previous_version...next_version
 - publish a release in github using the changelog
 - rm -rf node_modules
 - npm install
 - remove all soljson.js files in root folder
 - npm run build
 - npm publish
 - after remix_live is updated, drop the zip (from the root folder of remix-live repo) to the release.

# remix.ethereum.org update

This is not strictly speaking a release. Updating the remix site is done through the Travis build:

 - switch to the remix_live
 - git reset --hard -master-commit-hash-
 - git push -f origin remix_live

 CircleCI will build automaticaly and remix.ethereum.org will be updated

# remix-alpha.ethereum.org update

remix-alpha.ethereum.org is automaticaly updated every time commits are pushed to master
 
