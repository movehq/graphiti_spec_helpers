# GraphitiSpecHelpers

![Build Status](https://travis-ci.org/graphiti-api/graphiti_spec_helpers.svg?branch=master)

Spec helpers for [Graphiti](https://github.com/graphiti-api/graphiti)
APIs.

## Releasing

This gem is forked by @movehq for the purpose of being able to merge any PRs that we make (and have made) to the upstream repo.
To keep our release tags separate from the upstream tags, using `-hsc` suffix as a "prerelease" semver segment.
After all desired changes have been merged to master:

1. Derive the next version number.
   It should follow semver, so bump major/minor/patch segments as appropriate.
   Then apply the `-hsc.N` prerelease suffix.
   > For example, the existing version was `1.1.0`.
   Our changes were not breaking changes and added some capabilities, so we bumped the version to `1.2.0-hsc.1`.
   Now that we have a "pre-release" of a minor bump, only the `.1` needs to be incremented for any bug fixes or feature additions.
   Only breaking changes at this point would require the version bumped to, say, `2.0.0-hsc.1`.
2. Set this version number in [version.rb](lib/graphiti_spec_helpers/version.rb)
3. Merge this version bump to master (preferably by rebase or squash merge).
4. [Create a Release](https://github.com/movehq/graphiti_spec_helpers/releases/new)
   1. select "Choose a tag" and type in the same version as in version.rb **with a `v` prefix**.
   2. click "Generate Release Notes"
   3. check "set as latest release"
   4. click Publish
5. This Release process will create the corresponding git tag which triggers the release workflow.
6. The GitHub Actions [release workflow](.github/workflows/release.yml) will build and publish the gem to [GitHub Packages](https://github.com/orgs/movehq/packages?repo_name=graphiti_spec_helpers).
    > **Note**:
    The gem name will use `.pre` in place of the hyphen in the semver version. This is expected and is just a quirk of rubygems that pre-dates the semver standard. (because rubygems uses hyphens to separate the _platform_ for gems that require native compilation)
