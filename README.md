# sysfs

Go library for more reliable interactions with sysfs drivers. The sysfs library
assumes that your interactions with a sysfs driver is simple all-or-nothing
reading or writing data to files under `/sys/class/...`. To make the
interactions simpler and easier to test, write your classes to receive and use a
`sysfs.DeviceFile` interface rather than directly writing to the device files.

Testing and running on systems without the sysfs drivers can use the
DeviceFile implementations in `sysfs/sysfstest` to simulate the behavior
of a device, allow the app to be used on systems without the correct
drivers, and generate reliable input for testing.

When used in production builds, the standard `HardwareFile` implementation
can be proxied with other support classes in `sysfs` that will log
sysfs interactions, gather statistics, etc.
