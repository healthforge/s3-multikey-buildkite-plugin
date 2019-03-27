# AWS S3 Multikey Buildkite Plugin

Shamelessly based on Buildkite's S3 secrets plugin

For builds that need to clone other repositories place file `multikey.conf` in the
root of the pipeline directory in S3

Format, 2 column CSV:
```
bitbucket,healthforge-io/s3-multikey-buildkite-plugin
github,healthforge/buildkite-key-rotator
provider,owner/repository
```


## License

MIT (see [LICENSE](LICENSE))
