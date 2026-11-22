# visual-test

Go library and CLI for deterministic browser screenshot capture and visual regression review.

This module was extracted from [mitschwimmer/go-skill](https://github.com/mitschwimmer/go-skill). The ChatGPT skill and project-specific scenarios are maintained separately.

## Packages

- `visualtest`: scenario catalog, capture manifests, PNG comparisons and HTML/JSON reports (standard library).
- `visualtest/rod`: isolated Chromium capture runner using [Rod](https://github.com/go-rod/rod).
- `cmd/visualtest`: catalog validation and capture comparison CLI.

## Install

```sh
go get github.com/archaic-work/visual-test@latest
```

Import `github.com/archaic-work/visual-test/visualtest` or `github.com/archaic-work/visual-test/visualtest/rod`.

## Commands

```sh
go run ./cmd/visualtest validate path/to/scenarios
go run ./cmd/visualtest compare --base /tmp/main-shots --candidate /tmp/pr-shots --out /tmp/report
go test ./...
go vet ./...
```

For reproducible visual comparisons, pin Go, Chromium, fonts, OS image and fixture data. Browser tests require an installed Chromium; configure `VISUALTEST_BROWSER_EXECUTABLE` where needed.

## Migration

Existing consumers of `github.com/mitschwimmer/go-skill` should switch module imports and CLI invocations to `github.com/archaic-work/visual-test`. Pin a reviewed commit or tagged release rather than relying on a moving branch.
