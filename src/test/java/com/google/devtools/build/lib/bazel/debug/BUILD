load("@rules_java//java:defs.bzl", "java_test")

package(
    default_testonly = 1,
    default_visibility = ["//src:__subpackages__"],
)

filegroup(
    name = "srcs",
    testonly = 0,
    srcs = glob(["**"]),
    visibility = ["//src/test/java/com/google/devtools/build/lib/bazel:__pkg__"],
)

java_test(
    name = "WorkspaceRuleEventTest",
    size = "small",
    srcs = ["WorkspaceRuleEventTest.java"],
    deps = [
        "//src/main/java/com/google/devtools/build/lib/bazel/debug:workspace-rule-event",
        "//src/main/java/com/google/devtools/build/lib/bazel/debug:workspace_log_java_proto",
        "//src/main/java/com/google/devtools/build/lib/syntax:frontend",
        "//third_party:guava",
        "//third_party:junit4",
        "//third_party:mockito",
        "//third_party:truth",
    ],
)
