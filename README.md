# inventor-part-viewer

https://nimageran.github.io/inventor-part-viewer/

# Exporting BOM from Autodesk Inventor  
_For use with the “Inventor Part Scanner” web viewer_

This guide explains how to export a Bill of Materials (BOM) from Autodesk Inventor so it can be loaded into the web viewer.

> **Important:** Inventor’s default export is usually **Excel (.xlsx)**.  
> For the web viewer you should **export as CSV** (or later save the Excel file as CSV).

---

## 1. Start from the correct file

1. Open the **top-level assembly** in Inventor.  
   - File type must be **`.iam`** (not `.ipt`, not drawing).

If you are in a part or drawing, the BOM export options will not be available.

---

## 2. Open the Bill of Materials dialog

1. In the ribbon, go to the **Manage** tab.  
2. Click **Bill of Materials**.  
3. The **Bill of Materials** window opens with tabs like:
   - **Model Data**
   - **Structured (Disabled)**
   - **Parts Only (Disabled)**

---

## 3. Enable the Structured BOM view

Inventor disables some BOM views by default. You must enable one before exporting.

1. Click on the **Structured (Disabled)** tab to activate it.  
2. **Right-click** on the **Structured (Disabled)** tab.  
3. Choose **Enable BOM View**.  
4. The tab name changes to **Structured** (no “Disabled”).  
5. A table appears with columns (Part Number, Quantity, Description, etc.).

(You can enable **Parts Only** the same way if you want that view too.)

---

## 4. Choose the columns you need

For the Part Scanner tool, the most useful fields are:

- **Part Number**
- **Description**
- **Stock Number** (optional)
- (Optional) any other property you want to see later

To show/hide columns:

1. In the BOM table header, right-click a column heading.  
2. Use **Column Chooser / Columns** to add or remove columns.

---

## 5. Export the BOM (XLSX vs CSV)

With the **Structured** tab active:

1. In the BOM dialog toolbar, click **Export** / **Save As**.  
2. The **Save As** window opens.
3. By default, Inventor usually selects **Excel (.xlsx)** as the file type.
4. For the web viewer you have two options:

### Option A – Export directly as CSV (recommended)
- Change **Save as type** to **CSV / Text** (e.g. `Comma Separated Values (*.csv)`).
- Pick a folder and name (e.g. `Machine3505_BOM.csv`).
- Click **Save**.

### Option B – Export as Excel, then convert
- Leave **Save as type** as **Excel (.xlsx)** and save.
- Open the `.xlsx` file in Excel.
- Use **File → Save As** and choose **CSV (Comma delimited)**.
- Save as `Machine3505_BOM.csv`.

The viewer uses **CSV or XML**, so you must end up with a **.csv** (or compatible XML) file.

---

## 6. Using the BOM with the web viewer

1. Open the **Inventor Part Scanner** web page (`index.html` from your repo).  
2. Click **GLB** and load your exported **.glb** assembly model.  
3. Click **BOM (CSV/XML)** and load the **.csv** (or `.xml`) BOM you exported.  
4. Click a part in the 3D view or in the assembly tree:
   - The viewer will show **Part Number**, **Description**, **Stock Number** and other fields taken from the BOM.

---

## 7. Quick troubleshooting

- **Structured/Parts Only say “Disabled”:**  
  → Right-click the tab → **Enable BOM View**.

- **Export button is greyed out:**  
  - Make sure you’re in an **assembly (.iam)**.  
  - Make sure a BOM view (e.g. **Structured**) is **enabled**.

- **Viewer doesn’t show BOM data:**  
  - Confirm the file you loaded is **CSV or XML**.  
  - Check that the BOM has a **Part Number** column and that those part numbers match the part names / numbers in your model.

---

Keep this file in the repo so future-Nima doesn’t have to re-figure Inventor’s export weirdness again.
