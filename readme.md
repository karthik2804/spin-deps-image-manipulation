# Spin component dependencies: image manipulation

This repository contains an example of using the new Spin v3 feature for
component dependencies and an image manipulation example.


### Prerequisites

* Spin v3
* Spin templates
* the `spin deps` plugin
* `cargo component

### Steps to reproduce

* create a new library using `cargo component`:

```console
$ cargo component new --lib image-manipulation-lib
```

* once the component is implemented, publish to a registry:

```
$ spin deps publish target/wasm32-wasip1/release/image_manipulation_lib.wasm --registry fermyon.com --package fermyon-experimental:image-manipulation-lib@1.0.0
Published fermyon-experimental:image-manipulation-lib@1.0.0
```

* add the component:

```
$ spin deps add --registry fermyon.com fermyon-experimental:image-manipulation-lib@1.0.0
```

* generate bindings:

```
$ spin deps generate-bindings --language rust --output image-manipulation-http-rs/src/bindings --component-id image-manipulation-http-rs
```
