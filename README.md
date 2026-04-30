# aforo-nextgen-homebrew-tap

Public Homebrew tap for [Aforo NextGen](https://github.com/aforoai)
command-line tools.

## Available formulae

| Formula  | Description                                                                                          | Source                                                                                       |
| -------- | ---------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| `loadgen` | Load generator for the Aforo NextGen multi-tenant SaaS billing & metering platform's ingestion path. | [aforoai/aforo-nextgen-loadgen](https://github.com/aforoai/aforo-nextgen-loadgen) (private). |

## Install

```bash
brew tap aforoai/tap https://github.com/aforoai/aforo-nextgen-homebrew-tap
brew install aforoai/tap/loadgen
```

`brew upgrade aforoai/tap/loadgen` always pulls the latest tagged
release. Each tagged release of the upstream tool regenerates the
formula in `Formula/loadgen.rb` automatically — see "How the tap is
maintained" below.

## How the tap is maintained

This tap is **fully managed by GoReleaser**. Maintainers do not edit
`Formula/*.rb` by hand.

The pipeline:

1. A maintainer pushes a SemVer tag (`v*.*.*`) to one of the upstream
   repositories listed in the table above.
2. The upstream repo's `release.yml` workflow runs GoReleaser.
3. GoReleaser cross-compiles the per-platform binaries, archives them,
   computes SHA-256 checksums, publishes a GitHub Release on the
   upstream repo, then pushes a regenerated `Formula/<name>.rb` to this
   tap. The cross-repo push uses a PAT secret named
   `HOMEBREW_TAP_GITHUB_TOKEN` configured on the upstream repo.
4. End users running `brew upgrade aforoai/tap/<name>` see the new
   version on their next `brew update`.

The first commit to a freshly-created tap is just this README and an
empty `Formula/` directory. The first formula appears after the first
upstream release ships.

## Repository policy

- This repo is **public**. Homebrew formulae need public read access.
- Source repositories may be private — the formula references the
  upstream's tagged release archives via direct download URL with the
  release token; brew end-users do not need any auth.
- Pull requests editing `Formula/*.rb` directly are closed without
  merge — the formulae are generated artifacts. Open the PR against
  the relevant upstream repo instead.

## Issues

If a `brew install aforoai/tap/<name>` step fails, file the issue
against the **upstream tool's repo**, not this tap. Common failure
modes — broken binary, missing platform, formula test fails — all
trace back to the upstream's release pipeline, not the tap itself.

## License

Each formula in this tap is licensed under the same terms as its
upstream source. The tap repo's own metadata (this README, the
`.gitignore`) is Apache-2.0.
