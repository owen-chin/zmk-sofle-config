Flashing Each Half (macOS)

Board: Eyelash Sofle, nice!nano controller, physical reset button on the side of each half.

Per half:


Connect that half to your Mac via USB-C directly (not through the other half).
Press the reset button on the side.

Try a single press first.
If no drive appears, try a quick double-press instead.



Confirm the drive mounted:


bash   ls /Volumes/

Look for something like NICENANO.
4. Copy the firmware file using Terminal (not Finder — Finder frequently throws "can't complete the operation" errors on these drives):

bash   cp ~/Downloads/<firmware-folder>/left.uf2 /Volumes/NICENANO/; sync

(use the matching file for left vs. right half, and adjust the path/volume name as needed)
5. The drive will disconnect on its own once flashing completes — that's the success signal.

About cp errors: If you see something like:

cp: /Volumes/NICENANO/left.uf2: fcopyfile failed: Input/output error
cp: /Volumes/NICENANO/left.uf2: fchmod failed: No such file or directory

this usually means the drive disconnected because the flash already succeeded and the board rebooted — not that anything went wrong. Test the keyboard first before retrying. If it didn't actually flash, press reset again to remount and retry the cp command.

Order: Flash the left half completely (confirm working) before starting the right half. Don't have both connected/flashing at once.
