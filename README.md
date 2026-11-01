# Edit arrays and compute numeric reductions

Pure Buoy array range editing and numeric reductions inspired by [Joe Strout's
REALbasic ArrayUtils](https://strout.net/info/coding/rb/intro.html). Source and
sealed `.buipkg` consumers use `Import arrayutils`. No native dependencies.

## Install

From a Buoy consumer project with BPM installed:

```sh
bpm add arrayutils --git https://github.com/BuoyBay/arrayutils.git --rev refs/heads/main
```

BPM records the resolved commit in its lockfile. Keep that lockfile with the
consumer project for reproducible installs.

## Example

```buoy
Import arrayutils

Sub Main()
    Dim scores As Array Of Integer = [10, 20, 30, 40, 50]
    Print Average(scores)
    Dim tail As Array Of Integer = Slice(scores, -2, 0)
    Print Total(tail)
    Dim editable As Array Of String = Array.AsResizable(["one", "two", "three"])
    Splice(editable, 1, 2, ["second", "inserted"], 0, 0)
    Reverse(editable)
    For Each word As String In editable
        Print word
    Next
End Sub
```

## Build from source

With the native `build-packages` driver from [devtools](https://github.com/BuoyBay/devtools)
on your `PATH`, run from this checkout:

```sh
build-packages --root "$PWD" --compile-consumer arrayutils
```

The driver checks source targets and compiles an import consumer. See the
[API guide](docs/API.md) for behavior, limits and any host prerequisites.

## Local Buoy setup

On your own machine, install Buoy and run:

```sh
buoy ai init --both
```

The generated agent files and editor settings stay local and are ignored by Git.

## Contributing

[Contributing](CONTRIBUTING.md) · [License](LICENSE)
