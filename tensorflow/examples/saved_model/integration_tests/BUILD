licenses(["notice"])  # Apache 2.0

exports_files(["LICENSE"])

load("//tensorflow:tensorflow.bzl", "cuda_py_test")

py_library(
    name = "integration_scripts",
    srcs = [
        "export_mnist_cnn.py",
        "export_rnn_cell.py",
        "export_simple_text_embedding.py",
        "export_text_rnn_model.py",
        "integration_scripts.py",
        "use_mnist_cnn.py",
        "use_model_in_sequential_keras.py",
        "use_rnn_cell.py",
        "use_text_embedding_in_dataset.py",
        "use_text_rnn_model.py",
    ],
    visibility = ["//tensorflow:internal"],
    deps = [
        ":mnist_util",
        ":util",
        "//tensorflow:tensorflow_py",
    ],
)

py_library(
    name = "util",
    srcs = ["util.py"],
    visibility = ["//tensorflow:internal"],
    deps = [
        "//tensorflow:tensorflow_py",
    ],
)

py_library(
    name = "mnist_util",
    srcs = ["mnist_util.py"],
    visibility = ["//tensorflow:internal"],
    deps = [
        "//tensorflow:tensorflow_py",
    ],
)

cuda_py_test(
    name = "saved_model_test",
    srcs = [
        "saved_model_test.py",
    ],
    additional_deps = [
        ":integration_scripts",
        "//tensorflow:tensorflow_py",
    ],
    shard_count = 4,
    tags = [
        "noasan",  # forge input size exceeded
        "nomsan",  # forge input size exceeded
        "notsan",  # forge input size exceeded
    ],
)
