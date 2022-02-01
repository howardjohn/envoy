workspace(name = "envoy")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")
load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")
http_archive(
    name = "bazel_skylib",
    urls = [
        "https://mirror.bazel.build/github.com/bazelbuild/bazel-skylib/releases/download/1.1.1/bazel-skylib-1.1.1.tar.gz",
        "https://github.com/bazelbuild/bazel-skylib/releases/download/1.1.1/bazel-skylib-1.1.1.tar.gz",
    ],
    sha256 = "c6966ec828da198c5d9adbaa94c05e3a1c7f21bd012a0b29ba8ddbccb2c93b0d",
)
http_archive(
    name = "platforms",
    urls = [
        "https://mirror.bazel.build/github.com/bazelbuild/platforms/releases/download/0.0.4/platforms-0.0.4.tar.gz",
        "https://github.com/bazelbuild/platforms/releases/download/0.0.4/platforms-0.0.4.tar.gz",
    ],
    sha256 = "079945598e4b6cc075846f7fd6a9d0857c33a7afc0de868c2ccb96405225135d",
)

BAZEL_ZIG_CC_VERSION = "v0.4.2"

http_archive(
    name = "bazel-zig-cc",
    sha256 = "135f906ebf936a282b53e2d4516cdc86a283880ac4d6f3399f6fced2cd86c768",
    strip_prefix = "bazel-zig-cc-{}".format(BAZEL_ZIG_CC_VERSION),
    urls = ["https://git.sr.ht/~motiejus/bazel-zig-cc/archive/{}.tar.gz".format(BAZEL_ZIG_CC_VERSION)],
)

load("@bazel-zig-cc//toolchain:defs.bzl", zig_register_toolchains = "register_toolchains")

zig_register_toolchains(register = [
    # "x86_64-linux-gnu.2.33",
    "x86_64-linux-gnu.2.18",
    "aarch64-linux-gnu.2.33",
],
version = "0.10.0-dev.490+dd7309bde",
url_format= "https://ziglang.org/builds/zig-{host_platform}-{version}.tar.xz",
host_platform_sha256= {
    "linux-x86_64": "45af0295e8a26bcae5bf92b4cb73694211498287816d9e891ed3b053e7c13016",
    "linux-aarch64": "9bcac8e1fe47c1ca30aa8313c0cc0a5b46e80c42014fd544db913f6768e96155"
})

load("//bazel:api_binding.bzl", "envoy_api_binding")

envoy_api_binding()

load("//bazel:api_repositories.bzl", "envoy_api_dependencies")

envoy_api_dependencies()

load("//bazel:repositories.bzl", "envoy_dependencies")

envoy_dependencies()

load("//bazel:repositories_extra.bzl", "envoy_dependencies_extra")

envoy_dependencies_extra()

load("//bazel:dependency_imports.bzl", "envoy_dependency_imports")

envoy_dependency_imports()


