##  O que é este projeto?
 
Este projeto consiste na implementação de uma **ALU (Arithmetic Logic Unit) de 8 bits**, ou seja, uma Unidade Lógica e Aritmética — o componente responsável por realizar operações matemáticas e lógicas dentro de um processador.
 
A ALU foi construída com circuitos digitais simulados, utilizando registradores e operadores combinacionais para executar as operações sobre os operandos de entrada.
 
## Vídeo de apresentação
 
[![Apresentação da ALU 8 bits](https://img.youtube.com/vi/yHM74tY_DT0/0.jpg)](https://youtu.be/yHM74tY_DT0?si=h8oGRS5MU-F7qX_-)
 
> Clique na imagem acima para assistir à apresentação completa no YouTube.
 
## Componentes
 
A ALU é composta por:
 
- **N** — operando de entrada da ALU (8 bits)
- **AC (Acumulador)** — registrador principal, armazena o primeiro operando e recebe o resultado das operações
- **MQ (Multiplier/Quotient)** — registrador auxiliar, usado para armazenar os bits mais significativos da multiplicação e o quociente da divisão
 
## Operações implementadas
 
| Operação | Operandos | Saída |
|---|---|---|
| **Soma** | AC + N | AC (8 bits) |
| **Subtração** | AC - N | AC (8 bits) |
| **Multiplicação** | AC × N | AC (8 LSB) + MQ (8 MSB) |
| **Divisão** | AC ÷ N | AC (Resto) + MQ (Quociente) |
| **Shift lógico à esquerda** | AC | AC (8 bits) |
| **Shift lógico à direita** | AC | AC (8 bits) |
 
> **LSB** = Less Significant Bits (bits menos significativos)  
> **MSB** = Most Significant Bits (bits mais significativos)
 
## Como cada operação funciona
 
### Soma
Realiza a adição entre o registrador acumulador (AC) e o operando de entrada (N). O resultado é armazenado de volta no AC.
 
### Subtração
Realiza a subtração de N a partir do valor contido em AC. O resultado é armazenado no AC.
 
### Multiplicação
Multiplica AC por N. Como o resultado de uma multiplicação de 8 bits pode ter até 16 bits, os 8 bits menos significativos (LSB) ficam no AC e os 8 bits mais significativos (MSB) ficam no MQ.
 
### Divisão
Divide AC por N. O quociente é armazenado em MQ e o resto da divisão fica em AC.
 
### Shift lógico à esquerda
Desloca todos os bits do AC uma posição para a esquerda. O bit mais à esquerda é descartado e um `0` é inserido à direita. Equivale a multiplicar o valor por 2.
 
### Shift lógico à direita
Desloca todos os bits do AC uma posição para a direita. O bit mais à direita é descartado e um `0` é inserido à esquerda. Equivale a dividir o valor por 2.
 
## Ferramenta utilizada
 
O projeto foi simulado utilizando o **Digital**, um simulador de circuitos lógicos open source.
 
[Digital — hneemann/Digital (GitHub)](https://github.com/hneemann/Digital)
