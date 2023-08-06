# Yeah, Let's clone our drives without any 3rd party software
Linux is all about freedom for its users and here is yet another tutorial that will help you all out, especially if you're clumsy with your OS installations.
## Is it that easy?
For those who want to just get to it and know where to get the drive paths, here's the command:
```console
sudo dd if=path/to/source/drive of=/pth/to/target/drive conv=noerror,sync status=progress bs=100k
```

### Now for those who want to know what this command does,
Let's get at it from the beginning.

## What do you need?
1. Linux live boot USB
2. Source and target drive connected to the same machine
That's all


## Initializing in 3...2...
First of all, we'll launch our favourite utility in linux, the terminal. Once you've launched the terminal, run `sudo apt install dd` if you're on Ubuntu or `sudo pacman -S dd` for Arch linux.
Once this is done, you have the utility to clone your drive. Now just to make it interesting, we'll install another utility called `gparted`.

Run this in your terminal:
```console
sudo apt install gparted
```
OR 
```console
sudo pacman -S gparted
```
Just to verify, launch gparted either from the terminal or the app launcher. It should look something like this:
![gparted_home](/assets/gparted_home.png)
##
The drives attached can be seen by clicking the top right drop down menu
##
![gparted_dropdown](/assets/gparted_dropdown.png)

##
Now all the things required are installed. Let's get to work

## Identify your source and target drives
Before that, make sure the implicit things like target drive being atleast as big as the source drive are taken care of. Now once you're done with this, run in your terminal `sudo lsblk`. It should output something like this
![lsblk_out](/assets/lsblk_out.png)

This will give you a good idea of which drive you want to clone. Now suppose, I want to clone `nvme0n1`(238.5G) to `sdb`(465.8G), the question is, how?

## Here comes the flavour
Now let's get back to what `sudo dd if=path/to/source/drive of=/pth/to/target/drive conv=noerror,sync status=progress bs=100k` is doing. Also, I'll replace the paths with `/dev/nvme0n1` and `/dev/sdb` for source and target.
##
The `if` in the command stands for *input file* and `of` for *output file*. Yep you guessed it, we're guiding the command where it should copy _from_ and where it should copy _to_.
##
The `conv=noerror,sync` parameter in the command is used to control the behavior of the command when it encounters errors while reading or writing data.

`noerror`: With this option, the dd command will continue to copy data even if it encounters read errors. Without this option, dd would stop copying data when it encounters a read error.

`sync`: With this option, the dd command will pad any read errors with zeroes. This ensures that the block size is maintained and the image or backup file has consistent block sizes. Without this option, dd would fill the block with random data from the memory buffer.

So, using conv=noerror,sync in the dd command ensures that data is copied even if there are read errors and that the block size is maintained with consistent data.
`bs=100k`: For a layman, you can say that this controls the speed of copying the data. But technically speaking, when dd reads or writes data, it does so in blocks of the specified size. Using a larger block size can improve the performance of the dd command because it reduces the number of I/O operations required to copy the data. However, using too large a block size can also have negative effects, such as increasing the risk of errors and reducing performance if the block size is larger than the amount of data available to be copied.

## But how do I clone my OS installation??
I think the tutorial has been tiring already, in any case, I keep my promises. The 2nd part is in the folder named `clone-my-os`. gparted, installed previously is kind of the GUI for disk and partition management and comes in handy for OS cloning. The tutorial is there for anyone to see!!


