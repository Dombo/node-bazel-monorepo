workspace(name = 'monorepo')

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "build_bazel_rules_typescript",
    url = "https://github.com/bazelbuild/rules_typescript/archive/0.21.0.zip",
    strip_prefix = "rules_typescript-0.21.0",
)

# Fetch our Bazel dependencies that aren't distributed on npm
load("@build_bazel_rules_typescript//:package.bzl", "rules_typescript_dependencies")
rules_typescript_dependencies()

# Setup TypeScript toolchain
load("@build_bazel_rules_typescript//:defs.bzl", "ts_setup_workspace")
ts_setup_workspace()

# Setup the NodeJS toolchain
load("@build_bazel_rules_nodejs//:defs.bzl", "node_repositories", "npm_install")
node_repositories()

# Setup Bazel managed npm dependencies with the `npm_install` rule.
npm_install(
  name = "npm",
  package_json = "//:package.json",
  package_lock_json = "//:package-lock.json",
)

