# Metamaterial mechanisms editor

<img src="https://hpi.de/fileadmin/_processed_/csm_WEB_door_frontal-01_e7de4434b2.png" width="600" />
<img src="https://hpi.de/fileadmin/_processed_/csm_WEB_editor-01_1d3222effd.png" width="600" />

The editor consists of 2 main components: 

1. the voxel editor (in javascript, thus platform-independent) and 
2. the simulation (on windows only!)

**For developers:** the system implementation is described in our research paper: [https://hpi.de/baudisch/projects/metamaterial-mechanisms.html](https://hpi.de/baudisch/projects/metamaterial-mechanisms.html)

Please note that this is a research prototype implementation. Feel free to add and discuss issues in the discussion board and to help each other out. 



## Editor
_ADD how to run the editor_





## Simulation (on Windows only)
The simulation works only on Windows, since there is no Grasshopper for Mac. 


#### How to install:

1. install [Rhino 5](http://www.rhino3d.com/download)
2. install [Grasshopper](http://www.grasshopper3d.com/page/download-1)
3. install [karamba 1.1.0](http://www.food4rhino.com/app/karamba?etx=)  
    for licence choose "free" (NOT trial), use metric units
4. copy the items from 'src/simulation/bin/' to Grasshopper's Components folder. Find the folder by opening Grasshopper in the File menu 'Special Folders' - 'Components Folder'. (opening Grasshopper: start Rhino and type "grasshopper" into Rhino's command line)

To run the simulation, simply execute the batch script "1-START-SIMULATION.bat". As soon as the simulation is running, it can receive data from the editor.


#### If you don't use Windows, you can install the simulation on some remote Windows-machine: 
You can install the simulation on a remote Windows machines and let the platform-independent editor connect to that machine. The communication works via web sockets. You need to set the IP of your remote machine in 'config.json'. Set the editor's IP in 'src/simulation/editorURL.json'.


##### Troubleshooting: 
If Grasshopper cannot load the InputComponent, then it's dependencies might be blocked. Right-click the two .dll files in your Components folder and tick the checkbox "Unblock". Start the simulation using the batch script again.

<img src="http://alexandraion.com/wp-content/uploads/unblock_dll.jpg" width="400" />


##### For developers:
The Grasshopper components are developed in Visual Studio 2012 and they target .NET 4.5. Pre- and post-build events copy the neccessary binaries to the bin folder. In case you develop the components further, you can add post-build events to copy the 4 binaries directly to the Grasshopper Components folder. You can also debug the components by pointing to Rhino.exe in the project settings - Debug - Start external program. (It's already set, but the path might differ on your machine.)