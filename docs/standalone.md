# Standalone build

This fork is based on PdfCraft by the ArtCraft team. It runs as its own desktop
application. You do not need ArtCraft installed, a launcher, an account or a
community connection. The home community card, title-bar invitation, promotional
Help commands and About branding have been removed, together with unused
translations and upstream trademark images. Copyright and third-party notices
are retained.

## Build and run

Install Rust 1.95 or later and your platform's native build tools. On Windows,
use the MSVC Rust toolchain and Visual Studio's Desktop development with C++
workload (including the Windows SDK). Linux needs the libraries listed in
`.github/workflows/ci.yml`; macOS needs the Xcode command-line tools.

```sh
git clone https://github.com/Javed-Ali/Mypdfcraft
cd Mypdfcraft
cargo build --release --locked -p pdfcraft
```

Run `target/release/pdfcraft.exe` on Windows, or `target/release/pdfcraft` on
macOS/Linux. You can pass a PDF path as an argument. Normal reading and editing
work offline. The CLI is optional and built separately:

```sh
cargo build --release --locked -p pdfcraft-cli
```

Cargo downloads the pinned open-source dependencies while building, including
the shared `craft-libs` libraries. These are compiled into the program; they do
not require installing or running ArtCraft. The optional `craft-fonts` build input
embeds additional fonts for Japanese and other scripts; see the main README.
`cargo xtask models` fetches optional OCR models. Neither is needed to launch
the app or read ordinary PDFs.

Source, Help, package metadata and manual update checks point to this fork.
There are no automatic update checks. Until a release is published in this
fork, Check for updates can report that no release was found. Upstream binaries
still contain the upstream interface. This fork does not inherit upstream's
code-signing credentials or prebuilt releases.

Old promotional screenshots have been removed. To generate fresh screenshots,
run `cargo xtask demo-pdf` and `cargo xtask screenshots` on a configured build
machine. `cargo xtask assets --write` regenerates attribution after asset changes.
