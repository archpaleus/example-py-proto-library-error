load("@com_google_protobuf//:protobuf.bzl", "py_proto_library")

py_proto_library(
    name = "my_py_proto",
    srcs = ["my.proto"],
    deps = [
      # This doesn't work because the new py_proto_library expects a
      # secondary target with suffix of _genproto,
      # ie ':protobuf_python_genproto'.
      #"@com_google_protobuf//:protobuf_python"

      # This should work because its visibility is set to public and is
      # clearly intended for external consumption, however, this is just
      # an alias and py_proto_library actually looks for a secondary target with
      # a suffix of _genproto, ie ':well_known_types_py_pb2_genproto", which
      # is not aliased.
      # ERROR: no such target '@com_google_protobuf//:well_known_types_py_pb2_genproto'
      #"@com_google_protobuf//:well_known_types_py_pb2"

      # This is the package private definition that py_proto_library wants.  It works,
      # but only if we turn off visibility checking with --nocheck_visibility.
      "@com_google_protobuf//python:well_known_types_py_pb2"
    ],
    visibility = ["//visibility:public"],
)

