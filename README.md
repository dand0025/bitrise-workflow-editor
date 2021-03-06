# Bitrise Workflow Editor

## How to install & use the Workflow Editor on your Mac/Linux

1. Install the latest [Bitrise CLI](https://www.bitrise.io/cli) - it's a single binary command line tool
1. Run `bitrise setup` just to be sure everything's prepared
1. `cd` into a directory where you have your `bitrise.yml`, and run: `bitrise :workflow-editor`

That's all. The Workflow Editor is now part of the Bitrise CLI core plugins, so you don't have to install it manually.

To upgrade to the latest version of the Workflow Editor run:

```
bitrise plugin update workflow-editor
```

*Join the Workflow Editor's discussion at: [https://discuss.bitrise.io/t/workflow-editor-v2-offline-workflow-editor/39](https://discuss.bitrise.io/t/workflow-editor-v2-offline-workflow-editor/39)*


## Development

### Build a stand-alone binary, with embedded resources

```
bitrise run go-install
```

## New version release

- Ensure clean git
- Bump `RELEASE_VERSION` in `bitrise.yml`
- Commit changes
- Call `bitrise run create-release`
- Update changelog in `CHANGELOG.md`
- Commit changes, then squash both to a commit with message `vX.X.X`, push it
- On GitHub, create new release with title and tag `X.X.X`, description from changelog, starting with *Release Notes*, up to but not including *Release Commits*
- Wait for the `create-release` workflow to finish successfully on Bitrise
- Download the generated artifacts from Bitrise
- In terminal, run `chmod +x <path to generated binary> && <path to generated binary> version --full`
- After finish and double-checking build number and commit hash on Bitrise, run <path to generated binary> to check if binary is working
- On GitHub, attach the binaries, then select *Publish release*
- On discuss.bitrise.io, in *Changelog* category, create a topic called **Offline Workflow Editor / Workflow Editor v2 vX.X.X released**. Description should include the changelog (with URLs to related GitHub issues) and a link to the installation instructions.
- On GitHub, close the related GitHub issues, and milestones if the issues were assigned to any.
