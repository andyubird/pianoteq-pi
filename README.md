# pianoteq-pi

> Install Pianoteq and tweak your system on Raspberry Pi in one line ⚡️

[Pianoteq](https://pianoteq.com/) is probably the only top-notch virtual piano in the world that can be installed on Raspberry Pi.  
And `pianoteq-pi` might be the fastest way to install Pianoteq onto your Raspberry Pi.

> This is an early version, only tested on Raspberry Pi 5 + Raspberry Pi OS 64-bit + Pianoteq 9 Stage & Standard edition. Use at your own risk.

## How to use

1. Install [Raspberry Pi OS (64 bit)](https://downloads.raspberrypi.org/raspios_arm64/images/) on your Raspberry Pi.
2. Download Pianoteq for Linux from [the official website](https://pianoteq.com/), and put the **Linux `.tar.xz` package** you got onto your Raspberry Pi.  
   - Or download it directly on your Raspberry Pi.
3. Run the following command in the same folder as the Pianoteq `.tar.xz` package:

   ```shell
   wget -qO setup.py https://raw.githubusercontent.com/andyubird/pianoteq-pi/refs/heads/main/setup.py && sudo python3 setup.py
   ```

   Simple as that.

![](https://raw.githubusercontent.com/andyubird/pianoteq-pi/main/recording.gif)

After installing in this way, Pianoteq will run headlessly (no GUI, for better performance) on every system boot.  
If you want to adjust something, just double-click the desktop icon to open the GUI.

## What this script actually does?

1. Installs dependencies:
   - `cpufrequtils` – to improve CPU performance while running Pianoteq
2. Extracts the Pianoteq **`.tar.xz`** package to `/home/pi/`
3. Creates a `start.sh` script under the Pianoteq folder, and it:
   - sets CPUs to “performance” mode while running Pianoteq
   - runs Pianoteq as a GUI program or headlessly for better performance
   - sets CPUs back to “ondemand” mode when Pianoteq quits
4. Creates a desktop entry for Pianoteq, so you can open it easily by clicking the icon
5. Creates a system service to run Pianoteq headlessly every time the system starts up
6. Sets a default resolution so that you can run Pianoteq without connecting a display
7. Optionally overclocks the CPU (you can choose between several presets or restore stock settings) to get better performance
8. Disables `smsc95xx.turbo_mode` as Pianoteq officially advises
9. Modifies the “account limits” as Pianoteq officially advises
10. Checks if you have already installed Pianoteq and can re-install or uninstall it if you want

## FAQ

1. `Q` Why use the 64-bit version of Raspberry Pi OS instead of the 32-bit version, or Ubuntu Mate (64 bit)?  
   `A` 64-bit allows for better performance, and Raspberry Pi OS comes with VNC Server, which saves a lot of work.

2. `Q` Is Pianoteq playable on it?  
   `A` Sure it is. With sensible settings (reduced internal sample rate, multicore enabled, etc.) it is responsive and free of crackles or dropouts on a properly tuned Pi 4.

3. `Q` Can I try this on other machines / OS versions?  
   `A` Not recommended. It is primarily designed and tested for Raspberry Pi OS 64-bit on Raspberry Pi boards.
