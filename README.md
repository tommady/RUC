# myutil

A simple and friendly `error-chain`.

## Usage

```rust
use myutil::{err::*, *};

fn will_panic() {
    let l1 = || -> Result<()> { Err(eg!("Some error occur!")) };

    let l2 = || -> Result<()> { l1().c(d!()) };

    let l3 = || -> Result<()> { l2().c(d!()) };

    let l4 = || -> Result<()> { l3().c(d!()) };

    pnk!(l4());
}
```

# OutPut Sample

```shell
000000 [pidns: NULL][pid: 46574] 2020-09-06 18:18:32
Error:
├── file: src/lib.rs
└── line: 318
Caused By:
├── file: src/lib.rs
└── line: 316
    Caused By:
    ├── file: src/lib.rs
    └── line: 314
        Caused By:
        ├── file: src/lib.rs
        └── line: 312
            Caused By: Some error occur!
            ├── file: src/lib.rs
            └── line: 310
```
