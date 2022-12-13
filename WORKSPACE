workspace(name = "cloud-cpp-mini-client")

load("@bazel_tools//tools/build_defs/repo:git.bzl", "git_repository")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

#git_repository(
#    name = "google_cloud_cpp",
#    remote = "https://github.com/googleapis/google-cloud-cpp.git",
#    branch = "main",
#)

http_archive(
    name = "google_cloud_cpp",
    sha256 = "ac93ef722d08bfb220343bde2f633c7c11f15e34ec3ecd0a57dbd3ff729cc3a6",
    strip_prefix = "google-cloud-cpp-2.5.0",
    url = "https://github.com/googleapis/google-cloud-cpp/archive/v2.5.0.tar.gz",
)

# Load indirect dependencies due to
#     https://github.com/bazelbuild/bazel/issues/1943
load("@google_cloud_cpp//bazel:google_cloud_cpp_deps.bzl", "google_cloud_cpp_deps")

google_cloud_cpp_deps()

load("@com_google_googleapis//:repository_rules.bzl", "switched_rules_by_language")

switched_rules_by_language(
    name = "com_google_googleapis_imports",
    cc = True,
    grpc = True,
)

load("@com_github_grpc_grpc//bazel:grpc_deps.bzl", "grpc_deps")

grpc_deps()

load("@com_github_grpc_grpc//bazel:grpc_extra_deps.bzl", "grpc_extra_deps")

grpc_extra_deps()
