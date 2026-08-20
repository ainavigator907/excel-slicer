# Excel Slicer — split a workbook by column

*[日本語版はこちら / Japanese version](README.md)*

A Windows tool that takes one Excel file and splits it into separate files, one per distinct value in a column you choose (region, owner, department, and so on).

The workbook is displayed inside the tool exactly as it looks in Excel, so you set everything up by **clicking column headers and row numbers**. No formulas, no macros.

<br>

## Download

**▶ [Get the latest release](../../releases/latest)**

Two builds are available. They are the same tool.

| | File | Notes |
|---|---|---|
| **Standalone exe** | `ExcelSlicer_v4.exe` | No installation. Download and double-click. Starts in about 2–3 seconds |
| **Installer** | `ExcelSlicer_v4_setup.exe` | Installed build. **Starts in about 1 second.** Choose this if startup time matters |

The standalone exe unpacks itself into a temporary folder every time it launches, which costs a few seconds. The installed build skips that step.

- Supported OS: Windows 10 / 11 (64-bit)
- Works on machines that do not have Excel installed
- The installer does **not** require administrator rights
- Saved split presets and settings are shared between both builds

> **About the warning on first launch**
> This is an unsigned tool written by an individual, so Windows may show a blue
> “Windows protected your PC” screen the first time you run it.
> Click **More info** → **Run anyway**.

<br>

## What it does

| Feature | Description |
|---|---|
| Split by column value | Splits the workbook into one file per distinct value in the column you pick |
| Keeps formatting and formulas | Cell colours, borders and formulas are preserved in the output |
| Point-and-click setup | Pick columns and rows on a grid that looks like Excel |
| Per-sheet settings | Each sheet in the workbook can have its own split settings |
| Saved presets | Name a set of settings and recall it from a dropdown next time |
| Japanese / English | Switch the interface language from the **language** button at the top right (no restart) |
| Output filename pattern | Choose from 3 naming patterns (defaults to the original layout) |

<br>

## Basic usage

1. Double-click `ExcelSlicer_v4.exe` (or the installed Excel Slicer) to start it
2. **Drag & drop** an Excel file onto the area at the top, or click inside the dashed box to pick one
3. The sheet appears in the tool, laid out the way Excel shows it
4. Use the **mode buttons** in the middle to choose what you are setting, then click column headers (A, B, C…) or row numbers on the grid
5. Tick what you want to export under **Choose the data to export**
6. Set an output folder with **Change...**, then press **Split and save**

<br>

## The four mode buttons

### Split key column
Click a column header to make that column the basis for splitting (shown in green). Click again to clear it.
Normally you pick a single column. You can pick up to 5, but only for the unusual case of several tables sitting side by side on one sheet.

### Delete columns
Click a column header to remove that column from the output files (shown in red with a strikethrough). You can pick separate, non-adjacent columns.
**Right-click** a header to also get *Delete this column and everything after it*, which is handy for trimming unused columns off the end.

### Data start row
Click a row number to mark it as the first row of data (the row number turns blue).
Everything above it is treated as headings and is kept, unsplit, in every output file. Click again to go back to auto-detection. If you set nothing, the tool works it out automatically.

### Excluded rows
Click a row number to exclude that row from splitting (shown in yellow).
Excluded rows ignore the filter and stay as-is in every output file — useful for note rows below a table, or any row that must always be kept.
Values in excluded rows also disappear from the *Choose the data to export* list.

> Everything above is also available from the right-click menu.

<br>

## Sheet tabs

Every sheet in the workbook appears as a tab just below the grid.
Click a tab to switch to that sheet; **each sheet keeps its own settings**.

Picking a split key column automatically marks that sheet for export and puts a “✓” on its tab. The *Include this sheet in the split* checkbox on the right does the same thing.

Note: sheets that are not marked for export are removed from the split output files.

<br>

## Saved presets

Press **Save preset** to name and store a set of settings.
Next time, pick it from the *Split preset* dropdown to restore it. Presets saved by older versions still load.

<br>

## Output filename pattern

The **Filename:** dropdown lets you choose how the output files are named.

| Pattern | Example (split key "Tokyo", source file "sales.xlsx") |
|---|---|
| 【key】filename (default) | `【Tokyo】sales.xlsx` |
| filename_key | `sales_Tokyo.xlsx` |
| filename（key） | `sales（Tokyo）.xlsx` |

The default matches the original naming, so files come out named the same way as before unless you change it.

<br>

## Interface language

The **language** button at the top right switches between **日本語** and **English** (it's a button rather than an always-open dropdown, since most people leave it on Japanese). The change applies immediately — no restart needed — and is remembered next time you start the tool.
On first launch the language is chosen to match your Windows display language.

<br>

## FAQ

**Q. What do the split files look like?**
A. Data rows that do not match the split key are removed, and the file is saved scrolled to cell A1. Rows containing “Total”, “Subtotal”, “合計” or “小計”, and any rows you marked as excluded, are kept. Formatting and formulas carry over.

**Q. I deleted a column from the middle of the table and the formulas broke.**
A. Deleting a column anywhere other than the end can break formulas that referenced it, and merged cells that span the deletion point. The tool warns you on screen when you do this — always check the exported files. Trimming columns off the end (right-click → *Delete this column and everything after it*) does not have this problem.

**Q. Only some rows show up for a large sheet.**
A. The preview shows the first 5000 rows, but **splitting processes every row** in the sheet.

<br>

## Disclaimer

The author accepts no liability for any direct or indirect damage arising from use of this tool.
**Always back up your files before using it.**

This tool was written by an individual for their own work and is published as-is. Individual support and guarantees of correct operation are not provided.
