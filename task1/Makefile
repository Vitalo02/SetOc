all: Lec2 Lec3 Lec4

Lec2: Prog1

Lec3: Prog2 Prog3

Lec4: Prog4 Prog5 Prog6

Prog1:
	gcc 'Lec2/Prog1/Prog1.c' -o 'Lec2/Prog1/Prog1.out'

Prog2:
	gcc 'Lec3/Prog2/Prog2.c' -o 'Lec3/Prog2/Prog2.out'

Prog3:
	gcc 'Lec3/Prog3/Prog3.c' -o 'Lec3/Prog3/Prog3.out'

Prog4:
	gcc 'Lec4/Prog4/Prog4.c' -o 'Lec4/Prog4/Prog4.out'

Prog5:
	gcc 'Lec4/Prog5/Prog5.c' -o 'Lec4/Prog5/Prog5.out'

Prog6:
	gcc 'Lec4/Prog6/Prog6.c' -o 'Lec4/Prog6/Prog6.out'

clear:
	rm -rf Lec?/Prog*/*.out
