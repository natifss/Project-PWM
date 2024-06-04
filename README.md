#Trabalho para a disciplina de Sistemas Embarcados utilizando as saídas PMW do Arduíno

###1. Introdução ao PWM (#introdução-ao-pwm)

PWM, do inglês Pulse Width Modulation, é uma técnica utilizada por sistemas digitais para variação do valor médio de uma forma de onda periódica. A técnica consiste em manter a frequência de uma onda quadrada fixa e variar o tempo que o sinal fica em nível lógico alto. Esse tempo é chamado de duty cycle, ou seja, o ciclo ativo da forma de onda.

Analisando as formas de onda nota-se que a frequência da forma de onda tem o mesmo valor e varia-se o duty cycle da forma de onda. Quando o duty cicle está em 0% o valor médio da saída encontra-se em 0 V e consequentemente para um duty cycle de 100% a saída assume seu valor máximo, que no caso é 5V. Para um duty cycle de 50% a saída assumirá 50% do valor da tensão, 2,5 V e assim sucessivamente para cada variação no duty cycle.

![PWM-ARDUINO-01](https://github.com/natifss/Project-PWM/assets/119085630/9a994927-6d0c-4311-93da-0e896f60b1bd)

###2. Componentes necessários (#componentes-necessários)

Além da Placa PWM, outros componentes que podem ser necessários incluem:
```sh
- Microcontrolador: Para enviar os sinais PWM.
- Motores e LEDs: Dispositivos a serem controlados pela Placa PWM.
- Fontes de Alimentação: Para fornecer energia adequada ao sistema.
- Resistores e Capacitores: Para ajustes e filtragem de sinais.
- Cabos e Conectores: Para interconexão dos componentes.
```
###3. Esquemático (#esquemático)

![Captura de tela 2024-05-21 201325](https://github.com/natifss/Project-PWM/assets/119085630/b80ee193-96c6-432f-aafd-86a7ecc8a8e7)

![Captura de tela 2024-05-21 201131](https://github.com/natifss/Project-PWM/assets/119085630/415fab6c-7432-4a39-84a8-1a9caf1fd488)

![Captura de tela 2024-05-21 215708](https://github.com/natifss/Project-PWM/assets/119085630/664977d4-693f-4081-9bae-fd7fbbc76a06)

###4. Código-fonte (#código-fonte)
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
###5. Instruções de montagem (#instruções-de-montagem)

###6. Funcionamento do projeto (#funcionamento-do-projeto)
