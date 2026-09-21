# Setting Up the iDraw Pen Plotter with Inkscape on your own computer

---

## What is this thing anyhow?

The iDraw is a pen plotter: two stepper motors move a pen across paper, following whatever paths you give it. A third motor moved a pen up and down on the paper. You will control this plotter through **Inkscape**, a free, open-source vector editor, through an extension that talks to the plotter over USB. You'll be creating the original images in p5.js using p5.plotSVG, a library that extends the capabilities of p5.js.

_If you are using **the iMacs in Room 325**, everything you need is already installed and setup_. if you want to run this from your own computer you need to set it up for yourself, this includes three pieces of sofware:

1. **Inkscape** — the drawing software. (1.4.4 is the most recent version as of this writing)
2. **CH34x USB driver** — This is what lets your Mac recognize the plotter over USB.
3. **iDraw Inkscape extension** — the panel inside Inkscape that actually drives the plotter.

Windows and Linux mostly skip step 2. If you're on a Mac, you will need to restart your comuter before you use the software, so be sure to save and cleanly close out of any open applciations before you start this process.

---

## 1. Install the most recent version of Inkscape

1. Go to **https://inkscape.org/release/inkscape-1.4.4/** and download the installer for your operating system.
   - **macOS:** click the link for the macOS (Apple Silicon) or macOS (Intel) build, whichever matches your chip. If you're not sure, go under `Apple menu > About This Mac` to see whether you have an Intel or Apple Silicon (M1... M4) chip.
   - **Windows:** download the `.exe` or `.msi`.
   - **Linux:** use your package manager.
2. Run the installer and follow the prompts.
3. Launch Inkscape let it finish its first-run setup, then close it. **Inkscape must have been opened at least once before you install the extension**. Opening it automatically creates the folder the extension goes into.

---

## 2. Install the USB driver (macOS only)

The iDraw uses a **CH340/CH34x** USB-to-serial chip. macOS doesn't know how to talk to it on its own.

### Download

Download the driver ZIP file:

**https://file.wch.cn/download/file?id=178**

Unzip the file you downloaded. Inside you'll find both a `.pkg` and `.dmg` files. 

### Install

Pick the line that matches your Mac:

- **Intel Mac:** install the **`.pkg`** file — double-click it and follow the prompts.
- **Apple Silicon Mac :** open the **`.dmg`** — double-click it, drag the **CH34xVCPDriver** app into your Applications folder. 

Open the **CH34xVCPDriver** app and click the **Install** button. macOS may ask for permission to load a new kernel driver — under **System Preferences › Security & Privacy**, approve it.

Restart your computer.

### Test the driver

1. **Plug the iDraw into your Mac** with the USB cable.
2. Open **System Report** (Apple menu › About This Mac › System Report), go to **Hardware › USB**, and look for a device with **Vendor ID [0x1a86]**. If it's listed, your Mac sees the plotter.
3. Open **Terminal** (Applications › Utilities) and run:

   ```
   ls /dev/cu.*
   ```

   You should see something like `/dev/cu.wchusbserialxxxxx` or `/dev/cu.usbserial-xxxx`. That's your plotter's serial port. If it shows up, the driver is installed correctly.

---

## 3. Install the iDraw Inkscape extension

1. **Download** the extension from **https://drive.google.com/file/d/1nlaEtMm7Qk34WbiUnVxx5apWROZmbo__/view?usp=drive_link**.
2. **Open Inkscape.** Once it has launched, open **Edit › Preferences › System**. Look at the row labelled **User extensions**. Click the **Open** button next to it — that opens your Finder/Explorer directly to the extensions folder.
3. **Unzip the extension archive and copy its contents into that folder.** Copy the *contents*, not the enclosing folder.
4. **Quit Inkscape and reopen it.** The extension won't appear until Inkscape restarts.

Check the **Extensions** in Inkscape. Look for the **iDraw 2.0 Control** entry.

---

## 4. Confirm everything's talking

1. **Power the iDraw on** and make sure it's connected via USB.
2. Open Inkscape and go to **Extensions › iDraw 2.0 Control**.
3. On the **Setup** tab, find the pen up/down toggle. Click **Apply**. The pen should physically rise and lower. If it moves, you're connected — driver, extension, and plotter all work.
4. Set the plotter to **move to home** so prints start centered and uncropped.

Once Apply moves the pen, you're done — the plotter is ready to draw.

---

## Common problems

| Symptom | Fix |
|---|---|
| Mac doesn't recognize the plotter at all | Driver not installed, or wrong build — Apple Silicon needs the signed current version. Re-do step 2, approve under Security & Privacy. |
| Extension missing from the Extensions menu | You copied the folder instead of its contents, or didn't quit/reopen Inkscape. Check step 3. | 
| Plotter works but drawings are skewed/cropped | File › Document Properties must match the plotter's work area (A4, 210×297 mm), and the design must sit inside the page boundaries. |
| Inkscape freezes or crashes doing long prints | Close unused apps; Edit › Preferences › Input/Output, slow down or disable autosave; simplify paths (Path › Simplify). **Never close Inkscape mid-print** — stop the plotter first with its pause/off, then quit. |

---

## Notes

- Adapted from Lynn Vegh, "Using the iDraw with Inkscape," Guide. Experimental Methods and Media Lab, Trent University, Peterborough, Ontario. May 2025. https://emmlab.info/Resources_page/Using_the_IDraw_with_Inkscape_How-to_Guide.pdf