# TBS Robotics Gamepad with Python
TBS Robotics Gamepad with Python
## Prepare
- Laptop computer (MacOS, Linux), or micro computer (Raspberry Pi, JETSON Nano, etc.)
- Gaming controller - PS4
- Either USB or bluetooth connection
- Python 3.x
- Game controller library
## Connect game controller to laptop USB port
- Test if it works with web Java application
- https://gamepad-tester.com/
- Check if you can see the port
```
ls /dev/input/js0
```
- If you want to switch between USB and Bluetooth in Linux, you have to reset controller
- RMRC requirement is wired USB connection to control station laptop
## Install gamepad library
- https://pypi.org/project/pyPS4Controller/
```
sudo pip install pyPS4Controller
```
## Let’s look at default example code
- It uses MyController class from pyPS4Controller
- Instantiate the class with the known game pad I/O port. Please modify the line according the finding
- `controller = MyController(interface="/dev/input/js0", connecting_using_ds4drv=False)`
- `python3 pyDS4_test_v2.py`
## How to convert input to motor control
- Which input data or switch will be most useful
- What is the range of the input values
- RMRC controller conversion example
## How the data is handled
- Add artificial delay - 1 second - between gamepad output update
- Observe output example with extended delay
## Where to convert gamepad input to motor control
- Control station laptop
- Robot controller
## How to extract right data for motor control
- One lazy solution can be pickle
- The ps4controller library itself does not have time information, and it just pushes out queued data
- Pickle enforces only the latest data is picked up for motor control
## Open ended question: Implement a better way!
- How would you modify the class?
- Try other python game pad libraries
- https://github.com/chrippa/ds4drv
- https://www.piborg.org/blog/gamepad-library
- https://github.com/piborg/Gamepad
- https://blog.thea.codes/talking-to-gamepads-without-pygame/

