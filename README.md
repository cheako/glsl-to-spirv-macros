# glsl-to-spirv-macros

[![Documentation](https://docs.rs/glsl-to-spirv-macros/badge.svg)](https://docs.rs/glsl-to-spirv-macros)

```toml
[dependencies]
glsl-to-spirv-macros = "0.1.1"
```

Rust macros for generating SPIR-V binaries at compile time for use with Vulkan.

### [Documentation](https://docs.rs/glsl-to-spirv-macros)

Use this crate to compile your GLSL shaders at compile time into binaries embedded in your program.

Example usage:

```rust
use glsl_to_spirv_macros::{glsl_vs, include_glsl_fs};

static some_shader: &'static [u8] = glsl_vs!{r#"
    // Shader code here
"#};

fn main() {
    let another_shader = include_glsl_fs!("path/to/shader");
}
```

All macros in this crate return `&'static [u8]`, and can be used in the definition of `static` as well as local variables.
Every macro takes a string literal, e.g. `"..."`, `r#"..."#` etc.

These macros generate Vulkan-compatible SPIR-V binaries using the official glslang compiler - they
are not designed for use with other APIs, like OpenCL.

## License

This library is licensed under either of

 * Apache License, Version 2.0, ([LICENSE-APACHE](LICENSE-APACHE) or
   http://www.apache.org/licenses/LICENSE-2.0)
 * MIT license ([LICENSE-MIT](LICENSE-MIT) or
   http://opensource.org/licenses/MIT)

at your option.

### Contribution

Unless you explicitly state otherwise, any contribution intentionally submitted
for inclusion in the work by you, as defined in the Apache-2.0 license, shall be
dual licensed as above, without any additional terms or conditions.