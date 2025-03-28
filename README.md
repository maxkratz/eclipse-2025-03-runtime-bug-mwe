# Eclipse Modeling 2025-03 R runtime bug on Windows (MWE)

This repository holds a Minimal Working Example (MWE) to demonstrate a bug in **Eclipse Modeling 2025-03 R** on **Windows**-based systems.

The bug does not occur on Linux, macOS, or older versions of Eclipse (e.g., 2024-12 R).

## Description

Normally, you can create a plug-in project in your development workspace and let it export some Java packages.
The import and export of such projects are managed via the `MANIFEST.MF` file(s).
On your runtime workspace, you can have other projects that have the projects of the development workspace as a dependency defined in their `MANIFEST.MF`.
Eclipse should normally resolve the dependencies automatically and compile the project(s) within the runtime workspace correctly.

However, since updating to Eclipse Modeling 2025-03 R this seems to be broken on Windows-based systems only.

## Steps to reproduce the bug

1. Clone this repository to your machine.
2. Download the latest Eclipse Modeling 2025-03 R package for Windows, e.g., from [this page](https://www.eclipse.org/downloads/packages/release/2025-03/r/eclipse-modeling-tools).
3. Extract the archive and start Eclipse 2025-03 R.
4. Create a new workspace and import the project `org.example.dev.project` via *File* -> *Import...* -> *Existing Projects into Workspace* -> click on the button "Next >" -> select the dev project only -> click on "Finish".
    - Ensure the dev project was built properly and there are no errors within your development workspace.
5. Start a runtime workspace by right clicking on the project `org.example.dev.project` -> `Run As` -> `Eclipse Application`.
6. Within the runtime workspace, import the project `org.example.runtime.project`.
7. Eclipse is now unable to find the correct classes despite the dependency definition in the `MANIFEST.MF` file in `org.example.runtime.project`.
    - When checking *Help* -> *About Eclipse IDE* -> *Installation Details* -> *Plug-ins*, the plug-in `org.example.dev.project` is listed.

## License

This project is licensed under the GNU General Public License v3.0 - see the [LICENSE](LICENSE) file for more details.
