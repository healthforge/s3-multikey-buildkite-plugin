# AWS S3 Multikey Buildkite Plugin

An extension of (and shamelessly based on) Buildkite's S3 secrets plugin. When used alongside, it
allows multiple private keys to be loaded into the SSH agent. This allows multiple repositories to
accessed with different keys, which is important for GitHub as it doesn't allow access keys to be
reused.

## Keys

Keys must be listed in a `multikey.conf` file located in the pipeline folder of the s3 secrets bucket (e.g. `s3://secrets-bucket/my-pipeline/multikey.conf`). 

An example `multikey.conf` (2 column csv) file:

```
bitbucket,healthforge/my-repo
github,acme/another-repo
```

Private keys should then be placed in a `multikey` folder also within the pipeline folder. Key filenames
should match the lines in the multikey file with slashes replaced with dashes:

```
bitbucket-healthforge-my-repo
github-acme-another-repo
```

## Pipeline

```yaml
steps:
- label: "Build"
  command:
  - build.sh
  plugins:
    - healthforge/s3-multikey:
```

## License

MIT (see [LICENSE](LICENSE))

