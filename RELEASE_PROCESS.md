# Testground Release Process Checklist

## `testground/go-sdk` repo
Optionally release the Testground Go SDK
- [ ] Create a new release from Github, which automatically creates a new tag


## `testground/testground` repo
- [ ] If `testground/go-sdk` has been released, update it in `testground/testground` module
- [ ] Optionally upgrade the example test plans to the new `go-sdk`
- [ ] Create a new release from Github, which automatically creates a new tag
- [ ] `make install`, `docker tag` images with new version and push to Docker Hub


## `testground/infra` repo
- [ ] Update image version for next stable release (for example `v0.5.2`) and commit to `testground/infra` `master` branch.
- [ ] Tag the `testground/infra` `master` branch with version (for example `v0.5.2`)
- [ ] Update image version back to `edge` and commit to `master`


## `docs.testground.ai`
- [ ] Rename `master` variant to `new stable release vX.Y.Z` at https://app.gitbook.com/@protocol-labs/s/testground/
- [ ] Copy `new stable release vX.Y.Z` to a new `master` variant
- [ ] Make the `new stable release vX.Y.Z` default variant
- [ ] Optionally remove variants for previous releases to vX.Y.Z

---

## Git branching guidelines during release

The Testground team in general works on a two-week sprint schedule. We strive to produce a release of Testground every two weeks.

At the end of every sprint, before the beginning of a new sprint, we do a `temperature check` and decide if we as a team are happy to create a release out of the work done during the sprint.

If yes, we assign a `release manager` for the upcoming release, who is responsible for processing the checklist above and for creating a new release.

During that period the rest of the team continues to work on outstanding tasks, or they move on to the next sprint.

If necessary developers merge PRs into the `next` branch, which is synchronized and merged back to `master` after the `release manager` completes the release from the previous sprint. Alternatively at developers' discretion, folks are welcome to keep PRs approved and ready to be merged, use `stacked PRs` and any other methods, and avoid using the `next` branch, while a release is underway.
