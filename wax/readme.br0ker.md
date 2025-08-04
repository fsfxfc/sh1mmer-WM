# Br0ker

### Building Sh1mmer with an update payload

*Note that the web builder **cannot** be used to build shims with update payloads.*

1. Get Sh1mmer
```
git clone https://github.com/MercuryWorkshop/sh1mmer
```

2. Download the update for your board *(it may ask you to install dependencies)*
```
cd sh1mmer/wax
bash update_downloader.sh <board>
```
(Replace `<board>` with your board (lowercase). Currently most common boards are supported.)

The downloaded update files will now be located in `sh1mmer/wax/mounted_payloads/updates/16093`.
You may want to delete these when you're done building your shim, as they will automatically be built into any shims you build in the future otherwise.

3. Build Sh1mmer with extra space
```
sudo bash wax.sh -i <raw_shim.bin> -s 2.0G
```
(Replace `<raw_shim.bin>` with the raw shim bin file for your board. You may also need more than 2.0G of space.)

### Usage (Sh1mmer only)
Simply navigate to the payloads selector and select "Br0ker". Be sure not to unplug the USB drive until Br0ker is finished.

# update_downloader

update_downloader is currently hardcoded to use the list of updates in `lib/latest_r132.txt`.
The format for this file is each line should be `board,filename` where `board` is the board name in lowercase and `filename` is the name of the full (non-delta) update payload file.

Usage:
```
bash update_downloader.sh <board> [output dir]
```
This will download the update payload for the specified board, assuming it is in the list of updates.
If the output directory is unspecified, update_downloader will use `mounted_payloads/updates`.
