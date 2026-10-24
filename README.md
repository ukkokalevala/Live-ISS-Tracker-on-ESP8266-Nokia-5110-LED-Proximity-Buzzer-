Track the International Space Station live on a Nokia 5110 screen — with an LED that brightens as the ISS gets closer, and a buzzer that alerts you when it's nearby. Built on an ESP8266 (Wemos D1 Mini). No soldering required.

In this tutorial we wire up the display using hardware SPI (the fix that stops the blank-screen problem most people hit), pull live position data from the N2YO API, calculate the distance from your own coordinates, and map that distance to PWM brightness on an LED. Full code walkthrough, wiring diagram, and tuning tips included.

CHAPTERS
0:00 Intro
0:30 What you'll need
1:15 Wiring
2:30 Getting your API key
3:00 The secrets.h tab
3:45 Code walkthrough
5:15 Upload and first run
5:50 Tuning
6:20 Outro

PARTS USED
• ESP8266 board (Wemos D1 Mini)
• Nokia 5110 LCD module (PCD8544)
• 1x LED + 220Ω resistor
• 1x active buzzer (3.3V)
• Breadboard + jumper wires
• Micro-USB cable

WIRING SUMMARY
Display → ESP8266
  CLK  → D5  (GPIO14, hardware SPI — fixed)
  DIN  → D7  (GPIO13, hardware SPI — fixed)
  DC   → D6  (GPIO12)
  CE   → D1  (GPIO5)
  RST  → D2  (GPIO4)
  VCC  → 3.3V
  GND  → GND

LED    → D8 (GPIO15) via 220Ω resistor to GND
Buzzer → D0 (GPIO16), negative leg to GND

IMPORTANT NOTES
• The display runs on 3.3V — not 5V.
• Use the 3-argument display constructor (DC, CE, RST). The 5-argument version with CLK/DIN gives a blank screen on newer ESP8266 cores.
• Never upload secrets.h with your real WiFi credentials to GitHub. Share a blank version instead.
• Free N2YO API key: https://www.n2yo.com

API KEY & COORDINATES
Sign up at n2yo.com for a free API key. Put it in the sketch, and set your own latitude/longitude so the distance is calculated from your location.

TUNING
• FADE_MAX_KM — lower this if the LED is on too often (try 2500 instead of 5000)
• FADE_MIN_KM — distance at which the LED is fully bright (default 400 km)
• CLOSE_KM — the distance that triggers the buzzer (default 1000 km)

Built it? Drop a message in the comments — I'd like to hear how it went. And if you want to take it further, the same pattern works for any satellite: just swap the NORAD ID.

