## Projeto_CP1_Monitoramento_Luminosidade
Sistema de Monitoramento de Luminosidade desenvolvido para a Vinheria Agnello.

## 📌Descrição do Projeto

Este projeto implementa um sistema de monitoramento de luminosidade utilizando um sensor LDR conectado a um Arduino. A intensidade da luz ambiente é convertida em uma porcentagem (0% a 100%) e exibida em um display LCD 16x2.

Com base nessa leitura, o sistema classifica a luminosidade em três níveis:

*🟢 **OK**: iluminação ideal
*🟡 **Alerta**: fora da faixa ideal
*🔴 **Crítico**: iluminação inadequada

Cada estado é indicado por LEDs (verde, amarelo, vermelho) e, no caso crítico, também por um buzzer.

------

## ⚙️Dependências

* Biblioteca "LiquidCrystal" (já inclusa na IDE do Arduino)
* Arduino IDE

------

## ▶️Como Utilizar

1. Monte o circuito conectando:

   * LCD nos pinos digitais (12, 11, 10, 5, 4, 3, 2)
   * LEDs nos pinos 9 (verde), 8 (amarelo) e 7 (vermelho)
   * Buzzer no pino 6
   * LDR no pino analógico A0

2. Faça o upload do código para o Arduino.

3. Após iniciar:

   * O display mostrará uma tela de boas-vindas e a logo da nossa empresa (PRISMA)
   * Em seguida, exibirá a porcentagem de luminosidade e o status em tempo real

4. Observe os indicadores:

   * LED verde🟢 → iluminação adequada
   * LED amarelo🟡 → alerta
   * LED vermelho🔴 + buzzer → condição crítica

------

