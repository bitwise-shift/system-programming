#### How to build binary for Raspberry PI 2:

1. You need to install assembler tools:

```bash

````

2. Build source code into the binary ELF-file for bare metal

```bash
arm-none-eabi-as -mcpu=cortex-a7 source/main.s -o main.o  
arm-none-eabi-ld -Ttext 0x8000 main.o -o main.elf
arm-none-eabi-objcopy main.elf -O binary kernel7.img
```

3. Copy kernel7.img to your SD card, put it into your Raspberry PI and power on. You should see the gradient pattern onto your screen.

#### Disassembling

```bash
arm-none-eabi-objdump -b binary -m arm --adjust-vma=0x8000 -D kernel7.img | head -45
```

