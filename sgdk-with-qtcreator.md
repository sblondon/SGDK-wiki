# SGDK with QtCreator

1. Download Qt from [`www.qt.io/download-open-source/`](//www.qt.io/download-open-source/)  
2. Install QtCreator. The QtCreator checkbox is mandatory; you do not need any of the optional Qt components the installer suggests.
3. First, open the project, by selecting **File › New File or Project...**, then **Import Project › Import Existing Project › Choose...**.
4. Choose a directory to keep your source code in (create one if you haven't already done so), and give the project a name for QtCreator to call it. Click **Next**.
5. QtCreator will show a list of all the files currently in your project. (If you haven't yet added any files, none will be shown.) Click **Next**.
6. QtCreator will show a summary of the files that will be added. Click **Finish**.
6. You can add new source code to the project by right-clicking on the project root and choosing **Add new...** or **Add Existing Files...** If creating a new file, note that QtCreator has no C-specific templates, but the C++ source/header file templates are suitable for C code as well.
7. To tell QtCreator where the SGDK headers are, add a line to the `.includes` file that was automatically created with your SGDK directory (with forward slashes for path separators).
8. Choose the **Projects** tab on the left. Expand the Build Environment section by pressing **Details ▼** button.
9. On the right, click **Add**. Set the name of the new variable to `GDK`, and its value to the location where you extracted the SGDK to (with forward slashes).
10. Change the **Build Steps** and **Clean Steps**: Set the executable to `%GDK%/bin/make.exe`, and the arguments to `-f %GDK%/makefile.gen`. For the Build Steps, untick all the targets; for the Clean Steps, leave `Clean` ticked.
11. Build the project by pressing the hammer in the bottom-left. It should build successfully and create `out/rom.bin` in your project root.