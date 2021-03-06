# Description:
#   A grab-bag of testing utilities.

load("@rules_java//java:defs.bzl", "java_library", "java_test")

package(
    default_testonly = 1,
    default_visibility = [
        "//src:__subpackages__",
        "//tools:__subpackages__",
    ],
)

filegroup(
    name = "srcs",
    testonly = 0,
    srcs = glob(["*"]),
    visibility = ["//src:__subpackages__"],
)

java_library(
    name = "testutil",
    testonly = 1,
    srcs = [
        "BazelTestSuiteBuilder.java",
        "BlazeTestUtils.java",
        "BuildRuleBuilder.java",
        "BuildRuleWithDefaultsBuilder.java",
        "DebuggingEventHandler.java",
        "FakeAttributeMapper.java",
        "FoundationTestCase.java",
        "ManualClock.java",
        "ManualSleeper.java",
        "ManualSleeperTest.java",
        "Scratch.java",
        "Suite.java",
        "TestFileOutErr.java",
        "TestRuleClassProvider.java",
        "TestSpec.java",
        "TimestampGranularityUtils.java",
        "UnknownRuleConfiguredTarget.java",
    ],
    runtime_deps = ["//src/main/java/com/google/devtools/build/lib/unix"],
    deps = [
        ":JunitUtils",
        ":TestConstants",
        ":TestSuite",
        ":TestUtils",
        "//src/main/java/com/google/devtools/build/lib:build",
        "//src/main/java/com/google/devtools/build/lib:filetype",
        "//src/main/java/com/google/devtools/build/lib:os_util",
        "//src/main/java/com/google/devtools/build/lib/clock",
        "//src/main/java/com/google/devtools/build/lib/cmdline",
        "//src/main/java/com/google/devtools/build/lib/collect/nestedset",
        "//src/main/java/com/google/devtools/build/lib/packages",
        "//src/main/java/com/google/devtools/build/lib/packages:build_type",
        "//src/main/java/com/google/devtools/build/lib/packages:type",
        "//src/main/java/com/google/devtools/build/lib/syntax:frontend",
        "//src/main/java/com/google/devtools/build/lib/util/io",
        "//src/main/java/com/google/devtools/build/lib/util/io:out-err",
        "//src/main/java/com/google/devtools/build/lib/vfs:pathfragment",
        "//src/main/java/com/google/devtools/build/lib/vfs/inmemoryfs",
        "//third_party:guava",
        "//third_party:jsr305",
        "//third_party:junit4",
        "//third_party:truth",
    ],
)

java_library(
    name = "BazelPackageBuilderHelperForTesting",
    testonly = 0,
    srcs = ["BazelPackageBuilderHelperForTesting.java"],
    deps = [
        "//src/main/java/com/google/devtools/build/lib:build-base",
        "//src/main/java/com/google/devtools/build/lib:syntax",
        "//src/main/java/com/google/devtools/build/lib/cmdline",
        "//src/main/java/com/google/devtools/build/lib/packages",
        "//src/main/java/com/google/devtools/build/lib/skyframe/packages:BazelPackageLoader",
        "//src/main/java/com/google/devtools/build/lib/skyframe/packages:PackageLoader",
        "//src/main/java/com/google/devtools/build/lib/vfs",
        "//third_party:guava",
    ],
)

java_library(
    name = "TestRunnableWrapper",
    srcs = ["TestRunnableWrapper.java"],
    deps = [
        "//src/main/java/com/google/devtools/build/lib/concurrent",
        "//third_party:guava",
    ],
)

java_library(
    name = "TestThread",
    srcs = ["TestThread.java"],
    deps = [
        "//third_party:guava",
        "//third_party:truth",
    ],
)

java_library(
    name = "TestUtils",
    srcs = ["TestUtils.java"],
)

java_library(
    name = "TestSuite",
    srcs = [
        "ClasspathSuite.java",
        "CustomSuite.java",
        "TestSuiteBuilder.java",
    ],
    deps = [
        "//src/main/java/com/google/devtools/build/lib:classpath-util",
        "//third_party:guava",
        "//third_party:junit4",
    ],
)

java_library(
    name = "EventUtils",
    srcs = [
        "EventIterableSubject.java",
        "EventIterableSubjectFactory.java",
    ],
    deps = [
        "//src/main/java/com/google/devtools/build/lib/events",
        "//third_party:guava",
        "//third_party:jsr305",
        "//third_party:truth",
    ],
)

java_library(
    name = "JunitUtils",
    srcs = [
        "MoreAsserts.java",
    ],
    deps = [
        ":TestConstants",
        "//src/main/java/com/google/devtools/build/lib:util",
        "//src/main/java/com/google/devtools/build/lib/events",
        "//third_party:guava",
        "//third_party:junit4",
        "//third_party:truth",
    ],
)

# Library exposing Blaze constants for TAP's usage.
java_library(
    name = "TestConstants",
    srcs = [
        "TestConstants.java",
    ],
    deps = [
        "//src/main/java/com/google/devtools/build/lib/rules/cpp",
        "//third_party:guava",
    ],
)

java_library(
    name = "SkyframeExecutorTestHelper",
    srcs = [
        "SkyframeExecutorTestHelper.java",
    ],
    deps = ["//src/main/java/com/google/devtools/build/lib:build-base"],
)

java_library(
    name = "TestPackageFactoryBuilderFactory",
    srcs = [
        "TestPackageFactoryBuilderFactory.java",
    ],
    deps = [
        ":PackageFactoryBuilderFactoryForBazelUnitTests",
        "//src/main/java/com/google/devtools/build/lib/packages:builder_factory_for_testing",
    ],
)

java_library(
    name = "PackageFactoryBuilderFactoryForBazelUnitTests",
    srcs = ["PackageFactoryBuilderFactoryForBazelUnitTests.java"],
    deps = [
        ":BazelPackageBuilderHelperForTesting",
        "//src/main/java/com/google/devtools/build/lib:build-base",
        "//src/main/java/com/google/devtools/build/lib/packages",
        "//src/main/java/com/google/devtools/build/lib/packages:builder_factory_for_testing",
        "//src/main/java/com/google/devtools/build/lib/skyframe/packages:PackageFactoryBuilderWithSkyframeForTesting",
        "//src/main/java/com/google/devtools/build/lib/vfs",
    ],
)

java_library(
    name = "TestUtilTests_lib",
    srcs = [
        "MoreAssertsTest.java",
        "TestSizeAnnotationTest.java",
    ],
    deps = [
        ":JunitUtils",
        ":testutil",
        "//third_party:junit4",
        "//third_party:truth",
    ],
)

java_test(
    name = "TestUtilTests",
    size = "small",
    test_class = "com.google.devtools.build.lib.AllTests",
    runtime_deps = [
        ":TestUtilTests_lib",
        "//src/test/java/com/google/devtools/build/lib:test_runner",
    ],
)
