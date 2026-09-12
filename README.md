# deka-lsp

`deka-lsp` is the deka language server: an LSP-over-HTTP server for the deka
language (`.ds` sources, public language id `dekascript`). It discovers,
resolves, indexes, renames, and reports diagnostics for `.ds` files only.

Compiler diagnostics delegate to `dsc lsp` — the crate itself never compiles
source; type checking is owned by the dsc compiler, and this crate consumes
its diagnostic output.

The server is consumed by the deka CLI (`deka lsp`), which launches it and
routes editor traffic to it.

## Versioning

`deka-lsp` is published to crates.io and versions independently of the deka
monorepo. It follows semver on its own release cadence — it does **not** move
in lockstep with deka's workspace versions. Compatibility with deka/dsc is
expressed through versioned crate dependencies, not shared version numbers.

## Build and run

```sh
cargo build --release
cargo test --locked
cargo clippy --locked
```

The native server entry point is `deka_lsp::run_stdio` (enabled by the
default `native` feature), launched by the deka CLI with `deka lsp --stdio`.

## License

Apache-2.0. See [LICENSE](LICENSE).
