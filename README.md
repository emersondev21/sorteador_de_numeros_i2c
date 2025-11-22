# sorteador_de_numeros_i2c
## Sorteador de números aleatórios entre 00 e 99 através da plataforma Arduino Uno, utilizando Display LCD.

### 🎲 Gerador de Número Aleatório com LCD I2C e Interrupções Externas

Projeto utilizando Arduino Uno, display LCD I2C, interrupções externas (INT0 e INT1) e manipulação direta de registradores.

### 📘 Descrição do Projeto

Este projeto implementa um sistema que gera um número aleatório entre 00 e 99 sempre que um botão conectado à interrupção externa INT0 é acionado.
O número é exibido em um display LCD I2C 16x2, e toda a configuração de pinos é feita utilizando registradores de I/O, sem pinMode(), digitalRead(), etc.

Também são habilitadas duas interrupções externas (INT0 e INT1), usando manipulação direta dos registradores EICRA e EIMSK.

### 🧩 Componentes Utilizados

Arduino Uno (ATmega328P)

Display LCD 16x2 com módulo I2C (PCF8574 – endereço 0x27 ou 0x3F)

Botão para interrupção externa (INT0)

Jumpers macho–macho

Fonte de 5V do Arduino

### 🔌 Ligações
LCD I2C
LCD	Arduino Uno
VCC	5V
GND	GND
SDA	A4
SCL	A5
Botão (Interrupção INT0)

Um terminal → D2 (INT0)

Outro terminal → GND

O botão funciona com o pull-up interno ativado. Não é necessário resistor externo.

<img width="720" height="318" alt="image" src="https://github.com/user-attachments/assets/2855054d-3bf1-48cb-b942-b194702d0a03" />

### ⚙️ Funcionamento

Ao ligar o Arduino, o LCD exibe uma mensagem inicial.

Quando o botão conectado ao pino D2 é pressionado, a interrupção INT0 dispara.

A interrupção altera a flag novoNumero.

No loop(), quando essa flag é detectada, o Arduino:

Gera um número aleatório (0–99)

Atualiza o display LCD com o valor sorteado

### 🧠 Recursos Utilizados
✔ Manipulação direta de registradores

* DDRB: configurado manualmente (pinos PB0–PB5 como saída)

* EICRA: define o tipo de detecção das interrupções

* EIMSK: habilita INT0 e INT1

* sei(): habilita interrupções globais

✔ Interrupções externas (INT0 e INT1)

Configuradas para detectar borda de subida (ISCx1 = 1 e ISCx0 = 1).

✔ LCD I2C

Controlado pela biblioteca LiquidCrystal_I2C.h.
