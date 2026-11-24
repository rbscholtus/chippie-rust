# Chippie (Rust)

[![Build](https://github.com/rbscholtus/chippie-rust/actions/workflows/rust.yml/badge.svg)](https://github.com/rbscholtus/chippie-rust/actions/workflows/rust.yml)

An early-stage CHIP-8 emulator written in Rust, for the desktop and the web
(WebAssembly), with a small catalogue of playable games.

**[▶ Try it in your browser](https://rbscholtus.github.io/chippie-rust/)**

> [!NOTE]
> This project is not being developed further. Finishing it would have meant
> a lot more Rust learning, which wasn't my goal, and the Rust graphics
> libraries at the time weren't easy to work with. I rebuilt the idea in Go:
> see **[Chippie](https://github.com/rbscholtus/chippie)**, which plays over
> 300 CHIP-8, SUPER-CHIP and XO-CHIP games.

## What it does

- Runs CHIP-8 programs in a desktop window or in the browser, with a GUI
  built with [egui](https://github.com/emilk/egui).
- Includes a catalogue of 61 ROMs: games, Octojam titles, and the
  [Timendus test suite](https://github.com/Timendus/chip8-test-suite).
- Uses metadata from the
  [CHIP-8 database](https://github.com/chip-8/chip-8-database) to show each
  program's title and details.
- Lets you choose a colour scheme and adjust the speed (ticks per frame).

## Running it

> [!NOTE]
> These steps are for reference only. I haven't tried them recently.

You need a recent stable Rust (`rustup update`).

**Desktop:**

```sh
cargo run --release
```

On Linux, first install the libraries egui needs:

```sh
sudo apt-get install libxcb-render0-dev libxcb-shape0-dev libxcb-xfixes0-dev libxkbcommon-dev libssl-dev
```

**Web:** the build uses [Trunk](https://trunkrs.dev/).

```sh
rustup target add wasm32-unknown-unknown
cargo install --locked trunk
trunk serve            # then open http://127.0.0.1:8080/index.html#dev
```

`trunk build --release` writes a static site to `dist/`. The GitHub Actions
workflow in `.github/workflows/pages.yml` deploys it to GitHub Pages.

## License

[Apache 2.0](LICENSE). The ROMs in `roms/` belong to their authors.
