# Akiko-no-Hikari (晶子の光)

## Driver Code Overview
This code represents the driver component of the Akiko-no-Hikari project. It handles the low-level LED control and light effect simulation, while the core project functionality is implemented elsewhere.

## Driver Functionality
- Controls WS2812 LED strip using PIO (Programmable Input/Output)
- Implements Gaussian light distribution algorithms
- Manages day/night cycle transitions and color temperature changes
- Provides the interface between the main project logic and physical LED hardware

## How It Works
- Uses Gaussian functions to simulate natural light distribution
- Controls light position and diffusion range by adjusting Gaussian parameters (mean μ, standard deviation σ)
- Dynamically adjusts RGB color values to simulate different times of day and color temperature changes

## Hardware Specifications
- Controller: Raspberry Pi Pico (RP2040)
- LED Type: WS2812 programmable RGB LEDs
- LED Count: 48 units
- Data Pin: GPIO 22
- Communication: PIO (Programmable Input/Output) state machine
- Clock Frequency: 8MHz

## Integration Notes
This driver code should be integrated with the main Akiko-no-Hikari project. It provides the necessary functions to control the LED hardware but requires the core project components to determine when and how lighting effects should be triggered.

## Usage
When integrated with the main project, upload the complete code to a Raspberry Pi Pico, connect the WS2812 LED strip to GPIO pin 22, and the system will respond to the main project's control signals.