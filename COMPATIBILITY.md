# Compatibility policy

`is-msgs-sea` follows additive Protobuf evolution rules:

- existing field names, numbers, scalar/message types, enum names, and enum
  numbers are not changed;
- deleted tags and names must be declared `reserved` in a future release;
- new fields must use new tag numbers and old readers are expected to ignore
  them;
- serialized Protobuf bytes, rather than JSON output, define wire
  compatibility;
- Python releases support Python 3.10–3.14 with Protobuf 5–7.

CI compares the current descriptor surface to tag `v1.1.18`. `validate.proto`
is intentionally unchanged in 1.2.0 because its extensions are part of that
surface.
