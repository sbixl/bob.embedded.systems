# bob.embedded.systems

minimum: Ubuntu 23.10 because of glibc support min 2.36 in basement layer of bob

sudo apt install python3-pip python3-venv git

mkdir -p ~/tools/bob
cd ~/tools/bob
python3 -m venv .
python3 -m pip install BobBuildTool

source ~/tools/bob/bin/activate
bob --version

git clone https://github.com/sbixl/bob.embedded.systems.git --recurse-submodules
cd bob.embedded.systems

sudo apt install m4 swig libssl-dev uuid-dev libgnutls28-de

Note: swig, libssl-dev, uuid-dev and libgnutls28-de are required to build the u-boot tools (should be added as recipes in future)

bob dev sbc/board::rpi/board::rpi-variant-4-b-64-bit -v
