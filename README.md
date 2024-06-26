# Trabalho para a disciplina de Sistemas Embarcados utilizando as saídas PMW do Arduíno

### 1. Introdução ao PWM

PWM, do inglês Pulse Width Modulation, é uma técnica utilizada por sistemas digitais para variação do valor médio de uma forma de onda periódica. A técnica consiste em manter a frequência de uma onda quadrada fixa e variar o tempo que o sinal fica em nível lógico alto. Esse tempo é chamado de duty cycle, ou seja, o ciclo ativo da forma de onda.

Analisando as formas de onda nota-se que a frequência da forma de onda tem o mesmo valor e varia-se o duty cycle da forma de onda. Quando o duty cicle está em 0% o valor médio da saída encontra-se em 0 V e consequentemente para um duty cycle de 100% a saída assume seu valor máximo, que no caso é 5V. Para um duty cycle de 50% a saída assumirá 50% do valor da tensão, 2,5 V e assim sucessivamente para cada variação no duty cycle.

![PWM-ARDUINO-01](https://github.com/natifss/Project-PWM/assets/119085630/9a994927-6d0c-4311-93da-0e896f60b1bd)

### 2. Componentes necessários

Além da Placa PWM, outros componentes que podem ser necessários incluem:
```sh
- Microcontrolador: Para enviar os sinais PWM.
- Motores e LEDs: Dispositivos a serem controlados pela Placa PWM.
- Fontes de Alimentação: Para fornecer energia adequada ao sistema.
- Resistores e Capacitores: Para ajustes e filtragem de sinais.
- Cabos e Conectores: Para interconexão dos componentes.
```
### 3. Esquemático

![Captura de tela 2024-05-21 201325](https://github.com/natifss/Project-PWM/assets/119085630/b80ee193-96c6-432f-aafd-86a7ecc8a8e7)

![Captura de tela 2024-05-21 201131](https://github.com/natifss/Project-PWM/assets/119085630/415fab6c-7432-4a39-84a8-1a9caf1fd488)

![Captura de tela 2024-05-21 215708](https://github.com/natifss/Project-PWM/assets/119085630/664977d4-693f-4081-9bae-fd7fbbc76a06)

### 4. Código-fonte 
```sh
#include <Arduino.h>


const int motor = 9; 
const int button = 2;

int motorstate = LOW;
int buttonState = LOW;
int lastButtonState = LOW;

void setup() {
  pinMode(button, INPUT_PULLUP);
}

void loop() {

buttonState = digitalRead(button);
if(buttonState == HIGH && lastButtonState == LOW){
    motorstate++;
    if (motorstate == 0){
        analogWrite(9, 255);

    }else if (motorstate == 1){
        analogWrite(9, 191);

    }else if (motorstate == 2){
        analogWrite(9, 127);

    }else if (motorstate == 3){
        analogWrite(9, 64);

    }else if (motorstate == 4){
        analogWrite(9, 0);

    }else if (motorstate == 5){
        analogWrite(9, 255);
        motorstate = 0;
    }
}
lastButtonState = buttonState;
}
```
### 5. Instruções de montagem 

Para a motagem do circuito foi utilizado:
```sh
Arduino
Módulo Relé
Botão Push Button
Protoboard
Fios Jumper
Conexões
```
Botão:

Conectamos uma perna do botão ao pino 4 do Arduino e a outra no botão ao GND.

Relé:

Utilizado o pino IN do módulo relé ao pino 12 do Arduino, o pino VCC do módulo relé ao pino 5V do Arduino e o pino GND do módulo relé ao GND do Arduino.

Alimentação:

Fizemos a conexão do pino 5V do Arduino à linha de alimentação positiva (+) da protoboard e o pino GND do Arduino à linha de alimentação negativa (-) da protoboard.


Feito todas as conexões no proteus fizemos a parte de codigo no vcode. Progrado toda a lógica do funcioanento passamos o codigo ao Protues e fizemos o teste de funcionamento. Se ao apertarmos o botão o relé ficar ligado, e se apertarmos o botão novamente o relé ficar desligado.

### 6. Funcionamento do projeto 

Este projeto usa a funcionalidade PWM do Arduino para controlar um motor com um botão. O motor inicia desligado e conforme for apertando o botão ele incia e vai diminuindo a velocidade do motor até parar.
O código é composto por duas funções principais: setup() e loop(). A função setup() é executada uma vez quando o Arduino é ligado e configura o motor como saída. A função loop() executa continuamente, alternando a velocidade do motor com um sinal PWM
analogWrite(ledPin, 225); escreve um valor PWM de 128 (50% do ciclo de trabalho) no pino 9, fazendo com que o motor gire com sua intensidade máxima, e assim em diante.
