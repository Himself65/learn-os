as=arm-none-eabi-as
ld=arm-none-eabi-ld
nm=arm-none-eabi-nm
objcopy=arm-none-eabi-objcopy
objdump=arm-none-eabi-objdump

all: add.o
	# -T use linker script
	@${ld} -T add.ld -o add.elf add.o
	${nm} add.elf
	@${objcopy} -O binary add.elf add.bin
	@${objdump} -C -d -S --no-show-raw-insn add.elf > add.lst

add.o:
	@${as} -o add.o add.S

flash:
	dd if=/dev/zero of=flash.bin bs=4096 count=4096
	dd if=add.bin of=flash.bin bs=4096 conv=notrunc

clean:
	@rm -f add.bin add.elf add.o
