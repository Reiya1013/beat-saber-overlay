# (improved) Beat Saber Overlay

This is an improved version of Reselim's [Beat Saber Overlay](https://github.com/Reselim/beat-saber-overlay) with various display options.

Overlay the score information when distributing or recording Beat Saber via OBS.

![preview](https://rynan4818.github.io/beatsaber-overlay-bsr-image.png)

- The image shows a sample of the full option using HttpStatusExtention.

## Installation (OBS)

1. Please install the following mods to send the beat saver data to the overlay.
   - [Beat Saber HTTP Status](https://github.com/opl-/beatsaber-http-status) ※Original version of ModAssistant registration

   There is also a performance-improved version produced by denpadokei.
   - [Beat Saber HTTP Status](https://github.com/denpadokei/beatsaber-http-status)

   To use the optional `pp` feature and the custom difficulty display, you will also need to install denpadokei's version of HTTP Status and the following mods.
	 - [HttpStatusExtention](https://github.com/denpadokei/HttpStatusExtention)

   ※Both versions of HTTP Status require you to install `websocket-sharp` in ModAssistant. Please note that it is often forgotten to install.

2. Download the latest release from the [release page](https://github.com/rynan4818/beat-saber-overlay/releases).

3. Extract the zip to an appropriate folder. (Example: C:\TOOL\beat-saber-overlay)

4. Create a Browser source

![image](https://rynan4818.github.io/beatsaber-overlay-obs-setting1_en.png)

5. Add the Browser to Sources

![image](https://rynan4818.github.io/beatsaber-overlay-obs-setting2_en.png)

6. In Create new, enter an appropriate name and press OK.

![image](https://rynan4818.github.io/beatsaber-overlay-obs-setting3_en.png)

7. Double-click index.html in the unzipped zip file or open it with Chrome or Edge browser.

![image](https://rynan4818.github.io/beatsaber-overlay-obs-setting4_en.png)

8. Copy the address(URL) field of your browser.

![image](https://rynan4818.github.io/beatsaber-overlay-obs-setting5_en.png)

9. Paste the copied address into the OBS URL field.

   If it is a `Local file`, you cannot set options, so you need to enter it in URL notation like this.

   Set the size equal to your canvas size (1280x720, etc.)

   (Optional) For 1080p canvases, add the `scale` modifier (ex. `file:///C:/TOOL/beat-saber-overlay/index.html?modifiers=scale`) to scale the overlay by 1.5x

![image](https://rynan4818.github.io/beatsaber-overlay-obs-setting6_en.png)

10. Add modifiers options as needed. Separate multiple options with a comma (,).

![image](https://rynan4818.github.io/beatsaber-overlay-obs-setting7_en.png)

11. If you reduce the width to less than the canvas size, the overflow text will scroll.


## Options

Options are added to the URL query as such:

```
file:///C:/TOOL/beat-saber-overlay/index.html?modifiers=top,all
```

### `modifiers`

Multiple modifiers can be seperated with commas.

- `top`
	* Moves the overlay to the top and reverses the layout vertically
- `rtl`
	* Moves the overlay to the right and uses right-to-left text
- `scale`
	* Scales the overlay by 1.5x, for use on 1080p canvases
- `test`
	* Makes the background black, for testing purposes
- `bsr`
	* Show beatsaver's map key
- `miss`
	* Show the number of misses
- `mod`
	* Show Modifier (ex. DA,FS,NA,etc...)
- `energy`
	* Show energy bar
- `pp`
	* Shows pp points with 100% accuracy, Star Difficulty, and real-time pp points for ranked map.（※1）
- `all`
	* `bsr`, `miss`, `mod`, `energy`, `pp` Show all options.（※1）
- `no-performance`
	* Hide score display
- `no-hidden`
	* Don't hide the overlay when the map ends

※1：To use the `pp` option, you need to install [HttpStatusExtention](https://github.com/denpadokei/HttpStatusExtention).

### `ip` and `port`

Listen to events from another IP and/or port.
```
file:///C:/TOOL/beat-saber-overlay/index.html?ip=192.168.1.10&port=6557&modifiers=top,bsr
```