workspace(
    name = "project", 
    managed_directories = {"@npm": ["node_modules"]},
)
load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

# ================================================================
# NodeJS
# ================================================================

http_archive(
    name = "build_bazel_rules_nodejs",
    sha256 = "f10a3a12894fc3c9bf578ee5a5691769f6805c4be84359681a785a0c12e8d2b6",
    urls = ["https://github.com/bazelbuild/rules_nodejs/releases/download/5.5.3/rules_nodejs-5.5.3.tar.gz"],
)

load("@build_bazel_rules_nodejs//:repositories.bzl", "build_bazel_rules_nodejs_dependencies")

build_bazel_rules_nodejs_dependencies()

load("@build_bazel_rules_nodejs//:index.bzl", "yarn_install")

yarn_install(
    # Name this npm so that Bazel Label references look like @npm//package
    name = "npm",
    exports_directories_only = True,
    frozen_lockfile = False,    
    package_json = "//:package.json",
    yarn_lock = "//:yarn.lock",
)

