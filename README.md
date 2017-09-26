# TechnicRobot EV3 Blocks
Some useful programming blocks for LEGO Mindstorms EV3

## Known Issues

1. Some chipset I2C write operation must be ended with an I2C stop condition for working properly. However, there is no explicit way in the high level I2C interface of official EV3 firmware to generate the I2C stop condition after the write bytes. But it can be solved by a tricky method: Explicitly read an extra byte after the write bytes within the same I2C transaction.

1. The data type of I2C buffer in the official EV3 firmware is signed byte, which is only range from -127 to 127. Byte -128 (0x80) is treated as a special value that cannot be used directly in I2C write or read operation. In the case of using TechnicRobot I2C Port programming block, unsigned byte 128 (0x80) cannot be used in I2C write or read operation.
