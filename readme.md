# audioshare
The bash script hosted in this repo allows you to easily share audio
from applications on Linux (Ubuntu-like distros). We do this by routing the audio from your output
device into your input device (but only the audio from certain applications).
This means you can still use your microphone to speak while you are sharing audio,
and only the audio from the applications you want to share will be shared.

The code for this is taken from https://superuser.com/a/1621244/1686543
and has been adapted by me into a bash script for convenient use.

## Installation
1. `git clone` repository
2. `cd audioshare`
3. `chmod +x audioshare`
4. Move the `audioshare` executable to a directory in your path

## Usage
1. Find the name of your input device: `pactl list sources`
2. Find the name of your output device: `pactl list sinks`
3. Next, call the script with your input and audio device:
`audioshare <input-device> <output-device>`.
For example, for me, `<input-device>` is
`alsa_input.usb-Blue_Microphones_Yeti_Stereo_Microphone_FST_2018_06_08_04155-00.analog-stereo`,
and `<output-device>` is
`alsa_output.pci-0000_00_1f.3.analog-stereo`.
For you, they will be different.
4. Now, use something like `pulsemixer` to set your input device to
`Transmit + Signal`.
5. Then, use something like `pavucontrol` to send playback from the application
you want to share to `Signals to transmit`.
6. Done!

Once you have your device names, you can write a wrapper script/command
so you don't have to pass the device names every time.

To undo everything, do `audioshare reset`
