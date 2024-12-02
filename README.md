# simulations for smart pixels

# setup environment
```
setupATLAS
lsetup "python 3.9.18-x86_64-centos7"
lsetup "root 6.28.08-x86_64-centos7-gcc11-opt"
```

# first get pythia 8.307
```
wget https://pythia.org/download/pythia83/pythia8307.tgz
tar -xvf pythia8307.tgz
cd pythia8307
make
````

# update this path to your pythia path in Makefile.inc
`PREFIX=/home/abadea/pythia8307`

# setup this repo and run test
```
make all
./bin/minbias.exe cards/minbias.cmnd myTree.root 100
```

# with the docker images
```
git clone --recursive
docker run -it -v /local/d1/badea:/local/d1/badea local/my-image # open with binding
cd /local/d1/badea/tracker/cmspix28-mc-sim/pixelav
mkdir bin
gcc ppixelav2_list_trkpy_n_2f.c -o ./bin/ppixelav2_list_trkpy_n_2f.exe -lm -O2
cd ..
make
python launch.py -o temp -n 100
```
# References and Credits
https://github.com/elizahoward/cmspix28-mc-sim (Eliza Pixel Sim)
https://github.com/elizahoward/pixelav (Pixel AV)
https://github.com/elizahoward/smart-pixels-ml (Smart Pixels ML)
https://github.com/kdipetri/produceSmartPixMuC (produce Smart Pixels MC)
https://github.com/kdipetri/cmspix28-mc-sim (Pixel SIM Karri)