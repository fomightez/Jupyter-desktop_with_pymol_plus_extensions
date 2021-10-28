# Jupyter Desktop Server with PyMOL installed
[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/fomightez/Jupyter-desktop_with_pymol/master?urlpath=desktop)

## How to start a remote computing session and open & use PyMOL on the remote desktop

To get started, click on `launch binder` badge at the top of bottom of this page.

In the upper left of the desktop screen, click on `Applications` > select `Run Program...` from the top of the list, and enter `pymol` (all lowercase). Click the `Launch` button below where you entered `pymol`
That will Launch PyMOL on a remote, temporary computer streaming in your browser.

Choose `Skip Activation` at the bottom the dialog box that comes up as PyMOL starts.

Adjust the width of the PyMOL window by dragging on the bottom right corner down and to the right to maximize screen real estate to suit your preference.

Next to any `PyMOL>` prompt you see on the screen, type `fetch` followed by a PDB id and you'll be viewing your choice of molecule.

If you end up making anything useful, such as a session file (ending in `.pse`) or image file, you'll want to download it to your local machine. You'll need to do that from a different interface with the remote machine. Look at the URL of your PyMOL session screen and copy it. It will look similar to the following but be unique in some ways, such as the part in front of `mybinder` may be different depending on where in the global network the remote machine is:

```
https://hub.gke.mybinder.org/user/fomightez-jupyt-ktop_with_pymol-r7gbgfa3/desktop/?token=zdDDLXhXTzSw7Xcg0g1zfg
```

You want to look for `desktop` in front of `/?token..` and copy everything in front of `desktop` to **ANOTHER browser window** and add on `lab` at the end. This will result in something like this example below that's built on the example above:

```
https://hub.gke.mybinder.org/user/fomightez-jupyt-ktop_with_pymol-r7gbgfa3/lab
```

Hit return to load the page. Your generated PyMOL session file (ending in `.pse`) or image file should appear in the list of files in the file navigation panel in the upper. Right-click on the file in the list, and select `Download` from the middle of the list of possible actions.

----

## How to use the PyMOL GUI in general

I list a number of resources for using PyMOL [here](https://github.com/fomightez/pymol-binder#resources).  
There are several tutorials listed towards that bottom of that list that use the graphical user interface for interacting with PyMOL. **Using PyMOL via a mouse and display is how people tpyically use PyMOL.** Those steps should work in sessions launched from here.  However, the top of that list emphasizes using the commands and scripts to interact with PyMOL and allow one to work more reproducibly or accomplish repetitive tasks. 

-----

## How to use PyMOL using scripts and the API

**While using PyMOL via a mouse and display is how people tpyically use PyMOL, it isn't the only way.**  
If you want to use PyMOL reproducibly or do repetitive tasks in a largely automated way using scripts and the API, see [here for PyMOL use via commandline on Jupyter using MyBinder](https://github.com/fomightez/pymol-binder).

-----

## Extending PyMOLs abilities

There's software availabe that extends PyMOL's abilties and features. For example, [psico](https://pymolwiki.org/index.php/Psico) is a python module which extends PyMOL with many commands. I have made a separate repo [here](https://github.com/fomightez/Jupyter-desktop_with_pymol_plus_extensions/) as a playground for adding such extensions. See there and the 'Technical details' below for guidance if adding these to this remote-served PyMOL interests you.  




-----

## Technical details

<details>
  <summary>Click to expand and see technical details from October 27th, 2021 onward.</summary>

October 26th, 2021, I had restored to a working state. the version of the desktop Jupyter with pymol installed and working as a GUI. This was the version of the desktop and Pymol that looked okay but graphically wasn't the best. It was based on what [here](https://github.com/fomightez/jupyter-desktop-server) is based on. I plan to leave that in the current state because I found on October 26th probably good to have some variants of this tech available since it can be a bit fragile and having things that I knew worked in past can be useful.  
Lately, I had seen that [here](https://github.com/jupyterhub/jupyter-remote-desktop-proxy) updated the Linux remote desktop look be nicer and have a better user experience. For example, in addition to the better graphics, you no longer had to choose 'Use default config' button after launch. Thought since better, it may help impove using PyMOL via this system, too, and so I made repository [here](https://github.com/fomightez/jupyter-remote-desktop-proxy), where I could adapt the current version of [here](https://github.com/jupyterhub/jupyter-remote-desktop-proxy/tree/7d9b2810669e22b5ecdcfee8d8f531c3da0ab8a9) to add in PyMOL. I succeeded in adding it in [there](https://github.com/fomightez/jupyter-remote-desktop-proxy) and PyMOL worked with the better linux desktop interface (**BETTER GRAPHICS AND DESKTOP EXPERIENCE**) as of October 27th, 2021, in launches from [this version](https://github.com/jupyterhub/jupyter-remote-desktop-proxy/tree/7d9b2810669e22b5ecdcfee8d8f531c3da0ab8a9).
On October 27th, 2021, I converted this repo over from the previous desktop experience to the updated Linux dekstop experience based on [here](https://github.com/jupyterhub/jupyter-remote-desktop-proxy/tree/7d9b2810669e22b5ecdcfee8d8f531c3da0ab8a9) in the hopes I can easily now share the better desktop experience with PyMOL (**BETTER GRAPHICS AND DESKTOP EXPERIENCE**) instead of the older graphics experience that while useable, was not nearly as good as working with PyMOL directly on a computer. I find the experience based on [here](https://github.com/jupyterhub/jupyter-remote-desktop-proxy/tree/7d9b2810669e22b5ecdcfee8d8f531c3da0ab8a9) seems very close to working with it on your own machine if you expand the browser window and then click drag the PyMOL window inside the desktop view.  

For now, it is basic PyMOL. I have removed the [psico](https://pymolwiki.org/index.php/Psico) python module that extends PyMOL with several commands, as well as the [rna-tools](https://github.com/mmagnus/rna-tools). In fact, I decided a separate place for running/testing extensions may be in order as I have referred people here for PyMOL now and would be best to maintain an experience close to what they'd have if installed the standard software. See https://github.com/fomightez/Jupyter-desktop_with_pymol_plus_extensions/ for that.
</details>

<details>
  <summary>Click to expand and see technical details prior to October 27th, 2021.</summary>

This repo was originally meant to be able to run `pymol_preview_generator.py` from [here](https://github.com/mmagnus/rna-tools/tree/master/rna_tools/tools/pymol_preview_generator); however, the XFCE desktop doesn't seem to allow the icons to be changed (even using `gio set`), and so that was **a dead-end effort for now**. However, since PyMOL did at leat work in the desktop GUI, I left it in this state and a use case arose later where I could use it for training.

Presently, PyMOL installed here has the [psico](https://pymolwiki.org/index.php/Psico) python module that extends PyMOL with several commands. For example, presently [load_aln](https://pymolwiki.org/index.php/Load_aln) and [xfit](https://pymolwiki.org/index.php/xfit) are ready-to-use. Note that the addition of this module means `save` and `fetch` become 'overloaded with extra abilities as described [here](https://pymolwiki.org/index.php/Psico#Initialization) unless you use the `psico.init` approach specified there when importing. The fact psico doesn't even carry all the abilities needed, for example, `xfit` requirs the dependency csb is a reason I like using Binder when installing various combinations of 'extras' to test. This way I know my local installation will remain intact and I can just easily roll the repo back if something breaks, with no effect on anything else.


[Original source repo](https://github.com/yuvipanda/jupyter-desktop-server) allows running Run XFCE (or other desktop environments) on a JupyterHub. Source based on https://github.com/ryanlovett/nbnovnc and a fork of https://github.com/manics/jupyter-omeroanalysis-desktop .

Details on some of the underlying tech is found under 'Details' [here](https://www.ovirt.org/develop/release-management/features/virt/novnc-console.html). `pymol_preivew` added from [here](https://github.com/mmagnus/rna-tools/tree/master/rna_tools/tools/pymol_preview_generator). PyMOL added as described [here](https://github.com/fomightez/pymol-binder).

Originally, dimensions of the desktop geometry were set to '1680x1050' due to [original source repo](https://github.com/yuvipanda/jupyter-desktop-server), but PyMOL interface was overly pixelated; copied '1024x768' geometry from [here](https://github.com/manics/jupyter-omeroanalysis-desktop/blob/napari-binder/jupyter_desktop/jupyter_desktop.py).

This had stopped working apparently when they updated behind-the-scenes of Binder in late summer/eary Fall 2021 (the change that made JupyterLab the default). Luckily, the headless one [here](https://github.com/fomightez/pymol-binder) continued to work and show it had PyQt5 installed and working which is what I thought was the issue with this one as a I attempted to fix before realizing PyQt5 worked there. And after much fussing around in October 2021, I got it back to working based on that repositories `apt.txt` and `environment.yml` as the basis. It  did say, "There was an error initializing GLEW. Basics graphics, including shaders and volumes may be unavailable." However, I don't know if I overlooked this earlier and this is much improved since nothing was working in the last few days. While trying to fix the PyQt stuff, I had based on [here](https://stackoverflow.com/a/64353952/8508004) also added several items to `apt.txt` that I didn't have before. Realized in looking for help fixing PyMOL on remote session in October 2021, that this list comes from [here under what would be necessary for compiling](https://pymolwiki.org/index.php/Linux_Install). For now they are there; I meant to check if necessary or not. Also, I don't know what changed behind-the-scenes of Binder in late summer/eary Fall 2021. I guess the desktop version had additional stuff that got removed and this additional stuff made it so I didn't have to add much to `apt.txt` here prior to recently, so that it was simpler than [the apt.txt at my HEADLESS-working pymol-binder](https://github.com/fomightez/pymol-binder/blob/master/apt.txt). Odd, but I'm glad I had two different ones, one being more reliant on just what is in a repo, at the time.
</details>

----

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/fomightez/Jupyter-desktop_with_pymol/master?urlpath=desktop)
