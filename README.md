# 8Chess Test

[![CI server](https://github.com/EightChess-Team/8chesstest/actions/workflows/server.yaml/badge.svg)](https://github.com/EightChess-Team/8chesstest/actions/workflows/server.yaml) [![CI worker posix](https://github.com/EightChess-Team/8chesstest/actions/workflows/worker_posix.yaml/badge.svg)](https://github.com/EightChess-Team/8chesstest/actions/workflows/worker_posix.yaml) [![CI worker msys2](https://github.com/EightChess-Team/8chesstest/actions/workflows/worker_msys2.yaml/badge.svg)](https://github.com/EightChess-Team/8chesstest/actions/workflows/worker_msys2.yaml) [![CI lint](https://github.com/EightChess-Team/8chesstest/actions/workflows/lint.yaml/badge.svg)](https://github.com/EightChess-Team/8chesstest/actions/workflows/lint.yaml)

A fork of [Fishtest](https://github.com/official-stockfish/fishtest) for
distributed testing of [8Chess](https://github.com/EightChess-Team/8chess).

## Deployment

- Public server: <https://counting-bags-surgeon-shapes.trycloudflare.com>
- Central host: `162.35.161.218`
- The public URL is a free anonymous Cloudflare quick tunnel. If the tunnel
  restarts, read the current URL from `/var/log/fishtest-tunnel.log` on the
  server.
- Admin account: `8chess` (password provided separately).

The worker defaults to the 8Chess server above. Override it with
`worker/fishtest.cfg` or the environment variables `FISHTEST_WORKER_HOST`,
`FISHTEST_WORKER_PORT`, and `FISHTEST_WORKER_PROTOCOL`.

## Workers

See [`docs/6-worker.md`](docs/6-worker.md) and
[`worker/fishtest.cfg.example`](worker/fishtest.cfg.example).

The worker builds Stockfish sources with `make` and 8Chess sources with
`cargo build --release`. The 8Chess engine uses its embedded network by
default; a custom `EvalFile` is only needed when the test supplies one.

## Upstream

This project is derived from
<https://github.com/official-stockfish/fishtest>. See the upstream
documentation and license for details.
