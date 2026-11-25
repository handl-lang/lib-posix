# lib-posix

The POSIX.1-2017 **contract** — the port side of the port/impl split.
`src/index.hnl` declares signatures + docs; backends (`posix-c` over
libc via `ffi.call`, `posix-stub` for tests) export arrows of these
types; `lib-fs` is the reference fs impl.

## Layout

| path | role |
| --- | --- |
| `src/index.hnl` | the contract — signatures + docs |
| `pkg.hnl` | manifest — `modules: ["posix"]` |
| `scripts/hnl-gate.sh`, `ci.sh` | the gate / bupha entry |

## Contract

- Surface: fd ops (`open`/`read`/`write`/`pread`/`pwrite`/`lseek`/
  `fsync`/`fdatasync`), path-addressed fs (`unlink`/`rmdir`/`rename`/
  `mkdir`/`access`/`stat`/`lstat`/`fstat`/`opendir`/`readdir`/
  `closedir`/`getcwd`/`chdir`), process env (`getenv`/`env_has`),
  pure path conveniences (`join`/`resolve`/`basename`/`dirname`/
  `extname`), clock reads (`now_ms`/`instant_ns`/`elapsed_ns`/`epoch`).
- Pure `.hnl`; no Rust crate.

## Verification

```bash
HNL=../host-cli/target/debug/hnl scripts/hnl-gate.sh
```

## License

MIT.

<!-- myco:agent-awareness -->

## Agent awareness

- Session start / any work discussion: run `myco status --prompt`
  before proposing next steps — know the board first.
- User describes new work → offer to capture it (`myco todo add`,
  `issue new`, `proposal new`). Don't wait to be asked.
- Picking up a task: `myco resume <ID>` is the briefing.
- Wrapping up: `myco handoff <ID>` anything resumable; keep statuses
  honest (claimed → in-progress → blocked/done).

<!-- /myco:agent-awareness -->
