# Video 3DSP Renderer

DirectShow stereo video renderer, uses Bluetooth 3DSP protocol to control active shutter 3D glasses. Allows you to connect compatible 3D glasses to a PC with almost any display, with the only requirement being support for the necessary refresh rate.

## Features and Characteristics

- The DirectShow renderer format allows connection to various video sources;
- Supported stereo pair formats: horizontal, vertical, interlaced, anaglyph, and a test pattern for synchronization tuning;
- Video output modes: D3D9, D3D9 Overlay, D2D DX11;
- Ability to adjust shutter timings to achieve maximal synchronization and image quality;
- Supports USB and Serial HCI Bluetooth adapters;
- Minimum frame rate is 50 Hz according to the 3DSP specification, though lower values are possible if supported by the glasses;
- Maximum frame rate is practically unlimited (1000+ Hz);
- Requires a Bluetooth adapter that supports Connectionless Slave Broadcast - Master and Synchronization Train features. A compatibility test for the adapter is available.

Functionality has been tested with SSG-5100GB glasses. These glasses support a minimum stereo pair period of 32767 μs (no less than 61 Hz). The maximum frequency is unlimited.

## Installation

- Optionally - copy vid3dsp32.dll to Windows\SysWOW64 and vid3dsp64.dll to Windows\System32;
- Register the DLLs: regsvr32 vid3dsp32.dll or regsvr32 vid3dsp64.dll.

## Adapter connection

To work with a USB Bluetooth adapter, direct access is required. You have to change the standard driver to WinUSB driver by installing bth_wu.inf via the Device Manager. Note that the adapter will no longer be available for other OS functions. Revert to the previous driver to restore standard functionality.
Installing this driver may require disabling driver signature enforcement. After installation, the driver should work in normal mode.
Note: Very few adapters support the Connectionless Slave Broadcast feature, regardless of the Bluetooth version. As a recommended alternative, the use of an ESP32 Bluetooth serial HCI adapter is suggested.
[ESP32 Bluetooth serial HCI adapter](https://github.com/Mutabor-gh/esp32-bluetooth-serial-hci)

## Usage
Use the graphedt or GraphStudio program. Add your desired video source and the Video 3DSP Renderer. Open the Renderer's properties for configuration.
![Example graph](/images/graph.png)
Select your desired Bluetooth adapter and ensure if it is working and matches the requirements.
Select the video format and adjust the shutter timings (Phase shift and Open time) until you achieve the clearest and most comfortable image. You can use the test pattern (Stereo pair -> test).

The final result depends on your display's characteristics. For a comfortable viewing experience, a display with a low pixel response time and a refresh rate of at least 120 Hz is recommended.

The project source code will be made available once it is ready for publication.
