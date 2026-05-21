# EcloseR — user guide

EcloseR is a browser-based tool for staging Drosophila developmental events from scanned well-plate image series. All processing happens locally in your browser — no data is uploaded anywhere.

# Requirements

A modern browser (Chrome recommended, Firefox works)
A folder of images from your plate scanner (JPEG, PNG, or TIFF), all frames in a single folder
Images should be named sequentially (e.g. scan_001.jpg, scan_002.jpg) so they load in the correct order


# Step 1 — Load your image series
Click Load images in the top bar and select all frames from your scan folder at once. Use Ctrl+A (Windows) or Cmd+A (Mac) to select all files at once. The frames load in alphanumeric order and the first frame appears in the viewer.
The app reads EXIF timestamps from each image in the background — this is what gets recorded when you mark a developmental event.

# Step 2 — Add a plate
In the left panel, type a name for your plate in the Add plate field and click +.

Example: You scanned two plates side by side. Type Plate_1_males and click +, then type Plate_1_females and click + again.

Set the grid dimensions using the rows × cols fields. For a standard 96-well plate leave this at 8 × 12. For a 24-well plate enter 4 × 6.

# Step 3 — Draw the plate region
With your plate selected in the list, click Add plate region in the top bar. The cursor changes and a blue hint appears. Click and drag a rectangle around the physical plate in the image. Release the mouse to confirm.
A grid overlay appears inside the rectangle, dividing it into wells. Each cell is automatically assigned a well ID (A1, A2 … H12).

Tip: If the rectangle is slightly off, just click Add plate region again and redraw — it overwrites the previous one.

Repeat steps 2–3 for each plate in your image.

# Step 4 — Select the phases you want to track
In the right panel under Phases to track, check only the events relevant to your experiment:

H — Hatching (egg to L1)
P — Pupation (larva to pupa)
E — Eclosion (pupa to adult)
D — Death / survival assay

Unchecked phases are hidden from the interface to reduce clutter.

Example: For a pupal duration experiment, check P and E only. For a full lifecycle assay, check all four.


# Step 5 — Select a well
Click any cell in the well grid on the left panel, or click directly on a well in the image viewer. The selected well highlights in both places.
You can also type a well ID (e.g. B7) in the Jump to well box at the bottom of the right panel and press Enter.

# Step 6 — Scrub to the event and mark it
Use the scrubber at the bottom of the image viewer to move through your image series. The current frame number and its EXIF timestamp are shown above the slider.
Keyboard shortcuts:

← / → — step one frame back or forward
h — mark hatching
p — mark pupation start
e — mark eclosion

When you see the event you are looking for, click the corresponding button in the right panel (or use the keyboard shortcut). The timestamp from that frame is recorded instantly and appears in the right panel and the data table.

Example workflow for one well:

Select well A1
Scrub forward until the larva stops moving — click Mark pupation start. The right panel shows Pupation: 2024-06-10 08:42:15
Continue scrubbing until movement resumes — click Mark eclosion. The panel now shows Eclosion: 2024-06-14 11:17:03 and calculates Pupal duration: 98h 34min automatically



# Step 7 — Mark dead individuals
If a well contains a dead animal, select the well and click Mark as dead. The well turns red in the grid and the Survived column in the table is set to No.
For survival assays with the death phase enabled, you can additionally click Mark time of death to record the exact frame timestamp.

# Step 8 — Review and correct
You can go back to any well at any time and adjust your marks. Select the well, scrub to the correct frame, and click the mark button again — or use the ✕ button next to each event to clear it individually. The table updates in real time.

# Step 9 — Export your data
Click the Data table tab at the top of the center panel to see all wells across all plates in one table. From here:

Export CSV — saves a .csv file readable by Excel, R, or Prism
Export Excel — saves a .xlsx file directly
Copy table — copies tab-separated data to your clipboard for pasting into any spreadsheet

The table contains one row per well with columns for plate name, well ID, all recorded timestamps, survival status, and calculated durations.

# Notes

If your scanner does not embed EXIF timestamps, the image filename is used as the timestamp fallback. In that case, name your files with a parseable timestamp (e.g. scan_20240610_084215.jpg) for meaningful duration calculations.
The app has no save function yet — do not close the browser tab mid-session without exporting first.
Clicking a row in the data table jumps back to that well in the image viewer.
