## A simple boot sector program that loops forever

```nasm
loop:
	jmp loop

times 510-($-$$) db 0

dw 0xAA55
```

- `loop:` Define a label, "loop", that will allow us to jump back to it, forever.

- `jmp loop` Use a simple CPU instruction that jumps to a new memory address to continue execution. In our case, jump to the address of the current instruction.

- `times 510-($-$$) db 0` When compiled, our program must fit into 512 bytes, with the last two bytes being the magic number, so here, tell our assembly compiler to pad out our program with enough zero bytes (db 0) to bring us to the 510th byte.

- `dw 0xAA55` Last two bytes (one word) from the magic number, so BIOS knows we are a boot sector.
