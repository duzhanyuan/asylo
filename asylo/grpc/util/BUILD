#
# Copyright 2018 Asylo authors
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#

licenses(["notice"])  # Apache v2.0

load("//asylo/bazel:proto.bzl", "asylo_proto_library")

# The GrpcServerLauncher library is used for launching a gRPC server that hosts
# one or more services, each on its own thread.
cc_library(
    name = "grpc_server_launcher",
    srcs = ["grpc_server_launcher.cc"],
    hdrs = ["grpc_server_launcher.h"],
    visibility = ["//visibility:public"],
    deps = [
        "//asylo/util:status",
        "@com_github_grpc_grpc//:grpc++",
        "@com_github_grpc_grpc//:grpc++_codegen_base",
        "@com_google_absl//absl/strings",
        "@com_google_absl//absl/synchronization",
        "@com_google_asylo//asylo/util:logging",
    ],
)

# Tests for the GrpcServerLauncher library.
cc_test(
    name = "grpc_server_launcher_test",
    size = "medium",
    srcs = ["grpc_server_launcher_test.cc"],
    tags = ["regression"],
    deps = [
        ":grpc_server_launcher",
        "//asylo/test/grpc:messenger_client_impl",
        "//asylo/test/grpc:messenger_server_impl",
        "//asylo/test/util:status_matchers",
        "//asylo/test/util:test_main",
        "//asylo/util:status",
        "@com_github_grpc_grpc//:grpc++",
        "@com_github_grpc_grpc//test/core/util:grpc_test_util_base",
        "@com_google_absl//absl/memory",
        "@com_google_absl//absl/strings",
        "@com_google_absl//absl/time",
        "@com_google_googletest//:gtest",
    ],
)

asylo_proto_library(
    name = "enclave_server_proto",
    srcs = ["enclave_server.proto"],
    visibility = ["//visibility:public"],
    deps = ["//asylo:enclave_proto"],
)

cc_library(
    name = "enclave_server",
    hdrs = ["enclave_server.h"],
    visibility = ["//visibility:public"],
    deps = [
        ":enclave_server_proto_cc",
        "//asylo:enclave_runtime",
        "//asylo/util:status",
        "@com_github_grpc_grpc//:grpc++",
        "@com_github_grpc_grpc//:grpc_secure",
        "@com_google_absl//absl/synchronization",
        "@com_google_asylo//asylo/util:logging",
    ],
)
