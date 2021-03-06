Building the Mali Device Driver for Linux
-----------------------------------------

Build the Mali Device Driver for Linux by running the following make command:

KDIR=<kdir_path> USING_MMU=<mmu_option> USING_UMP=<ump_option> \
BUILD=<build_option> CONFIG=<your_config> make

where
    kdir_path: Path to your Linux Kernel directory
    mmu_option: 1 = Mali MMU(s) on
                0 = Mali MMU(s) off
    ump_option: 1 = Enable UMP support(*)
                0 = disable UMP support
    build_option: debug = debug build of driver
                  release = release build of driver
    your_config: Name of the sub-folder to find the required config.h(**) file
                 ("arch-" will be prepended)

(*)  For newer Linux Kernels, the Module.symvers file for the UMP device driver
     must be available. The UMP_SYMVERS_FILE variable in the Makefile should
     point to this file. This file is generated when the UMP driver is built.

(**) The config.h file contains the configuration parameters needed, like where the
     Mali GPU is located, interrupts it uses, memory and so on.

The result will be a mali.ko file, which can be loaded into the Linux kernel
by using the insmod command.
