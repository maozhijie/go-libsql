先准备 Rust 构建工具链（`rustc`/`cargo`）。如果你在 Linux/macOS 上构建多架构产物，推荐安装 `cross`：

```
cargo install cross
```

然后拉取 `libsql` 并构建 `libsql_experimental`：

```
git clone https://github.com/tursodatabase/libsql.git
cd libsql/bindings/c
```

Linux（推荐用 `cross`）：

```
cross build --release --target x86_64-unknown-linux-gnu
cross build --release --target aarch64-unknown-linux-gnu
```

Windows amd64（建议产出 MinGW 兼容的静态库）：

```
rustup target add x86_64-pc-windows-gnu
cargo build --release --target x86_64-pc-windows-gnu
```

最后把产物复制到本仓库的 `lib` 目录对应平台目录下：

```
libsql/target/<target>/release/libsql_experimental.a
```
