# Claymorify

## A handy tool to keep Claymore's straps, rxboost and other optimalizations working with other miner apps.

The app simply starts Claymore miner and when the optimizations is done it stops Claymore mining (but keep Claymore running) and starts another miner.

> You can do the same with your hands if Windows started. This tool is useful for big mining farms or when your mining rig restarts often.

## Usage:
Download and save Claymorify.exe to your Claymore miner folder (eg. C:\MinerClay\Claymorify.exe).

> Some of the antivirus programs report false positive because the Claymorify.exe is packed.
> If you don't trust it, don't use it!
> Original file md5 is 36fb71a79514efb0a82c7f6464745de0.

Create Claymorify.bat (eg. C:\MinerClay):
```
@echo off
cd C:\MinerClay
start Claymorify.exe -cp "C:\MinerClay" -ce "start-miner.bat" -i 012345 -p "updating memory timings finished" -d 10 -mp "C:\Miner" -me "start-miner.bat"
```

> Command line parameters:
```
-cp Path of the Claymore miner, eg. "C:\MinerClay"
-ce Executable of the Claymore miner, eg. "start-miner.bat"
-i The index of the cards which must to be paused, eg. 012345
-p The log string after Claymore miner automatically paused, eg. "updating memory timings finished"
-d The delay of seconds after miner automatically paused after the specified log line, eg. 10
-mp Path of the another miner, eg. "C:\Miner"
-me Executable of the another miner, eg. "start-miner.bat"
```

Create Claymore start-miner.bat (eg. C:\MinerClay\start-miner.bat):
```
@echo off
cd C:\MinerClay
set GPU_FORCE_64BIT_PTR 0
set GPU_MAX_HEAP_SIZE 100
set GPU_USE_SYNC_OBJECTS 1
set GPU_MAX_ALLOC_PERCENT 100
set GPU_SINGLE_ALLOC_PERCENT 100
EthDcrMiner64.exe
```

Example another miner start-miner.bat (if another miner is PhoenixMiner, C:\Miner\start-miner.bat):
```
@echo off
cd C:\Miner
set GPU_FORCE_64BIT_PTR 0
set GPU_MAX_HEAP_SIZE 100
set GPU_USE_SYNC_OBJECTS 1
set GPU_MAX_ALLOC_PERCENT 100
set GPU_SINGLE_ALLOC_PERCENT 100
PhoenixMiner.exe
```

Example Claymore config.txt (eg. C:\MinerClay\config.txt):

**Change your cclock, mclock, cvddc, mvddc, straps, rxboost values.**
```
-cclock 1215
-mclock 2150
-cvddc 900
-mvddc 900
-strap 1
-rxboost 1
-allcoins 1
-asm 2
-dbg 0
-ejobtimeout 1440
-epool eu.ubiqpool.io:8008
-epsw x
-erate 0
-eres 0
-etha 0
-ethi 15
-ewal 0xddddc346c04992cc4b9cac33187869dd0808ab77
-logsmaxsize 10
-mode 1
-mport -81
-r -1
-retrydelay 1
-tt 0
-wd 0
```
> The epool and ewal value does not matter because Claymore mining stops after optimizations applied. Its only needed to set the correct cclock, mclock, cvddc, mvddc, strap, rxboost values in an Ethash algo coin with smaller DAG.

Edit your another miner config.txt (eg. C:\Miner\config.txt).

**You must define the same cclock, mclock, cvddc, mvddc values in your another miner config.txt.**

### If you like this tool please send a small amount of donation (minimum 0.05 ETH) to 0xdddddddc3c1c2c2bbb0955f143cf1521ec90ed41 address or the tool will stop after several hours of running.
