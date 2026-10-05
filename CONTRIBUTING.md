# Contributing

Thanks for wanting to improve Quicksend.

## Reporting bugs

Open an [issue](https://github.com/Dschonas04/quicksend/issues/new/choose)
with your operating system, the Quicksend version (shown at the top of the
page) and what happened. Security problems please report privately, see
[SECURITY.md](SECURITY.md).

## Building and testing

Go 1.26 or newer, no C compiler:

```bash
go test -race ./...
go vet ./...
gofmt -l .            # must print nothing
go build ./cmd/quicksend
```

## Pull requests

1. Fork, create a branch, make the change.
2. Tests, `go vet` and `gofmt` must pass; new behaviour gets a test.
3. Add a line under "Unreleased" in [CHANGELOG.md](CHANGELOG.md).
4. Open a pull request and say what changes and why.

Quicksend has no runtime dependencies beyond the Go standard library and the
mDNS package. Please keep it that way unless there is a strong reason.

## License

By contributing you agree that your work is released under the
[MIT License](LICENSE).
