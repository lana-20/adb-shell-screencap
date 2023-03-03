# <img src="https://user-images.githubusercontent.com/70295997/222840327-da175a0f-ca1d-4a5c-bd4f-efced358e770.png" width=40> I want to capture a screenshot. How can I do it with an adb command?

Frequently, I need to capture a screenshot of the AUT on a mobile device to support my bug ticket. I use the <code>screencap</code> command in the following format:

		% adb shell screencap /sdcard/image_name.png

For example:

		% adb pull /sdcard/image_name.png ~/Documents
		/sdcard/image_name.png: 1 file pulled, 0 skipped 13.5 MB/s(177438 bytes in 0.013s)


Not every Android device supports the JPEG format, some Samsung devices do. The official image file extension on Android is .png. The output will tell you about failure, but won’t return any info about success. That’s normal.

First I take a screenshot, then I exit the <code>shell</code> and copy the file to my computer.

There is a shortcut to execute <code>screencap</code> and file retrieval in one single command, which works on macOS and Windows:

		adb exec-out screencap -p > ~/Documents/image_name.png

The <code>-p</code> flag forces the file to be generated in the PNG format. This option is recommended on macOS, because it’s common when the file gets saved with the .png extension, but cannot be opened as a PNG file. On Windows, the <code>-p</code> option may not be required.

The following shortcut only works on macOS:

		adb shell screencap -p > ~/Documents/image_name.png

Unfortunately, there is no equivalent trick for the <code>screenrecord</code> command.
