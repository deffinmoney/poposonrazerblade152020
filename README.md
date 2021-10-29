# poposonrazerblade152020
Making Pop!_OS run best on Razer Blade Advanced 15 2020 Model

It is relatively easy and if you decide to try to run Pop on the Razer Blade 15 Advanced from 2020 then there are 2 .conf/settings to change for you to have the best experience. These are just a few things I have noticed and done so far and I hope it saves some people some time and trouble. 

First you will want to have secure boot turned off and be sure to use the Nvidia ISO that System76 provides at https://pop.system76.com/.
I like to use rufus (https://rufus.ie/en/) to make the ISO into a bootable USB if coming from Windows and balenaEtcher (https://www.balena.io/etcher/) if coming from a Mac.

After installing Pop on your Razer Blade you will want to update via the Pop Shop or the terminal. I find waiting a few minutes for the pop shop to load and update from there the most efficient because it seems to "hijack" the process from the terminal anyways.

Once updated you will want to fix the suspend loop issue that you get with this laptop amoung others.
Go to /etc/kernelstub and edit the configuration file. You will want to append "button.lid_init_state=open" the user section. Be sure to include the comma to separate the line above from the new line.
You can also just use the command

sudo kernelstub -a "button.lid_init_state=open"

Next you may want to make it so that everytime you resume from suspend you dont see the kernel messages printing as x crashes and restarts due to a Nvidia/acpi/x conflict. This only happens when you are in a graphics mode that includes the discrete gpu. If you are only in the Intel graphics mode it does not happen.

For this you will want to edit sysctl.conf, to do this:

sudo nano /etc/sysctl.conf

Then, uncomment the "kernel.printk = 3 4 1 3" line.

Now reboot.

Please leave feedback and let me know it this helped or did not.
