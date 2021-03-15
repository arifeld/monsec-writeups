**Name:** Indiana Jones and the Tomb of the Lost Headers

**Type:** Forensics

**Difficulty:** Easy

### Challenge Notes:
>Somebody robbed this file of it's header and now i don't know what it is, only you can help!

>Note: Flag NOT in standard format. Wrap answer with MONSEC{}

### File(s) Attached:
[the_TOMB]

### Solution:
The attached file is missing a header (first few bytes of the hex dictating the type of file), making Windows unable to open the file.

We have to find the type of file and add the header ourselves.

Two ways of determining the file type:

**1)** Inspecting the hex - there are multiple references to `source/flag.png`. The `source/` tells us there is a folder inside the file, implying it is a compressed folder.

**2)** Using in-built Linux command `file`. Running `file the_TOMB` automatically determines the type of file (even without the header) - which returns that the file is a zip folder.

Finally, use [this page](https://digital-forensics.sans.org/media/hex_file_and_regex_cheat_sheet.pdf) to find the correct header for a .zip file and add it to the hex of the file. Finally, rename the file to the_TOMB.zip and extract.
