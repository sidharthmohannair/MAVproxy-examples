
# MAVProxy Commands and Examples

[MAVProxy](https://github.com/ArduPilot/MAVProxy) is a powerful command-line ground control station for UAVs. It allows you to monitor, control, and configure your drone from your terminal. Below is a guide on common MAVProxy commands and examples on how to use them effectively.

## Prerequisites

Before diving into MAVProxy commands, ensure you have completed the steps in the [Installing ArduPilot and MAVProxy on Ubuntu 20.04](https://github.com/sidharthmohannair/Installing-ArduPilot-and-MAVProxy-on-Ubuntu-20.04) guide.

## Basic MAVProxy Usage

Start MAVProxy with the following command:

```bash
mavproxy.py --master=<connection_string>
```

### Example

To connect to a flight controller over USB:

```bash
mavproxy.py --master=/dev/ttyUSB0 --baudrate 115200 --aircraft MyCopter
```

Replace `/dev/ttyUSB0` with your specific device path.

## MAVProxy Console Commands

Once MAVProxy is running, you can issue commands via the console. Below are some of the essential commands:

### Basic Commands

- **arm throttle**: Arms the drone, enabling the motors.
  ```bash
  arm throttle
  ```
  Example:
  ```bash
  arm throttle
  ```

- **disarm**: Disarms the drone, stopping the motors.
  ```bash
  disarm
  ```

- **mode <mode_name>**: Changes the flight mode.
  ```bash
  mode GUIDED
  ```
  Example:
  ```bash
  mode LOITER
  ```

- **takeoff <altitude>**: Commands the drone to take off to a specified altitude.
  ```bash
  takeoff 10
  ```

### Navigation Commands

- **wp load <file>**: Loads a mission plan from a file.
  ```bash
  wp load mission.txt
  ```
  Example:
  ```bash
  wp load /path/to/mission.txt
  ```

- **wp list**: Lists all waypoints in the current mission.
  ```bash
  wp list
  ```

- **wp clear**: Clears the current mission waypoints.
  ```bash
  wp clear
  ```

- **guided <latitude> <longitude> <altitude>**: Commands the drone to fly to a specified location in GUIDED mode.
  ```bash
  guided 37.7749 -122.4194 50
  ```

### Data Display and Monitoring

- **status**: Displays the current status of the drone, including GPS, battery, and more.
  ```bash
  status
  ```

- **altitude**: Shows the current altitude of the drone.
  ```bash
  altitude
  ```

- **battery**: Displays the current battery voltage and current usage.
  ```bash
  battery
  ```

- **attitude**: Shows the current attitude (pitch, roll, yaw) of the drone.
  ```bash
  attitude
  ```

### Advanced Commands

- **param set <name> <value>**: Sets a parameter to a specified value.
  ```bash
  param set ALT_HOLD_RTL 1000
  ```

- **param show**: Lists all the parameters and their current values.
  ```bash
  param show
  ```

- **module load <module_name>**: Loads a MAVProxy module.
  ```bash
  module load map
  ```

- **module unload <module_name>**: Unloads a MAVProxy module.
  ```bash
  module unload map
  ```

## Practical Examples

### Example 1: Start MAVProxy and Arm the Drone

```bash
mavproxy.py --master=/dev/ttyUSB0 --baudrate 115200 --aircraft MyCopter
```

In the MAVProxy console:

```bash
arm throttle
```

### Example 2: Take Off and Land

Start MAVProxy:

```bash
mavproxy.py --master=/dev/ttyUSB0 --baudrate 115200 --aircraft MyCopter
```

In the MAVProxy console:

```bash
mode GUIDED
takeoff 10
```

To land the drone:

```bash
mode LAND
```

### Example 3: Navigate to a GPS Coordinate

Start MAVProxy:

```bash
mavproxy.py --master=/dev/ttyUSB0 --baudrate 115200 --aircraft MyCopter
```

In the MAVProxy console:

```bash
mode GUIDED
guided 37.7749 -122.4194 50
```

### Example 4: Load and Start a Mission

Start MAVProxy:

```bash
mavproxy.py --master=/dev/ttyUSB0 --baudrate 115200 --aircraft MyCopter
```

In the MAVProxy console:

```bash
wp load /path/to/mission.txt
mode AUTO
```

## Conclusion

These commands and examples provide a basic understanding of how to use MAVProxy to control your drone. For more advanced usage and detailed command options, refer to the [MAVProxy Documentation](https://github.com/ArduPilot/MAVProxy).

