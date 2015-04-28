Running Google DeepMind Atari Deep Q Learner on an Ubuntu VirtualBox in OS X on a Mac Pro (Cylinder)
==============================================================

Follow the following steps and expect to spend some time debugging the procedure!

I. Make a virtual machine
-------------------------

I used a fixed size VirtualBox's own virtual disk format as the hard-disk. I installed Ubuntu 14 with live CD on this machine. To fix the virtual machine screen resolution problem follow these steps (source: http://askubuntu.com/questions/240745/how-do-i-get-a-larger-screen-resolution-in-virtualbox-on-mac-os-x)

1. Turn off 3D Acceleration in the VM settings.
2. Run these code in a terminal in virtual machine:
```
apt‐get update
apt‐get upgrade
apt‐get install dkms
apt‐get install build‐essential
```
3. Go to the Devices menu and tell it to install the Guest Additions. A new CDROM will appear on the desktop. Rightclick and choose the Autorun.
4. Restart the VM.
5. Now resize the VM window or choose Full Screen mode and it will resize the desktop screen resolution properly.
6. You can eject the Guest Additions CDROM.

II. Install ipython notebook
----------------------------

Run these commands and make sure they suceed in installing the packages.
```
sudo apt-get install python-pip
sudo pip install "ipython[all]"
sudo apt-get install libzmq3-dev
sudo apt-get install python-zmq
sudo pip install markupsafe
sudo pip install jsonschema
ipython notebook
```
The last line is just to test if the ipython browser window works and opens properly. If not, see what package is missing and causing the error.

III. Install Torch
------------------

Follow the instructions on http://torch.ch/docs/getting-started.html#_ , but you may have to use `sudo` for some of the commands:
```
curl -sk https://raw.githubusercontent.com/torch/ezinstall/master/install-deps | sudo bash
git clone https://github.com/torch/distro.git ~/torch --recursive
cd ~/torch;
sudo ./install.sh
```
Make sure that the torch directories are added at the end of `~/.bashrc`, then restart the terminal. Test if Torch is properly installed by running `th` and `itorch notebook`.


IV. Install Deepmind's Package
------------------------------

Download deepmind's package for example at https://github.com/kuz/DeepMind-Atari-Deep-Q-Learner/archive/master.zip. Extract it, and go inside the folder and run `sudo ./install_dependencies.sh`.

If some packages are still missing, you can download them one by one, extract them, and go to their directory and run this command there:
`~/torch/install/bin/luarocks make`
