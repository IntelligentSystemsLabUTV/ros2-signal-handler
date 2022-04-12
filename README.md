# ros2_signal_handler

Signal handler module for ROS 2 applications.

Can be used by any ROS 2 standalone application (but also to component managers, if that's needed), and allows to define custom behaviours upon process termination.

**The main motivation behind this is that `rclcpp::init` installs its own signal handler, thus overriding any other termination procedure you might need.**

This also adds support for initialization of custom ROS 2 contexts, and uses `sigaction` to manage handlers.

## Usage

This package is made of a single header only: `signal_handler.hpp`, so to access its functions you just need to include that.

All operations are performed by a `ROS2SignalHandler::SignalHandler` object; to use it, interface it with the following public methods:

- `SignalHandler::init` to initialize it;
- `SignalHandler::install` to install a new signal handler for a given signal;
- `SignalHandler::uninstall` to uninstall a previously-installed signal handler;
- `SignalHandler::ignore` to ignore a specific signal;
- `SignalHandler::fini` to reset the `SignalHandler` object and restore everything to default settings and behaviours.

Routines may throw `std` exceptions upon error.

Refer to code comments for specific API documentation.
