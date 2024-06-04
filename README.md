# Sistemas-Embarcados-PWM

## Introdução ao PWM

PWM (Modulação por Largura de Pulso) é uma técnica eficiente para controlar a quantidade de energia entregue a uma carga. É amplamente utilizada em aplicações como controle de motores, iluminação LED e fontes de alimentação comutadas.

### Conceito Básico

- **Ciclo de Trabalho (Duty Cycle)**: Percentual do tempo em que o sinal está em nível alto dentro de um ciclo. Varia de 0% (sempre baixo) a 100% (sempre alto).
- **Frequência**: Número de ciclos por segundo (Hz). Frequências mais altas permitem controle mais suave.

### Aplicações Comuns

- **Controle de Motores**: Ajusta a velocidade do motor DC variando o ciclo de trabalho do sinal PWM.
- **Controle de Brilho de LEDs**: Modula o brilho dos LEDs ajustando o ciclo de trabalho.
- **Fontes de Alimentação Comutadas**: Regula a tensão de saída controlando o tempo em que os transistores estão ligados/desligados.

### Vantagens

- **Eficiência Energética**: Minimiza a dissipação de energia.
- **Flexibilidade**: Fácil implementação em microcontroladores.
- **Controle Preciso**: Permite controle preciso da potência entregue à carga.

PWM é uma técnica versátil e eficiente para o controle de dispositivos eletrônicos, melhorando o desempenho e a eficiência dos sistemas.

## Componentes Básicos

### CELL

O processador CELL, oficialmente denominado Cell Broadband Engine Architecture (CBEA), é um microprocessador desenvolvido por Sony, Toshiba e IBM (STI). Lançado em 2005, o CELL foi criado para oferecer alto desempenho em tarefas de computação intensiva, incluindo gráficos, jogos e processamento multimídia.

### L293D

O L293D é um driver de ponte H amplamente utilizado em projetos eletrônicos para controlar motores DC e motores de passo. Esse circuito integrado possibilita que microcontroladores e outras fontes de controle de baixa potência operem motores de maior potência de forma eficiente e segura.

### Motor

Motores DC (corrente contínua) e motores de passo são amplamente empregados em projetos de eletrônica e robótica. Combinados com controladores como o Arduino Nano e drivers como o L293D, esses motores possibilitam a criação de sistemas de movimento precisos e eficientes.

## Esquemático

![Esquemático](https://github.com/IanSiqueira/Sistemas-Embarcados-PWM/assets/101524235/2ead4243-7ad7-4b8a-823d-28e80cad9cd4)

## Código Fonte

```cpp
#include <Arduino.h>

const int button = 4;
int buttonState = LOW;
int lastButtonState = LOW;
int qtdeClick = 0;

void setup() {
  pinMode(button, INPUT_PULLUP);
}

void loop() {
  buttonState = digitalRead(button);
  if (lastButtonState == LOW && buttonState == HIGH) {
    qtdeClick++;
    if (qtdeClick == 0) {
      analogWrite(9, 255);
    } else if (qtdeClick == 1) {
      analogWrite(9, 191);
    } else if (qtdeClick == 2) {
      analogWrite(9, 127);
    } else if (qtdeClick == 3) {
      analogWrite(9, 64);
    } else if (qtdeClick == 4) {
      analogWrite(9, 0);
    } else if (qtdeClick == 5) {
      analogWrite(9, 255);
      qtdeClick = 0;
    }
  }
  lastButtonState = buttonState;
}

```

## Funcionamento do Projeto

O projeto visa definir a frequência do motor com base no botão sendo apertado, alterando os valores da frequência e seus usos. Um osciloscópio é utilizado para medir as oscilações entre frequências e assim modificar as velocidades do motor.
