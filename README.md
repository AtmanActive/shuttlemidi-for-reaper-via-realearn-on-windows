# ShuttleMIDI for Reaper via ReaLearn on Windows.

ShuttleMIDI sends MIDI events for the [Contour ShuttleXpress](https://contourdesign.com/products/shuttle-xpress) (also known as Contour Multimedia Controller Xpress) to enable usage as a MIDI transport controller with [Reaper DAW](https://reaper.fm) via [ReaLearn](https://www.helgoboss.org/projects/realearn/) on [Windows](https://www.microsoft.com/en-gb/windows).

Pros: 
- portable usage mode: no need to install Contour drivers, works from any path, lightweight.
- MIDI reliability: works even if another window steals focus, can be routed to other machines.

Cons:
- no more per-app ShuttleXpress config switching: this is for Reaper and Reaper only.



ShuttleMIDI doesn't provide it's own MIDI driver for Windows. It relies on the excellent and free [loopMIDI driver from Tobias Erichsen](https://www.tobias-erichsen.de/software/loopmidi.html).

# Installation
1. Install the loopMIDI driver from https://www.tobias-erichsen.de/software/loopmidi.html
2. Add a loopback MIDI port called "ShuttleMIDI" in the loopMIDI control panel
3. Build the application or download the latest release from the ["Releases" section](https://github.com/dg1psi/shuttlemidi/releases).
```
go build -ldflags "-linkmode external -extldflags -static -s -w -H=windowsgui" -a
```
4. Run the "shuttlemidi.exe" file
5. Open SDR Console
6. Configure the MIDI Controller in the Options