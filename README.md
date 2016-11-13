# mppTracker
python max power point tracker for solar cells (hopefully robust enough for perovskites)


## Installation
#### Windows and MacOS
1. Install Anaconda [from here](https://www.continuum.io/downloads) (Choose the largest python version number)
1. Run the "Anaconda Prompt" program that was installed in step #1 and type the following in:

  ```bash
conda update --all
conda install git pyserial
pip install pyvisa pyvisa-py
git clone https://github.com/AFMD/mppTracker
cd mppTracker
# now see Usage section below
```  

#### Ubuntu
  TODO  

#### Arch Linux
  TODO  

## Usage
```
usage: mppTracker.py [-h] [--dummy] [--visa_lib VISA_LIB] [--reverse_polarity]
                     address t_dwell t_total

Max power point tracker for solar cells using a Keithley 2400 sourcemeter
(hopefully robust enough for perovskites). Data is written to stdout and human
readable messages are written to stderr.

positional arguments:
  address              VISA resource name for sourcemeter
  t_dwell              Total number of seconds for the dwell phase(s)
  t_total              Total number of seconds to run for

optional arguments:
  -h, --help           show this help message and exit
  --dummy              Run in dummy mode (doesn't need sourcemeter, generates
                       random data)
  --visa_lib VISA_LIB  Path to visa library in case pyvisa can't find it, try
                       C:\Windows\system32\visa64.dll
  --reverse_polarity   Swaps voltage polarity on output terminals.
```

## Requirements
* pyvisa (tested with version 1.8)
* pyvisa-py (tested with version 0.2, this is optional depending on how your sourcemeter is attached)

## Examples
```bash
python mppTracker.py GPIB0::24::INSTR 10 120 # GPIB attached sourcemeter
python mppTracker.py TCPIP::192.168.1.54::INSTR 10 120 # ethernet attached sourcemeter
python mppTracker.py USB0::0x1AB1::0x0588::DS1K00005888::INSTR 10 120 # USB attached sourcemeter
python mppTracker.py ASRL::COM3::INSTR 10 120 # rs232 attached 10 sourcemeter
python mppTracker.py ASRL::/dev/ttyUSB0::INSTR 10 120 # rs232 attached sourcemeter
```
