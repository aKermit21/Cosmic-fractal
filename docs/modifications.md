---
title: "Modifications"
description: "Modifications and adaptations"
---

# Modifications 🔨

For testing purposes when working with cloned project (not installed by script), all new (and old) images can be placed into `image/` subdirectory.

To modify and test changed code, it is recommended to use a separate build directory (e.g., `build-dev/`) containing a modified build settings instance:

```shell
meson setup build-dev/
cd build-dev/
meson configure --buildtype=custom --optimization=2
```
This will enable assertions and extensive logging.

