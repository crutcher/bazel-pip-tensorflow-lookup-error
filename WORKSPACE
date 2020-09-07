load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")
load("@bazel_tools//tools/build_defs/repo:git.bzl", "git_repository")

# =======================================================================
# Load python resource rules.

RULES_PYTHON_TAG = "0.0.2"

RULES_PYTHON_SHA256 = "b5668cde8bb6e3515057ef465a35ad712214962f0b3a314e551204266c7be90c"

#http_archive(
#    name = "rules_python",
#    sha256 = RULES_PYTHON_SHA256,
#    strip_prefix = "rules_python-%s" % RULES_PYTHON_TAG,
#    url = "https://github.com/bazelbuild/rules_python/releases/download/%s/rules_python-%s.tar.gz" % (RULES_PYTHON_TAG, RULES_PYTHON_TAG),
#)

git_repository(
    name = "rules_python",
    remote = "https://github.com/bazelbuild/rules_python.git",
    commit = "6ed1fe53f8b36ecd404d98634d8e7411531cd6f8",
    shallow_since = "1598886558 -0700",
)

load("@rules_python//python:repositories.bzl", "py_repositories")

py_repositories()

load("@rules_python//python:pip.bzl", "pip_import", "pip_repositories")

pip_repositories()

pip_import(
    name = "pip_deps",
    python_interpreter="python3.7",
    requirements = "//:requirements.txt",
)

load("@pip_deps//:requirements.bzl", "pip_install")

pip_install()

