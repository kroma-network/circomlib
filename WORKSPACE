workspace(name = "kroma_network_circomlib")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "kroma_network_rules_circom",
    sha256 = "53f91f916b56e8f3070f1a594b625866afafe53057222a02796bee6f06dfc349",
    strip_prefix = "rules_circom-977a8c486949d86bd4099a4e85deca56a9e47233",
    urls = ["https://github.com/kroma-network/rules_circom/archive/977a8c486949d86bd4099a4e85deca56a9e47233.tar.gz"],
)

load("@kroma_network_rules_circom//:rules_circom_deps.bzl", "rules_circom_deps")

rules_circom_deps()

load("@rules_rust//rust:repositories.bzl", "rules_rust_dependencies", "rust_register_toolchains")

rules_rust_dependencies()

rust_register_toolchains(
    edition = "2021",
    versions = [
        "1.66.1",
    ],
)

load("@rules_rust//crate_universe:repositories.bzl", "crate_universe_dependencies")

crate_universe_dependencies()

load("@rules_rust//crate_universe:defs.bzl", "crates_repository")

crates_repository(
    name = "crate_index",
    cargo_lockfile = "@kroma_network_rules_circom//:Cargo.lock",
    lockfile = "@kroma_network_rules_circom//:Cargo.Bazel.lock",
    manifests = ["@kroma_network_rules_circom//:Cargo.toml"],
)

load("@crate_index//:defs.bzl", "crate_repositories")

crate_repositories()
