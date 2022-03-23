////////////////////      1ST LAB ////////////////////////////


ASSEMLER CODE

.CSEG
call main


; array

.SET array_size = 32

.DSEG
array: .byte array_size

.CSEG
array_pgm:
	.DB 3, 20, 54, 254, 122, 54, 171, 101, 10, 155, 53, 219, 43, 187, 132, 98, 189, 123, 10, 207, 66, 52, 38, 29, 10, 155, 53, 219, 43, 187, 132, 255
	
;;;;;;;;;

; arr_out

.DSEG
arr_out: .byte array_size

;;;;;;;;;


.CSEG
main:
	; Z = &array_pgm
	ldi r31, high(array_pgm * 2)  
	ldi r30, low(array_pgm * 2)

	; Y = &array
	ldi r29, high(array)      
	ldi r28, low(array)

	; X = &array + size
	ldi r26, low(array + array_size)    
	ldi r27, high(array + array_size)
	
	docopy:

		; *(array++) = *(array_pgm++)
		lpm  r23, Z+      
		st   Y+, r23
		
		; while (Y < X)
		cp   r28, r26   
		cpc  r29, r27
		brlo docopy


	; Y = &array
	ldi r29, high(array)  
	ldi r28, low(array)

	; min = 255
	ldi r24, 255           

	find_min:
		ld  r23, Y+
		
		; if r24 > r23
		cp   r24, r23
		brlo skip_min
		mov  r24, r23
	skip_min: 

		; while (Y < X)
		cp   r28, r26   
		cpc  r29, r27
		brlo find_min   
		

	
	; num < min -> never because always min <= num
	; num >= min  ->  5 <= (num - min) <= 10  ->  0 <= (num - (min + 5)) <= 5
	; min - (-5) == min + 5
	subi r24, 256 - 5
	; val = 5
	ldi r22, 5
	
	; Y = &array
	ldi r29, high(array)  
	ldi r28, low(array)
	
	; Z = &arr_out + 1
	ldi r31, high(arr_out + 1)  
	ldi r30, low(arr_out + 1)

	find_numbers:
		ld   r23, Y+
		
		; diff = (num - min - 5)
		mov r25, r23
		sub r25, r24
		
		; if (num - min - 5) <= 5
		cp   r25, r22
		brsh abs1
		st   Z+, r23
	abs1:

		; while (Y < X)
		cp   r28, r26   
		cpc  r29, r27
		brlo find_numbers
	
	; X = &arr_out + 1
	ldi r27, high(arr_out + 1)  
	ldi r26, low(arr_out + 1)

	; Z -= X
	sub r30, r26

	; *X = Z
	st  -X, r30
	
	rjmp PC
  
  
 ////////////////////////////////// 2ND LAB //////////////////////////////////////////////
 
 ASSEMBLER CODE
 
 
.CSEG
call main




main:
	; F = A * (B + 4) + (C – 3) / 2 * (D + 2)
	.SET A = 5
	.SET B = 7
	.SET C = 10
	.SET D = 15

	ldi  r16, A
	ldi  r17, B
	ldi  r18, C
	ldi  r19, D


	; B = B + 4
	subi r17, 256 - 4

	; C = C - 3
	subi r18, 3

	; D = D + 4
	subi r19, 256 - 2

	; A = A * B
	push  r16
	push  r17
	rcall mul8_add
	pop  r16
	
	; C = C / 2
	push  r18
	ldi   r20, 2
	push  r20
	rcall div8_sub
	pop   r18

	; C = C * D
	push  r18
	push  r19
	rcall mul8_add
	pop   r18

	; A = A + C
	add   r16, r18

	; PORTD = A
	out   11, r16

	
	rjmp PC



; using r0, r1, r24, r25, r26
mul8_add:
	pop  r0
	pop  r1

	pop  r24
	pop  r25
	; push r26
	ldi  r26, 0
	
	; if r24 >= r25
	cp   r24, r25
	brlo mul8_add_loop
	
	; r24, r25 = r25, r24
	push r24
	mov  r24, r25
	pop  r25

mul8_add_loop:
	add  r26, r25
	subi r24, 1
	brne mul8_add_loop
	
	; mov  r25, r26
	; pop  r26
	; push r25
	push r26
	
	push r1
	push r0
	ret


	
; using r0, r1, r24, r25, r26
div8_sub:
	pop  r0
	pop  r1

	pop  r24
	pop  r25
	
	; push r26
	ldi  r26, 0
	
div8_sub_loop:
	inc  r26
	sub  r25, r24
	brsh div8_sub_loop
		
	; mov  r25, r26
	; pop  r26
	; dec  r25
	; push r25
	dec  r26
	push r26

	push r1
	push r0
	ret
 
 ////////////////////////////////// 3RD LAB //////////////////////////////////////////////
 
 
 
 C++ CODE
 
 #include <inttypes.h>
#include <avr/io.h>


int main() {
	volatile uint8_t _seq[] = {216, 16, 66, 6, 6, 3, 0};
	uint8_t *sequence = (uint8_t*)_seq;

	uint8_t unique = 0;
	uint8_t count = 0;
	uint8_t pairs = 0;
	uint8_t size = 0;
	uint8_t i;
	uint8_t si;
	uint8_t buf[20];

	while (sequence[size] != 0)
	size++;

	for (i = 0; i < size; i++) {
		for (si = 0; si < unique; si++) {
			if (sequence[i] == buf[si]) {
				si = 255;
				break;
			}
		}
		if (si != 255) {
			buf[unique] = sequence[i];
			unique++;
		}
	}

	PORTD = unique;

	
	for (i = 0; i < unique; i++) {
		count = 0;
		for (si = 0; si < size; si++) {
			if (buf[i] == sequence[si])
				count++;
		}
		if (count == 2)
			pairs++;
	}
	
	PORTD = pairs;

	return 0;
}
