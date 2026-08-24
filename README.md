# DOM-0S
Operating system built from scratch with C

## PROGRESS IN PICS
### BOOT
![boot](./screenshots/boot.png)
<br>
<br>

### KERNEL
![kernel](./screenshots/kernel.png)
<br>
<br>

### OUTPUT
![output](./screenshots/output.png)
<br>
<br>

### CREATING PANIC
![panic](./screenshots/creating_panic.png)
<br>
<br>

### EXCEPTION HANDLING
![exception](./screenshots/exception_handling.png)
<br>
<br>

### MEMORY ALLOCATION
![memory](./screenshots/memory_allocation.png)
<br>
<br>

### PROCESS/CONTEXT SWITCHING
![process](./screenshots/process.png)
<br>
<br>

### PAGE TABLE
#### REGISTER INFO
![register](./screenshots/page_table_register_info.png)

#### ACTUAL PAGE TABLE
![page table](./screenshots/actual_page_table.png)
<br>
<br>

### APPLICATION
![application](./screenshots/application.png)
<br>
<br>

### USER MODE
![user mode1](./screenshots/user_mode.png)

![user mode2](./screenshots/user_mode2.png)
<br>
<br>

### SYSTEM CALL
![syscall](./screenshots/sys_call.png)

#### SENDING COMMANDS TO SHELL
![commmands to shell](./screenshots/syscall2.png)
<br>
<br>

### DISK IO (READING FROM AND WRITING TO A DISK)
![disk IO](./screenshots/disk.png)
<br>
<br>

### FILE SYSTEM
![file system](./screenshots/file_system.png)

#### READING FROM AND WRITING TO FILES
![file system2](./screenshots/file_system2.png)
<br>
<br>

## CHALLENGES
### BOOT SECTION
**PROBLEM** 

./run.sh failed with

```console
qemu-system-riscv32: Unable to find the RISC-V BIOS "opensbi-riscv32-generic-fw_dynamic.bin"

```

**CAUSE** 

Ubuntu/Zorin's opensbi apt package only ships riscv64 firmware **(/usr/lib/riscv64-linux-gnu/opensbi/generic/fw_dynamic.bin)**, not riscv32.
 
**qemu-system-riscv32's -bios default** needs a 32-bit firmware binary, which doesn't exist anywhere on a stock Ubuntu/Zorin install.

**FIX**

 Downloaded the prebuilt 32-bit OpenSBI firmware directly from QEMU's own upstream repo, placing it in QEMU's default data search path (**/usr/share/qemu**, found via **qemu-system-riscv32 -L help**):

 ```bash
 sudo wget -O /usr/share/qemu/opensbi-riscv32-generic-fw_dynamic.bin \
  https://github.com/qemu/qemu/raw/master/pc-bios/opensbi-riscv32-generic-fw_dynamic.bin
 ```

 This let **-bios default** resolve correctly without modifying **run.sh** or any guide-provided files.
<br>
<br>
<br>

**DEVELOPED WITH ZORIN OS 18.1**
