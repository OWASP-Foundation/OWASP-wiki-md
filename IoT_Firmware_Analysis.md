<center>

[Back To The Firmware Analysis
Project](https://www.owasp.org/index.php/OWASP_Internet_of_Things_Project#tab=Firmware_Analysis)

</center>

## Obtain and Analyze Firmware

### Obtain Firmware

  - From vendor download site
  - Capture during device update
  - Extract directly from hardware

### Analyze Firmware File

  - Run the "file" command on the \*.bin file

` * We are looking for File to return as "data"`

  - Verify the MD5 signature if you have it

`* Run the "cat" command on the *.md5 file`
`* Run the "md5sum" command on the *.bin file`

  - Run "strings" against \*.bin file

`* ex. "strings -n 10 xyz.bin > strings.out"`
`* ex. "less strings.out"`
`* Running strings can give deeper insight into the file`

  - Run "hexdump" against \*.bin file

`* ex. "hexdump -C -n 512 xyz.bin > hexdump.out"`
`* ex. "cat hexdump.out"`
`* Running hexdump can help identify the type of firmware build`

  - "binwalk" will be one of the primary tools used for analyzing,
    reverse engineering and extracting data from the firmware image

`* ex. "binwalk xyz.bin"`
`* We are looking for binwalk to identify the type of file system in use, ex. squashfs filesystem`

### Extracting the File System from the Firmware File

  - Run binwalk against the firmware file

`* ex. "binwalk xyz.bin"`
`* Again, we are looking for binwalk to hopefully identify the file system`

  - Extracting the filesystme using "dd"

`* Assuming binwalk has identified a valid file system like squashfs for example, we can use "dd" as one way to extract the file system`
`* ex. "dd if=xyz.bin bs=1 skip=922460 count=2522318 of=xyz.squashfs"`
`* Note: skip and count values will vary depending on your specific bin file`

  - Following extraction of the filesystem assuming it is squashfs, we
    can expand the contents by running "sasquatch"

`* ex. "sasquatch xys.squashfs"`
`* "cd" into "squash-root" and have a look around for interesting things`
`* Some examples include:`
`* /etc/ssl`
`* /etc/passwd`
`* /etc/shadow`
`* .ssh/authorized_keys`

### Using the Firmware Modification Kit

  - The firmware modification kit can be used to attempt extracting a
    file system that is is not the traditional squashfs file system
  - Typically if you run hexedit on the firmware file you will see
    "sqsh" at the beginning of the file, however if you see something
    like "shsq" it's probable that the file system has been modified.
  - After we dd the firmware file to extract the squashfs file system,
    we can attempt to run "unsquashfs"

`* ex. "unsquashfs xyz.squashfs`
`* If that does not work, we can try "unsquashfs_all"`
`* ex. "unsquashfs_all.sh xyz.bin"`
`* Assuming that works, you can view the file system at "fmk/rootfs"`
`* You can also simply run the extract-firmware.sh script under the fmk directory`

### Extracting and Running Binaries

  - We might want to see how identified binaries behave without running
    them on the device itself
  - One way to identify potentially interesting binaries is by examining
    the startup script from the device which we can discover by
    extracting the file system
  - QEMU emulation is also another way to examine binaries

### Extracting a jffs2 file system

  - Use the "unjffs2" batch file which is part of the firmware
    modification kit. "/firmware-mod-kit/src/jffs2/unjffs2"
  - You can also extract the jffs file using binwalk assuming Jefferson
    is installed (https://github.com/sviehb/jefferson)

### Extracting from a CPIO archive file

  - cpio -ivd --no-absolute-filenames -F {filename}

### Extracting from a UBI file system

  - Ensure Python Setuptools is installed for UBI Reader to install
    properly (sudo apt-get install python-setuptools)
  - Ensure UBI Reader is installed
    (https://github.com/jrspruitt/ubi_reader)
  - Run binwalk -e {filename}

### Mounting a .ext2 file

  - Create a mount directory (e.g. mkdir rootfs)
  - sudo mount -t ext2 {filename} rootfs

### Things to check for once the file system is mounted or extracted

  - "etc/passwd" and "etc/shadow"
  - "etc/ssl"
  - grep -rnw '/path/to/somewhere/' -e "pattern" like password, admin,
    root, etc.
  - find . -name '\*.conf' and other file types like \*.pem, \*.crt,
    \*.cfg, .sh, .bin, etc.
  - You can also run the Firmwalker script to search for these items in
    the extracted file system (https://github.com/craigz28/firmwalker)

### Dynamic testing of a web admin interface without the device

  - See the example video
    (https://craigsmith.net/episode-12-1-firmware-emulation-with-qemu/)