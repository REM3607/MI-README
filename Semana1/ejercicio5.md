# CODIGO

.data
        message: .asciiz "\nMi NOMBRE ES:\n"
        message2: .asciiz "\nRandy E. Moran B\n"        

  .text
        main:
              li $v0, 4
              la $a0, message
              syscall
              li $v0, 4
              la $a0, message2
              syscall


# RESULTADO

.data
        message: .asciiz "\nMi NOMBRE ES:\n"
        message2: .asciiz "\nRandy E. Moran B\n"        

  .text
        main:
              li $v0, 4
              la $a0, message
              syscall
              li $v0, 4
              la $a0, message2
              syscall
