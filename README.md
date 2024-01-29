# capsule

> A rather clumsy attempt to have a static blog generator (based on
> [YOCaml](https://github.com/xhtmlboi/yocaml)) that puts less pressure on me to
> write long articles that nobody reads.

## Local installation

The most standard way to start a development environment is to build a "_local
switch_" by sequentially running these different commands (which assume that
[OPAM](https://opam.ocaml.org/) is installed on your machine).

```shellsession
opam update
opam switch create . ocaml-base-compiler.5.1.1 --deps-only -y
eval $(opam env)
```

Once the switch has been initialized, you need to install _the pinned
dependencies_ by running these commands:

```shellsession
opam install nightmare nightmare-tyxml -y
opam install nightmare_js nightmare_js-vdom -y
opam install yourbones yourbones-ppx yourbones_js yourbones_js-beacon -y
```

Otherwise, if you use `make`, you can just run the command `make deps`.

And since the JavaScript part of the application relay on ... `npm`, you have to
install `npm` and running `make` will build the inner library... `hell.js`.

If everything went well, which I don't doubt for a second, the project should be
compilable and executable, you can now contribute to this blog, for example, to
correct spelling mistakes... For ease of use, I use `make` as a very
_sophisticated orchestrator_. You can run the `make` command to build the binary
that statically serves the site.

## Up and running

- `dune exec bin/capsule.exe -- build [--target=TARGET]` build the website into `TARGET`
- `dune exec bin/capsule.exe -- watch [--target=TARGET] [--port=PORT]` build the website
  into `TARGET` and serve `TARGET` listening `PORT`.
