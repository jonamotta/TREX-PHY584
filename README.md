# TREX-PHY584
Ministage in HH->bbtautau for the PHY584 course 

## The LHC complex
The LHC is a circular particle accelerator. The collider has two adjacent parallel beamlines in which particles travel in opposite directions along the 26.7km ring. The beams intersect at four points where the particle collisions take place and the data collection is carried out by the four main experiments: CMS, ATLAS, LHCb and ALICE. When seen as part of the entire CERN complex, the LHC is the last element of an injection chain composed of several particle accelerators whose purpose is both to supply the LHC and to deliver accelerated particles to experiments that are not the four ones placed on the LHC beamline.

The LHC, when accelerating protons, works at a peak center-of-mass energy of 13 TeV and a collision rate of 40 MHz. The reachable instantaneous luminosity is $\mathcal{L} = 10^{34}cm^{-2}s^{-1}$. These specifications are chosen to investigate the TeV scale physics, to understand the process of EWSB, and to study the role played by the H in it.

The LHC started its operation in 2008 and two phases of its working life have been completed: Run1 and Run2, respectively referring to the 2009-2013 and 2015-2018 data taking periods.

## The CMS experiment
The CMS detector is a multipurpose apparatus optimized to study high transverse momentum physics processes in proton-proton (pp) collisions. The central feature of the apparatus is a superconducting solenoid, providing a magnetic field of 3.8T parallel to the beam direction. Charged particle trajectories are measured by the silicon pixel and strip trackers, which cover a pseudorapidity region of $|\eta| < 2.5$; pseudorapidity is defined as $\eta = -\text{ln}(\tan{\frac{\theta}{2}})$, where $\theta$ is the angle between the trajectory of the particle and the direction of the beam. A lead tungstate crystal electromagnetic calorimeter (ECAL), and a brass and scintillator hadron calorimeter (HCAL) surround the tracking volume and cover $|\eta| < 3$. The steel and quartz-fiber Cherenkov hadron forward calorimeter extends the coverage to $|\eta| < 5$. The muon system consists of gas-ionization detectors embedded in the steel flux-return yoke outside the solenoid, and covers $|\eta| < 2.4$. The selection of the physics of interest is done through the CMS trigger system which consists of two levels designed to single out events from the 40 MHz interaction rate of collisions. The first level of the trigger is implemented in hardware while the second level is implemented in software and further refines the purity of the output stream.

## Setting up the working environment

### What you need to do just once
You should first set up your laptop in a way that you can connect to the LLR servers and use the Jupyter notebook from the outside. For this, you need to create a SSH key and upload it to any LLR server. 

If you are using an operating system of the Microsoft Windows family you have two options:
* you can install Ubuntu via the Linux Subsystem for Windows and start a terminal emulator this way (I am not a Linux expert so I wwon't be able to help very much with this)
* download the [MobaXterm](https://mobaxterm.mobatek.net) terminal emulator and work from there (this proved to work smoothly and efficiently last year)

Once you are in your terminal, create the key with the following program (just hit enter all the time to accept the defaults):

  `ssh-keygen`

Next, you copy the key over to an LLR server:

  `ssh-copy-id -i ~/.ssh/mykey appro2@polui01.in2p3.fr`

This one time you'll need a password, just ask me about it. 

Now it's time to configure your ssh client to connect to the LLR severs via the correct proxy server from the outside. To do so, add the following lines to your `~/.ssh/config` file (if you have one) or cretae a new one (if you do not have one):

  ```
  Host *.in2p3.fr
    AddKeysToAgent yes
    UseKeychain yes
    IdentityFile ~/.ssh/<mykey>
    XAuthLocation /opt/X11/bin/xauth
    ForwardAgent yes
    ForwardX11 yes
    ForwardX11Trusted yes
    PasswordAuthentication yes
  ```
**NB** be careful to put the correct name of your ssh key in the 4th line!!

You should now be able to conect to any of the LLR interactive servers as follows, even from the outside:

  `ssh 'appro2@polui01.in2p3.fr'`

If this setup does not work (like last year for someone) we will sort it out in another way with the network manager.

### What you need to do every time

Connect to the working machine:

  `ssh -Y 'appro2@polui01.in2p3.fr'`

#### If you are inside the LLR network:

open a Jupyter notebook:
  
  `notebook` (if you are inside the LLR network)
  
this should prompt you a link of this kind:

  `http://polui01.in2p3.fr:8888/?token=cb13ddc3d6da41a2e1f52f9fc46081038fad3991d17881de`

past the link inside your favourite browser, and the magic is done: the Jupyter Notebook should be open and running.

##### If you are outiside the LLR network:

open a Jupyter notebook:

  `notebook01_gate` (if you are outside of the LLR network)

this should prompt you a link of this kind:

  `http://134.158.128.183:<port_number>/?token=7a6d205f71ec2eea66ae613ee3a969e71314ebef3d255989`

now open a second terminal window and run the following:

  `ssh -L<port_number>:polui01.in2p3.fr:<port_number> appro2@llrgate01.in2p3.fr`

now you can past the link inside your favourite browser substituting:

  `134.158.128.183` with `localhost`

and the magic is done: the Jupyter Notebook should be open and running.
