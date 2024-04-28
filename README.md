# Voice-Controlled-LCD-Display
This project appears to be a simple wireless notice board using Arduino, a LiquidCrystal display, and SoftwareSerial communication. Let's break down the components and functionality:

1. **LiquidCrystal Display (LCD)**:
   - The project utilizes the LiquidCrystal library to interface with a standard character LCD display (16x2 configuration).
   - Pins 4, 5, 6, 7, 8, and 9 of the Arduino board are connected to the corresponding pins on the LCD module.

2. **SoftwareSerial**:
   - SoftwareSerial is a library that enables serial communication on digital pins other than the hardware serial port (usually pins 0 and 1, labeled RX and TX).
   - In this project, pins 2 and 3 are used for SoftwareSerial communication.

3. **Setup**:
   - The `setup()` function initializes various components and settings:
     - It initializes the LCD with 16 columns and 2 rows.
     - It begins communication with the SoftwareSerial at a baud rate of 9600.
     - It initializes the Serial communication for debugging purposes.
     - It displays a welcome message on the LCD ("Wireless Notice Board").

4. **Loop**:
   - The `loop()` function continuously runs the main program logic:
     - It reads data from the SoftwareSerial port.
     - It trims any leading/trailing whitespace from the received data.
     - It prints the received data to the Serial monitor for debugging.
     - If the received data is different from the previous value (`oldval`), it updates the display content (`newval`).
     - It clears the LCD display and prints the updated content (`newval`) starting from position `i` on the first row.
     - It increments the `i` counter to scroll the message horizontally on the LCD.
     - If `i` exceeds 15 (the maximum column index), it resets `i` to 0 to restart the scrolling.
     - Finally, it updates the `oldval` with the current `val` to track changes in the received data.

5. **Functionality**:
   - The system continuously receives messages through the SoftwareSerial port and displays them on the LCD.
   - If a new message is received, it replaces the previous message and scrolls it horizontally on the display to ensure visibility.

Overall, this project serves as a basic wireless notice board that can display messages sent over a serial connection. It can be expanded with additional features such as message prioritization, wireless communication protocols (like Bluetooth or Wi-Fi), or user interaction for message selection or editing.
