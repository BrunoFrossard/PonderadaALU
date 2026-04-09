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

## CPU - Central Processing Unit

### O que é uma CPU?
A Unidade Central de Processamento é o componente fundamental de qualquer sistema computacional, e a sua função principal é processar dados através de um ciclo de decodificação e execução de instruções.

Seus componentes principais trabalham de forma síncrona para realizar cálculos e movimentar informações entre os registradores:
* **Unidade Lógica e Aritmética (ALU):** O núcleo onde os cálculos reais e operações lógicas acontecem.
* **Registradores (AC e MQ):** Memórias que armazenam resultados temporários para acesso imediato da ALU.
* **Unidade de Controle:** Responsável por interpretar o **Opcode** e definir qual caminho o dado deve seguir.

### Refatoração da ALU: Ajustes e Complementos
Durante o ciclo de desenvolvimento, a ALU passou por um processo de refatoração técnica. O projeto inicial apresentava conflitos de sinal que exigiram uma reestruturação profunda da arquitetura interna.

1.  **Eliminação de Conflitos de Drivers:** Túneis globais de entrada foram substituídos por conexões físicas. Isso garantiu que a ALU receba sinais apenas através de seus pinos de interface, eliminando o erro de mais de uma saída ativa causado por colisões de nomes no escopo global da CPU.
2.  **Estabilização do Subtrator:** O módulo de subtração foi ajustado para tratar corretamente o sinal de Borrow, evitando que o Carry Out da subtração entrasse em conflito com o Carry do somador.
3.  **Unificação de Controle:** Os seletores dos Multiplexadores foram recalibrados para operar em sincronia com o barramento do Opcode.

### Tabela de Operações (Opcodes)
| Opcode | Operação |
| :--- | :--- |
| `000` | **SOMA** | 
| `001` | **SUBTRAÇÃO** |
| `010` | **MULTIPLICAÇÃO** | 
| `011` | **DIVISÃO** | 
| `100` | **SHIFT LEFT** | 
| `101` | **SHIFT RIGHT** | 
| `110` | **NAND** | 
| `111` | **XOR** |

### Como Operar a CPU
1.  **Inicie a Simulação:** Clique no botão Play no simulador Digital.
2.  **Defina os Dados:** Insira o valor desejado na entrada `N`.
3.  **Escolha a Operação:** Ajuste o `Opcode` conforme a tabela acima.
4.  **Habilite o Sistema:** Ligue a chave `ENABLE`.
5.  **Execute o Ciclo:** Interaja com o componente de Clock para processar a instrução.

### Ferramenta utilizada
 
O projeto foi simulado utilizando o **Digital**, um simulador de circuitos lógicos open source.
 
[Digital — hneemann/Digital (GitHub)](https://github.com/hneemann/Digital)
