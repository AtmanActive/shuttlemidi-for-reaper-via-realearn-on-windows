# ShuttleMIDI for Reaper via ReaLearn on Windows.

ShuttleMIDI sends MIDI events for the [Contour ShuttleXpress](https://contourdesign.com/products/shuttle-xpress) (also known as Contour Multimedia Controller Xpress) to enable usage as a MIDI transport controller with [Reaper DAW](https://reaper.fm) via [ReaLearn](https://www.helgoboss.org/projects/realearn/) on [Windows](https://www.microsoft.com/en-gb/windows).

Pros: 
- portable usage mode: no need to install Contour drivers, works from any path, lightweight.
- MIDI reliability: works even if another window steals focus, works even if Reaper is minimized, can be routed to other machines.

Cons:
- no more per-app ShuttleXpress config switching: this is for Reaper and Reaper only.


# Map


![ShuttleMIDI for Reaper via ReaLearn on Windows](https://raw.githubusercontent.com/AtmanActive/shuttlemidi-for-reaper-via-realearn-on-windows/main/ShuttleMIDI-for-Reaper-via-ReaLearn-on-Windows.png)

The assignment of commands can be easily altered once it is installed.


# Preparation

ShuttleMIDI is an exe program pushing MIDI events onto a MIDI input port. Therefore, you will need a virtual MIDI cable to forward these MIDI events onto a MIDI output port so Reaper can pick them up.

- Free option is to use the excellent [loopMIDI driver from Tobias Erichsen](https://www.tobias-erichsen.de/software/loopmidi.html).

- Another free (open-source) option is to use [Springbeats Virtual MIDI Cable Driver](https://springbeats.com/sbvmidi/)

- Pro option is to use [Bome Network](https://www.bome.com/products/bomenet) which is a comprehensive MIDI routing / virtualization / networking software.

# Installation
1. Install the Virtual MIDI Cable (one of the three options mentioned above).
2. Create a new Virtual MIDI Cable, name it "ShuttleMIDI" or similar. If using Bome Network, make sure to route the cable's input to cable's output to create the actual loopback.
3. Download ShuttleMIDI.zip from [Releases](https://github.com/AtmanActive/shuttlemidi-for-reaper-via-realearn-on-windows/releases) and unzip it anywhere you want. It is a portable app and will work from anywhere.
4. Run shuttlemidi.exe once and choose the appropriate MIDI device (the Virtual MIDI Cable you created above) by left clicking on shuttlemidi.exe's icon in the system tray. It will save the changes and exit. Now you can run it again. Later on you can add it to your auto-run manager if you like.
5. Download Reaper.zip from [Releases](https://github.com/AtmanActive/shuttlemidi-for-reaper-via-realearn-on-windows/releases) and unzip it in the folder next to your Reaper instalation, portable or otherwise. The ZIP file contains the folder "Reaper" so it will merge with your reaper installation, adding the scripts under \Reaper\Scripts\AtmanActive Scripts\Jog scroll view horizontaly\.
6. Now start your Reaper and go to main menu "Actions" -> "Show action list...". In the new window that just opened called "Actions", click on the button "New action..." and then on "Load reascript...". Now navigate to your Reaper installation folder and then to subfolders Scripts\AtmanActive Scripts\Jog scroll view horizontaly\ and choose all of the files there. This will import 16 new scripts/actions into your Reaper. They are all prefixed "aa_" so you can easily find them manually if you want. Now you can close all the existing windows in Reaper.
7. Install [ReaLearn](https://www.helgoboss.org/projects/realearn/) (if you don't already have it).
8. Now, start your Reaper (if it is not already running) and to to main menu "Options" -> "Preferences...". In the new window that just opened called "Reaper Preferences" find "MIDI Devices" and in the MIDI inputs table, find the new Virtual MIDI Cable you installed in the previous steps, right click on it and choose "Enable input for track record input" and "Enable input for control messages". Click OK to close that window.
9. Now, start your Reaper (if it is not already running) and go to main menu "View" -> "Monitoring FX". In the new window that just opened called "FX: Monitoring", click on the button "Add" and add a new ReaLearn FX instance (VSTi: ReaLearn (Helgoboss). In the "Input" dropdown on the ReaLearn instance window, choose the Virtual MIDI Cable you created in the previous steps.
10. Download ReaLearn.zip from [Releases](https://github.com/AtmanActive/shuttlemidi-for-reaper-via-realearn-on-windows/releases) and unzip it to some temp folder. Inside, open the file "ShuttleXpress with ShuttleMIDI ReaLearn for Reaper MainCompartment.json" in a text editor and copy everything to copy buffer (CTRL+A + CTRL+C). Now, back to Reaper and ReaLearn instance window, click on the button "Import from clipboard".
11. Done. Start controlling your Reaper using your ShuttleXpress.




# Building from source
```
go build -ldflags "-linkmode external -extldflags -static -s -w -H=windowsgui" -a
```

