# Mog Window

`github.com/moglang/window` is Mog's official SDL2-backed native window package.
It is a standalone source repository. The Mog language runtime does not build or
bundle it.

For normal projects, install the signed prebuilt artifact from your configured
registry and import the package by its canonical module path:

```mog
const window = @import("github.com/moglang/window")
```

The manifest keeps `import_name = "window"`, so managed projects may also use
`@import("window")` after installation. The canonical module path is preferred
in shared code.

Registry projects should depend on the registry package ID while retaining the
module import:

```toml
[dependencies]
window = { package = "github:window", version = "^0.1.0", registry = "official" }
```

For contributor and source-build workflows, add the Git module at a signed tag;
Mog will build this repository with CMake and the system SDL2 development
package. Build directly with:

```bash
cmake -S . -B build -DCMAKE_BUILD_TYPE=Release
cmake --build build --config Release
```

Release tags run GitHub Actions to build Linux and macOS bundles and publish
signed native artifacts using the configured registry credentials.
