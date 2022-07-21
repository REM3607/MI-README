# Create a program that adds any two given numbers provided by the user

# CODIGO 

.data

	      number1: .asciiz "\nIngrese el primer numero: "
        
	      number2: .asciiz "\nIngrese el segundo numero: "
        
	      message: .asciiz "\Primer Numero Ingresado ES:\n"
        
        message2: .asciiz "\nSegundo Numero Ingresado ES\n" 
              


  .text
  
	      main:
        
              li $v0, 4
              
              la $a0, number1
              
              syscall
              

              li $v0, 5
              
              syscall
              

              move $t0, $v0
              

              li $v0, 4
              
              la $a0, number2
              
              syscall
              

              li $v0, 5
              
              syscall
              

              move $t1, $v0
              

              li $v0, 4
              
              la $a0, message
              
              syscall
              
              
              li $v0, 1
              
              move $a0, $t0
              
              syscall
              
              li $v0, 4
              
              la $a0, message2
              
              syscall
              
              
              li $v0, 1
              
              move $a0, $t1
              
              syscall
              

# RESULTADO


Ingrese el primer numero: 3 

Ingrese el segundo numero: 2

Primer Numero Ingresado ES:
3

Segundo Numero Ingresado ES
2
-- program is finished running (dropped off bottom) --
