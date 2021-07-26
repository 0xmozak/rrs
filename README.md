# Rust RISC-V Simulator (rrs)

A RISC-V ISS implemented in Rust. Supports the RV32IM instruction set (no
exceptions or CSRs yet).

RRS is split into two parts, rrs-lib and rrs-cli

## rrs-lib

This crate implements the components required for the ISS. Documentation can be
generated via rustdoc

```sh
> cd rrs-lib
> cargo doc
```

Once generated it can be found in `target/doc/rrs-lib`

### Tests

`rrs-lib` implements a small number of tests, these can be run with cargo as
usual.

```sh
> cd rrs-lib
> cargo test
```

## rrs-cli

This crate implements a CLI for the ISS, build and run rrs-cli with a `--help`
argument to get full usage instructions.

```sh
> cd rrs-cli
> cargo run -- --help
```

E.g. to execute a binary `prog.bin` in a 1 MB memory starting at 0x20000000 

```sh
> cargo run -- --load_addr 20000000 --mem_size 100000 --binary prog.bin
```

rrs-cli has two special memory locations for output and controlling the
simulation.

* 0x80000000 - Write a character here to output it to stdout
* 0x80000004 - Write a non zero value here to terminate the simulation

## Blog

I've written about rrs on my blog, see:

* [Building a RISC-V Simulator in Rust - Part 1](https://gregchadwick.co.uk/blog/building-rrs-pt1/)
