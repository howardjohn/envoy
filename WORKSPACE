workspace(name = "envoy")

load("//bazel:api_binding.bzl", "envoy_api_binding")

envoy_api_binding()

load("//bazel:api_repositories.bzl", "envoy_api_dependencies")

envoy_api_dependencies()

load("//bazel:repositories.bzl", "envoy_dependencies")

envoy_dependencies()

load("//bazel:repositories_extra.bzl", "envoy_dependencies_extra")

envoy_dependencies_extra()

load("//bazel:python_dependencies.bzl", "envoy_python_dependencies")

envoy_python_dependencies()

load("//bazel:dependency_imports.bzl", "envoy_dependency_imports")

envoy_dependency_imports()

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "io_tweag_rules_nixpkgs",
    strip_prefix = "rules_nixpkgs-9b13ed0469116a37658040a7b62d70aea90ad0bc",
    urls = ["https://github.com/tweag/rules_nixpkgs/archive/9b13ed0469116a37658040a7b62d70aea90ad0bc.tar.gz"],
)

load("@io_tweag_rules_nixpkgs//nixpkgs:repositories.bzl", "rules_nixpkgs_dependencies")
rules_nixpkgs_dependencies()

load("@io_tweag_rules_nixpkgs//nixpkgs:nixpkgs.bzl", "nixpkgs_git_repository", "nixpkgs_package", "nixpkgs_cc_configure")
nixpkgs_git_repository(
    name = "nixpkgs",
    revision = "d7570b04936e9b0f5268e0d834dee40368ad3308", # Any tag or commit hash
    sha256 = "" # optional sha to verify package integrity!
)
nixpkgs_cc_configure(
  name = "nixpkgs_config_cc",
  repository = "@nixpkgs",
  attribute_path = "clang_15",
)

http_archive(
    name = "rules_cc",
    sha256 = "4dccbfd22c0def164c8f47458bd50e0c7148f3d92002cdb459c2a96a68498241",
    urls = [
        "https://github.com/bazelbuild/rules_cc/releases/download/0.0.1/rules_cc-0.0.1.tar.gz",
    ],
)
load("@rules_cc//cc:repositories.bzl", "rules_cc_dependencies", "rules_cc_toolchains")
rules_cc_dependencies()

rules_cc_toolchains()