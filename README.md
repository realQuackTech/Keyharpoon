
# Keyharpoon(USB Based KeyStroke)
<br />
This project is primarily built around the ATmega32 microcontroller and an ESP-based Wi-Fi module, aiming to create an advanced and customizable BadUSB platform. 
<br />
The motivation behind the project is to overcome the limitations of existing similar tools, such as being closed-source, lacking extensibility, or missing modern connectivity options.
<br />

![KeyHarpoon Demo](https://raw.githubusercontent.com/realQuackTech/Keyharpoon/refs/heads/main/images/introduce.gif)
<br />

KeyHarpoon offers a reliable and open-source hardware foundation for cybersecurity professionals, IT personnel, developers, and security researchers, with capabilities such as USB HID injection, Wi-Fi-based control, and potential remote payload delivery. Thanks to its modular structure and clean codebase, this project is highly suitable for further development aimed at automation, red team operations, or learning USB attack vectors. Since the project supports the local language, it poses no compatibility issues in that regard.
<br />

By combining USB and wireless interfaces, this board opens the door to next-generation HID attacks and scripting capabilities, offering an easy-to-set-up and straightforward solution to integrate into your existing toolkit.

<br />


# 🚀 **Features**

-->High capacity

-->Customizable open ports

-->Turkish keyboard layout support

-->Status LED

-->Physically customizable reset button
<br />
# ☕ Support Me

This project is being developed as open source and is continuously being improved to become more stable and secure. If you find the project useful and would like to contribute to its development, you can support it by buying me a coffee! 🙌

[!["Buy Me A Coffee"](https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png)](https://buymeacoffee.com/quacktech)

Your support is a great source of motivation for keeping the project up to date and adding new features. Thank you! 💙

# First Usage

If you have purchased the hardware, all you need to do is connect it via the USB port for initial setup.

**1)** To configure the device, connect from a Wi-Fi-enabled device to the access point (AP) with SSID **KeyHarpoon** and enter the password **keyharpoon**.

**2)** Once connected, simply navigate to **http://192.168.4.1** in any browser. If you receive a warning that the site cannot be verified, please proceed anyway.

**3)** The web interface should now be visible. Be sure to change the default password to ensure better security.

<br />
<br />
### Status LED

If you want to monitor the status of your payload remotely while it's being injected into the target, you can use the onboard RGB status LED.  
Usage is simple — just specify which color should be active at each stage in your payload.

| Command     | Color   | Description         |
|-------------|---------|---------------------|
| `LED r`     | 🔴 Red   | Turns LED red       |
| `LED g`     | 🟢 Green | Turns LED green     |
| `LED b`     | 🔵 Blue  | Turns LED blue      |
| `LED s`     | ⚫ Off   | Turns LED off       |

<br />
<br />
### Physical Button

The device includes a physical password reset button.  
When pressed, the SSID and password will temporarily reset to the default values: **KeyHarpoon** and **keyharpoon**.  
Keep in mind that this reset is **temporary** — once the device is powered off and on again, it will revert to the previous password.  
Therefore, after resetting, you should enter a new password and save it to persistent storage.
<br />
If you do **not** intend to use the physical button, you can disable it via the toggle switch located in the top-right corner of the **Settings** tab on the web interface.
<br />
This feature allows you to quickly reset the device without losing any data, in case you forget your password.  
However, if the button is disabled and you forget the password, you’ll need to reboot the device manually.
<br />
⚠️ This feature is enabled by default.
<br />
<br />
### Bootloader Customization

The onboard **ATmega32U4** microcontroller comes with support for a user-customizable bootloader.  
This can be achieved by accessing the ISP (In-System Programming) pins on the device — specifically, the **MOSI**, **MISO**, **SCK**, and **RESET** lines.
<br />
Through this interface, developers can:
<br />
- Flash their own bootloader,
- Perform firmware updates,
- Define custom startup behaviors tailored to the hardware.
<br />

![ESP8266 Dev Board](https://raw.githubusercontent.com/realQuackTech/Keyharpoon/refs/heads/main/images/hardware.png)

<br />
<br />
### ESP8266 USB Communication

Additionally, the ESP8266 Wi-Fi module included in the project is configured to communicate over USB.  
This allows users to access the ESP module directly via the USB serial port — enabling firmware flashing, debugging, or sending commands over serial.
<br />
Thanks to this configuration, the ESP module can operate independently, enabling **bi-directional control** over both Wi-Fi and USB.
<br />
This architecture offers a flexible development environment, where both the **ATmega32U4** and **ESP8266** modules are fully accessible to the developer.  
You can choose to work with just the microcontroller, just the ESP module, or integrate both for more complex applications.

<br />

With the switch configurations below, you can selectively access a specific module or enable the device for full operation.

<br />
<br />
**ESP(01011101)**

![qt](https://github.com/realQuackTech/Keyharpoon/blob/main/images/sw1.png?raw=true)

<br />
**Default(10101101)**

![qt](https://github.com/realQuackTech/Keyharpoon/blob/main/images/sw2.png?raw=true)

<br />
**Atmega(10101010)**

![qt](https://github.com/realQuackTech/Keyharpoon/blob/main/images/sw3.png?raw=true)


<br />
<br />
### Supported Platforms / Boards

KeyHarpoon works seamlessly on all platforms that support the **USB HID (Human Interface Device)** protocol.  
The device is recognized by the computer as a standard USB keyboard, making it fully compatible with:
<br />
- Windows  
- Linux (Ubuntu, Debian, Arch, etc.)  
- macOS  
- Android (with USB-OTG support)  
- Other USB HID-supported systems  
<br />
On the hardware side, the device features an onboard **ATmega32U4** microcontroller, which allows direct USB keyboard emulation.  
This enables full plug-and-play functionality across modern systems **without requiring any additional drivers**.
<br />
No special software is needed — just plug it in and use it on any supported platform.
<br />
<br />
### 🧩 Driver Setup

#### How to Install the Windows Driver?
<br />
KeyHarpoon requires a custom USB driver to be recognized properly by Windows.  
The driver is included in the `.zip` archive under the `drivers` folder.  
The installation process has been automated to simplify setup.


<br />
<br />
#### Installation Steps:
1. Download and extract the `.zip` archive.  
2. Inside the `drivers` folder, **right-click** on `post_install.bat` and select **"Run as Administrator"**.  
3. This will:
   - Add the `QuackTechLLC.cer` certificate to your system (**Local Machine → Trusted Root Certification Authorities**).
   - Automatically install the driver using `keyharpoon1.inf` and `keyharpoon.cat`.

<br />
<br />
#### Manual Installation (If Needed):

If the automatic installation fails:
<br />
- Double-click `QuackTechLLC.cer` and install it under **Local Machine → Trusted Root Certification Authorities**.
- Right-click on `keyharpoon1.inf` and choose **"Install"**.
<br />
⚠️ If it still doesn’t work, go to **Device Manager**, right-click the device, and select **"Update Driver"**.
<br />
After completing these steps, your device will be recognized and can be used with the **Arduino IDE** and other related tools.
<br />
<br />
#### Using the Board with Arduino IDE

If you plan to use the board within Arduino IDE, follow the setup steps provided here:  
[🔗 KeyHarpoon Arduino Setup Guide](https://github.com/realQuackTech/Keyharpoon/releases/tag/package)  
(You may still need to run the `.bat` file manually.)


<br />
<br />
### 🔒 Security Notice

🔴**WARNING:** This device is designed exclusively for responsible security testing and educational purposes.  
KeyHarpoon was developed to test USB security, identify vulnerabilities, and conduct research within a development environment. Any misuse, unauthorized access, or unethical use is unacceptable and illegal in many countries.
<br />
📌 **Before using this tool, you must obtain explicit permission from the owner of the target system.**  
The developers of this project are **not responsible** for any misuse, damage, or legal consequences resulting from the use of this device.
<br />
<br />
### USAGE

The usage is quite simple and almost identical to similar counterparts. Here are some **q-let** commands:

| Command       | Description                            |
|---------------|----------------------------------------|
| **WINDOW/GUI** | Enter the Start menu (Windows)        |
| **WINDOWS**    | Press Windows key and character       |
| **ESC**        | Close pop-ups or exit full-screen mode|
| **PAGEUP/DOWN**| Scroll up or down the page            |
| **F1 - F12**   | Function keys for specific actions   |
| **ENTER**      | Confirm or submit an action          |
| **PRINTSCREEN**| Capture the screen                    |
| **SPACE**      | Insert a space                        |
| **BACKSPACE**  | Delete the previous character         |
| **LED**        | RGB status LED: (r)ed, (g)reen, (b)lue, (s)top |


<br />

![qt](https://github.com/realQuackTech/Keyharpoon/blob/main/images/enter.png?raw=true)

<br />
<br />
### Note on Timing

Please pay attention to the timing intervals between keypresses. Ensure that there is at least a **400 ms** delay between each line. Otherwise, the keypresses may overlap, potentially locking up the device.
<br />
If you wish to save your payload and set it for automatic execution, you can find your saved files in the **File Operations** section.



![qt](https://github.com/realQuackTech/Keyharpoon/blob/main/images/file.png?raw=true)

<br />
<br />
## Settings Page




![qt](https://github.com/realQuackTech/Keyharpoon/blob/main/images/set.png?raw=true)
<br />
<br />

### 📡 OTA (Over The Air) Update Support

With the OTA (Over The Air) option located in the top-right corner, you can enter your current SSID and password to log in.


![qt](https://github.com/realQuackTech/Keyharpoon/blob/main/images/ota.png?raw=true)
<br />
The KeyHarpoon device has OTA (Over The Air) support through the ESP module. This allows you to easily update your device via a web interface without the need for any additional software.
<br />
You can use the following two sections in the web interface to perform the update:
- **Firmware**: Select and upload your new `.hex` sketch file here to reprogram the ESP module.
<br />
For all these operations, you do not need to connect the device to your computer via USB or boot it. The device can be updated remotely as long as it is connected to a Wi-Fi network.
<br />

<br />
<br />
### 📬 Contact / Support

For any feedback, suggestions, or support requests, feel free to contact us:
- 🌐 **Website**: [https://quacktech.tech](https://quacktech.tech)
- 📧 **Email**: [contact-quacktech@proton.me](mailto:contact-quacktech@proton.me)
- ☕ **Support us**: [https://buymeacoffee.com/quacktech](https://buymeacoffee.com/quacktech)
<br />
If you would like to contribute to our project, you can send a pull request via GitHub or create an issue to report bugs or request features.
<br />
<br />
## Licence

[![GPLv3 License](https://img.shields.io/badge/License-GPL%20v3-yellow.svg)](https://opensource.org/licenses/)


<br />
<br />
### 🎓 Credits

The following open-source libraries and community contributions were used during the development of this project:

📡 **ESP8266-Based Development**
- Wire
- ESP8266WiFi
- FS
- ESP8266mDNS
- ESPAsyncTCP
- ESPAsyncWebServer
- ESPAsyncHTTPUpdateServer
- SPIFFSEditor
- ArduinoJson
<br />
⌨️ **ATmega-Based Development**
- Wire
- Keyboard
- String
- FastLED

Additionally, the open-source contributions and documentation from the Arduino community have laid the foundation for this project.
