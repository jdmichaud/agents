---
name: Rust development
description: Set of rules to follow when developing in Rust. Use this when
creating or updating a Rust based project.
---

# Rust development

This skills will help you develop and maintain Rust project in a organized and
standard way.

# When to use the skill

Use this skill whenever creating or updating a Rust based project or working
in the Rust language.

# Simple set of rules to follow

- Whenever you need to test a Rust based project, always compile the program in
  debug mode (`cargo build` or `cargo run`). Building in debug mode is faster
  and provide helpful error message in case of a crash. You release mode only
  when testing performance or binary size.

- Before committing, always run `cargo fmt` and `cargo clippy` in order to
  commit properly formatted Rust code.

- Whenever you create a Rust project, unless instructed otherwise or if it is
  technically impractical, create a release mode that allows for the compilation
  of a static binary with no dynamic dependency.

- When adding dependencies to Rust projects, use cargo add.

- Prefer expect() over unwrap(). The expect message should be very concise, and
  should explain why that expect call cannot fail.