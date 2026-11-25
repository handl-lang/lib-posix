# lib-posix

The POSIX.1-2017 contract — the port side of the port/impl split. `src/index.hnl`
declares signatures + docs for file-descriptor ops (`open`/`read`/`write`/
`pread`/`pwrite`/`lseek`/`fsync`/`fdatasync`), path-addressed fs
(`unlink`/`rmdir`/`rename`/`mkdir`/`access`/`stat`/`lstat`/`fstat`/
`opendir`/`readdir`/`closedir`/`getcwd`/`chdir`), process env
(`getenv`/`env_has`), pure path conveniences (`join`/`resolve`/`basename`/
`dirname`/`extname`), and clock reads (`now_ms`/`instant_ns`/`elapsed_ns`/
`epoch`). Backends (`posix-c` over libc via `ffi.call`, `posix-stub` for
tests) export arrows of these types; `lib-fs` is the reference fs impl.

## Layout

```text
src/                     the .hnl sources
pkg.hnl                  package manifest
scripts/hnl-gate.sh      the gate
workflows/gate.yaml                    bupha entry (handl-gates)
```

## Gate

```bash
HNL=../host-cli/target/debug/hnl scripts/hnl-gate.sh
```

## License

MIT.
