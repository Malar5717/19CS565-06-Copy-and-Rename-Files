# EXP 06: COPY AND RENAME FILES
### AIM

The objective is to copy all files from a designated source folder to a destination folder and rename each file by appending a unique timestamp (`yyyyMMddHHmmss`) to its name.

---

### PROCEDURE

The workflow uses built-in .NET functionality exposed through UiPath activities:

1.  **Define Variables:** `sourcePath`, `destinationPath`, and `files` (Array of String) are defined.
2.  **Get Files:** An **Assign** activity uses `Directory.GetFiles(sourcePath)` to retrieve a list of all files in the source folder.
3.  **Loop Files:** A **For Each** loop iterates through the list of files (`files`).
4.  **Rename Logic (Inside Loop):**
    * **Path.GetFileNameWithoutExtension(item)** and **Path.GetExtension(item)** are used to separate the file name from its extension.
    * **DateTime.Now.ToString("yyyyMMddHHmmss")** generates the timestamp.
    * The new path and name are constructed: `destinationPath + "\" + fileName + "_" + timestamp + ext`.
5.  **Copy File:** The **Copy File** activity copies the original file (`item`) to the newly constructed path (`newName`).

---

## OUTPUT

Files are copied form the `srcFiles` folder to the `destFiles` folder attached.

new files: srcFile -> srcFile_20250927233409.txt, srcFile2 -> srcFile2_20250927233409.txt

---

## RESULT

The automation successfully copies multiple files and ensures each copy has a unique file name by appending the timestamp, preventing overwrites in the destination folder.
