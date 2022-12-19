# disable-p2
a fork of diable-c6 but for p2 state (voltage too low and reboot)(maybe not complete, not sure if it fixes 100% of the problems but for me it looks like it works)

A systemd service to disable the p2 state upon system boot, preventing Ryzen freezes. [Here is some info on the bug](https://bugzilla.kernel.org/show_bug.cgi?id=196683).

This simply installs `zenstates.py` from [ZenStates-Linux](https://github.com/r4m0n/ZenStates-Linux) and creates a one-shot service based on it.

## Prerequisites

The `zenstates.py` script requires the `msr` kernel module. Ensure that you're either loading the `msr` module at startup or have it compiled into the kernel. If `/dev/cpu/*/msr` exists, then your `msr` module is active.

Refer to your specific distribution and init system to find out how to load kernel modules. For instance, if you're using systemd, refer to `man modules-load.d`.

## Installation
just run `./install.sh`
This will install a systemd unit called `disable-p2` to the default location, `/usr/local/lib/systemd/system/disable-p2.service`, and offer to enable/start the service for you.

You can also customize the install location. See `./install.sh --help` for options.
