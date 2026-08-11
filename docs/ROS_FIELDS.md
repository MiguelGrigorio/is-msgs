# ROS field conventions

- `Header.stamp` is a Unix timestamp split into seconds and nanoseconds;
  `frame_id` is copied verbatim.
- Linear positions, translations, velocities, accelerations, ranges, and point
  clouds use ROS SI conventions (normally metres and metres per second).
- Angles and angular velocities use radians and radians per second.
- Quaternions use `(x, y, z, w)` without normalization by the library.
- Pose and speed covariances are row-major 6×6 arrays (36 doubles). IMU
  covariances are row-major 3×3 arrays (9 doubles).
- `RawImage.data` is the original row-major ROS image buffer. `step` includes
  row padding and `is_bigendian` is preserved.
- `Image.data` contains encoded JPEG, PNG, or WebP bytes, never base64.
- `PointCloud.data` and every PointField offset/type/count preserve the
  `sensor_msgs/PointCloud2` layout exactly.
- NaN and infinity are valid sensor values and are not sanitized.
