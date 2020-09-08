# How to release apex

## Install go and goreleaser

```
brew install go
brew install goreleaser/tap/goreleaser
```

For [goreleaser](https://goreleaser.com/quick-start/) to work, you must have
`GITHUB_TOKEN` set in your environment to a [Github
token](https://github.com/settings/tokens/new) with full repo scope.

## Install dependencies and update mod files

```
go get -u ./...
git add go.mod go.sum
git commit -m "Update dependencies"
```

## Update the history, if needed

```
vi History.md
git add History.md
git commit History.md
```

## Push a new tag

```
git push origin master
git tag -a v0.17.0 -m "Release v0.17.0"
git push origin v0.17.0
```

## Build and upload the release

```
export GITHUB_TOKEN=...
make release
```
