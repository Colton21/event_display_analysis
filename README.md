<snippet>
  <content>
#{Event Display Analysis}
TODO: Consider the Larlite, Argo, and Bee event displays.

##Event Displays

  All of the event displays have many buttons and configurations to keep them modular and useful for as many members of the collaboration as possible. This however means that there are many configurations that students will potentially need to deal with.

##Larlite event display:

  The larlite event display takes several packages and requires a fair number of steps to setup. These steps may also vary slightly based on the OS. I have a working version on my Mac OSX, but I will try and make sure these instructions also work for Linux distributions.
  
  The larlite event display has both a 2D and a 3D viewer. The 3D viewer is rather bare-bones, but I believe this does have the ability to display truth information.
  
#Requirements
  In order to run larlite and the larlite event display we will need a few things installed already:
  1. CERN Root installation - make sure that pyROOT is enabled during installation
  2. Python (preferrably version 2.7.X release)
  3. Several Python Packages
    1. NumPy
    2. PyQt4
  4. Qt and sip
  
  For Ubuntu systems there is a good chance that Qt, sip, and PyQt4 are already installed on your system. If PyQt4 is not installed, then make sure that Qt and sip are installed before trying to installed PyQt4. [Installation tips for PyQt4](https://cdcvs.fnal.gov/redmine/projects/ubooneoffline/wiki/Larlite_Evd).
  
###Installation
  The first step for setting-up the larlite event display is to have larltie installed. Installing larlite is not very difficult and is outlined very clearly by Taritree Wongjirad of MicroBooNE on his [github page] (https://github.com/twongjirad/LArLiteSoftCookBook/wiki/build-and-setup-LArLite). This builds the core version of larlite.
  
  For simply the commands needed to get a working build:
  
  ```bash
      git clone https://github.com/larlight/larlite.git
      cd larlite
      source config/setup.sh
      make -j4
  ```
  
  This should take a few minutes. Now to build the event display, we need to:
  
  
  ```bash
      cd UserDev/DisplayTool/
      source setup_evd.sh
      make
  ```
  This should take another few minutes to build the event displays.

  You can test to make sure that your larlite installation can find the location of your ROOT libraries, to make use of pyROOT and that PyQt4 is properly installed by starting a python shell and typing:
  
  ```python
      import ROOT
      import PyQt4
  ```
  Be aware that case matters!

###Usage

  When entering a new session, larlite will, naturally, still be built, but you will need to make sure that you setup the same uboonecode environment used when installing larlite. In your larlite directory, make sure to once again `source config/setup.sh`.

  An immediate limitation I should note is that to properly run the larlite event display we will need a larlite file. The 2D version of the larlite event display also does not dispaly truth information (mctrack / mcshower)

  You can run the larlite 2D event display simply by typing: `evd.py -u [file]` or the 3D display by typing `evd3D.py -u [file]`. These scripts are located in `UserDev/DisplayTool/python`.
  
  The display supports all 3 planes for the detector as well as a host of options on both sides. To view only 1 plane at a time, select one of the planes from the View Options in the bottom left. Above this are some useful tick-boxes - by ticking the "Wire Drawing" option, an ADC vs Time plot will appear at the bottom of the display. Clicking on a wire will update this plot. Clicking on both "Use cm" and "Draw Scale Bar" makes a scale bar in cm appear on each wire plane. This bar scales with the zoom of each individual plane, which can be useful for orientation.
  
  The bubbles in the top right-hand corner control more display options. Selecting "Wire" from the "Wire Draw Options" bubbles, will display the wires (essentially a dark-blue background). Then we have a series of drop-down menus which select the producer we would like to use to display the event information. I think each one of these will be selected in the future.
  
  The larlite event display also has an in-built screen capture feature, with the button located in the bottom right.
  
  The ReadMe for the developer's GitHub page contains some additional advice, located [here] (https://github.com/coreyjadams/EventViewer). **NOTE: that repository has an out-dated version of the event display. Do not use this particular build.**

##Argo Event Display:

  Argo is a browser-based event display and as such requires no direct installation.
  
  I have a suspicion that you need an active VPN to Fermilab's network to access the event display (security and confidentiality likely).
  
##Bee

  Bee is also a browser-based event display and requires no direct installtion. This was tested wtih Google Chrome.
  
  On a first-pass, the Bee event display has a quick response time and has some [already generated files to view](http://www.phy.bnl.gov/wire-cell/bee). It doesn't appear to need any VPN to access from outside Fermilab.
  
  The event display seems to be exclusively a 3D viewer, which has a nice display. However when zooming in closely to objects, they appear to remain at the same resolution.
  
###Usage

  Using the display seems to be extemely simple. Unless I am missing something, all of the functionality can be easily learned in 15 minutes to so. Using a combination of the mouse to rotate and zoom and the keyboard to traverse users can explore the MicroBooNE detector.
  
  The interface looks very nice, however is mostly just repeated functionality, which consists mostly of righting the camera to xy, xz, yz positions and choosing from which producer information to display.
  
  From my 30 min of playing around with the event display, I have been unable to discover where and how the wire information is accesed. Clicking on the areas with charge deposition do not provide further information regarding how much, though the colouring gives relative deposition amounts.


## Credits
VENu - mobile app (Marco)
ARGO - browser (Nathaniel)
Bee - browser (BNL)
LArlite - "standalone" (Corey, Yale)
## License
TODO: Write license
</content>
  <tabTrigger>readme</tabTrigger>
</snippet>
