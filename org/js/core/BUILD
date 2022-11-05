load("@npm//@bazel/typescript:index.bzl", "ts_project")
load("@build_bazel_rules_nodejs//:index.bzl", "pkg_npm")
load("@build_bazel_rules_nodejs//:index.bzl", "js_library")

ts_project(
    name = "core_js_src",
    srcs = glob(["src/*.ts", "src/**/*.ts"], exclude = ["src/**/*.spec.ts"]),
    extends = "//:tsconfig.base.json",
    tsconfig = "tsconfig.json",
    out_dir = "build",
    root_dir = "src",
    tsc = "@npm//typescript/bin:tsc",
    deps = [ 
    	"@npm//tslib",
    ],
   
	declaration_map = True,
	resolve_json_module = True,
	source_map = True,
	composite = True,
	declaration = True,
	incremental = True,
 	visibility = ["//visibility:public"]    
)

js_library(
    name = "lib",
    package_name = "@org-js/core",
    deps = [
        ":core_js_src",
    ],
 	visibility = ["//visibility:public"],
)

pkg_npm(
    name = "package",
    package_name = "@org-js/core",
    deps = [":core_js_src"],
	visibility = ["//visibility:public"]    
)