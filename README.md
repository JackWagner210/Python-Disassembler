# Python-Disassembler
ARM LegV8 disassembler written in python.

Given a .txt file of 32bit ARM machine code, produces a formated file with a seperated binary, address number, and assembly instuctions.

Ex input:
10001011000000100000000000100011
11001011000000100000000000100011
10001010000000100000000000100011
10101010000000100000000000100011
00010111111111111101100011110000
10010001000001100100000001000001
11010001000001100100000001000001
11111000010001100100000001000001
11111000000001100100000001000001
10110100111111111111111110110011
10110101000000000000000001110011
11010010100000000001111111100001
11110010111111111110000000000010
11010011010000000001000000100000
11010011011000000001000000100000
11111110110111101111111111100111
11111111111111111111111111111111
11111111111111111111111111111110
11111111111111111111111111111101

Ex output:

10001011000 00010 000000 00001 00011	96	ADD	R3, R1, R2
11001011000 00010 000000 00001 00011	100	SUB	R3, R1, R2
10001010000 00010 000000 00001 00011	104	AND	R3, R1, R2
10101010000 00010 000000 00001 00011	108	ORR	R3, R1, R2
000101 11111111111101100011110000   	112	B	#-10000
1001000100 000110010000 00010 00001 	116	ADDI	R1, R2, #400
1101000100 000110010000 00010 00001 	120	SUBI	R1, R2, #400
11111000010 001100100 00 00010 00001	124	LDUR	R1, [R2, #100]
11111000000 001100100 00 00010 00001	128	STUR	R1, [R2, #100]
10110100 1111111111111111101 10011  	132	CBZ	R19, #-3
10110101 0000000000000000011 10011  	136	CBNZ	R19, #3
110100101 00 0000000011111111 00001 	140	MOVZ	R1, 255, LSL 0
111100101 11 1111111100000000 00010 	144	MOVK	R2, 65280, LSL 48
11010011010 00000 000100 00001 00000	148	LSR	R0, R1, #4
11010011011 00000 000100 00001 00000	152	LSL	R0, R1, #4
11111110 110 11110 11111 11111 100111	156	BREAK
11111111111111111111111111111111    	160	-1
11111111111111111111111111111110	    164	-2
11111111111111111111111111111101	    168	-3
