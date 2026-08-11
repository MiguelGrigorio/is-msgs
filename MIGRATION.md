# Migrating from is-msgs 1.1.18

1. Remove `is-msgs` and install `is-msgs-sea==1.2.0`. Both distributions use
   the same `is_msgs` package and must not coexist.
2. Keep existing imports such as `from is_msgs.common_pb2 import Pose`.
3. Existing Pose, Speed, Position, Orientation, and RangeScan consumers may
   adopt the additive fields gradually.
4. Map `sensor_msgs/Image` to `is.vision.RawImage`. `is.vision.Image` now
   explicitly represents already compressed JPEG/PNG/WebP bytes or a URI.
5. Use `is.vision.CompressedImage` for `sensor_msgs/CompressedImage` and keep
   its ROS format string.
6. Preserve `PointCloud.data` as its original PointCloud2 byte buffer; do not
   expand it into floating-point lists or base64.

See [ROS field conventions](docs/ROS_FIELDS.md) for units and layouts.
