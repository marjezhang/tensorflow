# Description:
#   The new XLA client libraries.
#
# This is NOT YET ready to use.

licenses(["notice"])  # Apache 2.0

package(default_visibility = [":friends"])

package_group(
    name = "friends",
    includes = [
        "//tensorflow/compiler/xla:friends",
    ],
)

# Filegroup used to collect source files for dependency checking.
filegroup(
    name = "c_srcs",
    data = glob([
        "**/*.cc",
        "**/*.h",
    ]),
)

load("//tensorflow:tensorflow.bzl", "tf_cc_test")

# TODO(b/74197823): Replace computation_builder with xla_builder.
cc_library(
    name = "xla_builder",
    srcs = ["xla_builder.cc"],
    hdrs = ["xla_builder.h"],
    deps = [
        "//tensorflow/compiler/xla:literal_util",
        "//tensorflow/compiler/xla:shape_util",
        "//tensorflow/compiler/xla:status_macros",
        "//tensorflow/compiler/xla:statusor",
        "//tensorflow/compiler/xla:types",
        "//tensorflow/compiler/xla:util",
        "//tensorflow/compiler/xla:xla_data_proto",
        "//tensorflow/compiler/xla/service:hlo",
        "//tensorflow/compiler/xla/service:hlo_proto",
        "//tensorflow/compiler/xla/service:shape_inference",
        "//tensorflow/core:lib",
    ],
)

tf_cc_test(
    name = "xla_builder_test",
    srcs = ["xla_builder_test.cc"],
    deps = [
        ":xla_builder",
        "//tensorflow/compiler/xla:literal_util",
        "//tensorflow/compiler/xla:shape_util",
        "//tensorflow/compiler/xla:status_macros",
        "//tensorflow/compiler/xla:test",
        "//tensorflow/compiler/xla:test_helpers",
        "//tensorflow/compiler/xla:xla_data_proto",
        "//tensorflow/compiler/xla/service:hlo",
        "//tensorflow/compiler/xla/service:hlo_matchers",
        "//tensorflow/core:test",
    ],
)

# -----------------------------------------------------------------------------

filegroup(
    name = "all_files",
    srcs = glob(
        ["**/*"],
        exclude = [
            "**/METADATA",
            "**/OWNERS",
        ],
    ),
    visibility = ["//tensorflow:__subpackages__"],
)
