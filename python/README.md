# is-msgs-sea for Python

The distribution is named `is-msgs-sea`; the import package remains
`is_msgs` so existing source code does not need to change.

```shell
uv remove is-msgs
uv add is-msgs-sea==1.2.0
```

Python 3.10 through 3.14 and Protobuf 5 through 7 are supported. Do not install
`is-msgs` and `is-msgs-sea` together because both provide `is_msgs`.

## Compiling application protos

Install the opt-in compiler and invoke the module without changing your
project directory:

```shell
uv add 'is-msgs-sea[codegen]==1.2.0'
uv run python -m is_msgs.utils.build --output generated proto/my_service.proto
```

Application schemas may keep the canonical import:

```protobuf
import "is/msgs/common.proto";
```

The installed wheel already contains generated `*_pb2.py`, type stubs, and
transformed imports. Installation never downloads `protoc` or generates code.

## Reproducible repository codegen

```shell
uv sync --extra codegen
uv run python scripts/generate_python.py
git diff --exit-code
```

Build and validate a release with:

```shell
uv build
uv publish --dry-run dist/*
```

After explicit authorization, publish those exact artifacts with `uv publish
dist/*`.
