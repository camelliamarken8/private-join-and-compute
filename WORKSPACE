# Copyright 2019 Google LLC.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     https://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

"""WORKSPACE file for Private Join and Compute."""

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")
load("//bazel:pjc_deps.bzl", "pjc_deps")

# gRPC
# must be included separately, since we need to load transitive deps of grpc.
http_archive(
    name = "com_github_grpc_grpc",
    strip_prefix = "grpc-1.68.0",
    integrity = "sha256-hvDyi3WxViyCt/xdQ2tPX12my41n9Z6f7F+Kof6SQDc=",
    urls = [
        "https://github.com/grpc/grpc/archive/v1.68.0.tar.gz",
    ],
)

load("@com_github_grpc_grpc//bazel:grpc_deps.bzl", "grpc_deps")
grpc_deps()

load("@com_github_grpc_grpc//bazel:grpc_extra_deps.bzl", "grpc_extra_deps")
grpc_extra_deps()

pjc_deps()

load("@rules_python//python:pip.bzl", "pip_parse")

pip_parse(
    name = "pip_deps",
    requirements_lock = ":requirements.txt",
)

load("@pip_deps//:requirements.bzl", "install_deps")

install_deps()