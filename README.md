# wload

## Description
ESXDOS dot command to upload machine code programs over the air from PC to wifi equiped ZXUNO.

## Usage
On the ZXUNO: `.wload`

On the PC: `nc <ip_address_of_zxuno_as_advertised_by_wload> 6912 < binary_file`

`nc` is the netcat program. Included in most Linux distros, and available also for OSX and Windows.

## Binary file format
Binary files must include a 16 bit value (little endian) containing the load address of the program, followed by a 16 bit value (little endian) with the execution entry point of the program, followed by the actual program

Such files can be generated by the PASMO assembler, this way:

                      org ORIGIN_OF_CODE

                      dw $
                      dw EntryPoint

                      bla bla bla
                      more bla bla bla

    EntryPoint:       beginning of execution
                      bla bla bla

                      end

Assemble with `pasmo --bin program.asm program.bin`
