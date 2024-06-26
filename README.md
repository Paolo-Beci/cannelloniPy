# CannelloniPy
Python version of the [Cannelloni library](https://github.com/mguentner/cannelloni)

For now implemented only on the receiver side.

## General logic of the library
![Cannelloni library logic](/img/cannelloni.png)

## Installation
Simply copy and paste the `cannellonipy.py` file into your project.

## Cannelloni message format
The message format is the same as the one used in the Cannelloni library:
```txt
# UDP packet format:
# 1 byte - Version
# 1 byte - Operation code
# 1 byte - Sequence number
# 1 byte - Number of CAN frames
# First CAN frame:
# - CAN frame format:
# - 4 bytes - CAN ID
# - 1 byte - Length of hexadecimal data
# - N bytes - Data
# Second CAN frame:
# ...

# -----------------------------------------------------------------------------------------
# | Version | Operation code | Sequence number | Number of CAN frames | CAN frame 1 | ... |
# -----------------------------------------------------------------------------------------
```

## Usage
```python
# Import the library
from cannellonipy import run_cannellonipy, CannelloniHandle

# Create a cannellonipy handle
cannellonipy_handle = CannelloniHandle()

# Run the library
run_cannellonipy(cannellonipy_handle, "0.0.0.0", 1234)

# Get the received data
received_frames = handle.get_received_can_frames()
for frame in received_frames:
    print("Received CAN frame -> CAN ID:", frame.can_id, ", Length:", frame.len, ", Data:", frame.data[:frame.len].hex())
```
An example of usage can be found in the `usageTest.py` file.

## TODO
- :white_square_button: Implement CAN transmit
- :white_square_button: Implement CAN receive
- :white_square_button: Implement tests
