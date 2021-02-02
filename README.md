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
You should first set up your laptop in a way that you can connect to the LLR servers and use the Jupyter notebook from the outside. For this, you need to create a SSH key and upload it to any LLR server. If you are using an operating system of the Microsoft Windows family, you can install Ubuntu via the Linux Subsystem for Windows and start a terminal emulator this way.

Once you are in your terminal, create the key with the following program (just hit enter all the time to accept the defaults):

  `ssh-keygen`

Next, you copy the key over to an LLR server:

  `ssh-copy-id -i ~/.ssh/mykey appro2@polui01.in2p3.fr`

This one time you'll need a password, just ask me about it.

### What you need to do every time

Now connect to the tunneling machine:

  `ssh -Y appro2@llrgate01.in2p3.fr`

from there connect to the working machine:

  `ssh -Y appro2@polui01.in2p3.fr`

When you are there you should run this three commands to make `ROOT` available inside your working area:

  `module use /opt/exp_soft/vo.llr.in2p3.fr/modulefiles_el7`

  `module load python/3.7.0`

  `source /opt/exp_soft/llr/root/v6.14.04-el7-gcc71-py37/bin/thisroot.sh`

Open a Jupyter notebook:

  `jupyter-notebook --no-browser --ip 134.158.128.183`

this should promptyou a link of this kind:

  `http://134.158.128.183:<port_number>/?token=7a6d205f71ec2eea66ae613ee3a969e71314ebef3d255989`

Now open a second terminal window and run the following:

  `ssh -L<port_number>:polui01.in2p3.fr:<port_number> appro2@llrgate01.in2p3.fr`

Now you can past the link inside your favourite browser substituting:

`134.158.128.183` with `localhost`

And the magic is done: the Jupyter Notebook should be open and running.
