# Resultados: Modificação da Antena (Baseline vs. 1/4 de Onda)

Este documento apresenta a análise comparativa de desempenho de radiofrequência (RF) na faixa de 2,4 GHz, validando a modificação de hardware realizada no microcontrolador ESP32.

## 🛠️ A Modificação de Hardware

A antena original integrada à placa (_PCB Trace Antenna_) foi isolada fisicamente através da interrupção de sua trilha logo após o estágio de casamento de impedância. Em seu lugar, foi implementada uma antena externa do tipo **Monopolo de 1/4 de onda**.

- **Frequência Alvo:** 2.4 GHz
- **Comprimento de Onda ($\lambda$):** ~ 12,5 cm
- **Elemento Ativo ($\lambda/4$):** Fio de cobre exposto dimensionado para exatos **3,1 cm**.
- **Plano de Terra:** Malha do cabo coaxial soldada aos _pads_ de GND, utilizando o próprio plano de terra da placa como contrapeso.

## 📊 Análise Comparativa (Dados de Telemetria)

Os testes foram conduzidos utilizando o sistema de _Site Survey_ desenvolvido neste projeto. Foi selecionada uma rede alvo constante para medir o comportamento do RSSI (Intensidade do Sinal) e a estabilidade da recepção.

| Métrica Analisada            | Antena Original (PCB)                 | Antena Modificada (1/4 Onda)       | Impacto / Resultado                       |
| :--------------------------- | :------------------------------------ | :--------------------------------- | :---------------------------------------- |
| **Intensidade Média (RSSI)** | ~ -39 dBm a -43 dBm                   | ~ -25 dBm a -30 dBm                | **Ganho expressivo de ~ 11 dBm**          |
| **Estabilidade de Sinal**    | Alta flutuação (_fading_ severo)      | Curva de propagação plana          | **Casamento de impedância validado**      |
| **Confiabilidade (Pacotes)** | Perda de _beacons_ (linhas quebradas) | Leituras contínuas e ininterruptas | **Melhoria na Relação Sinal-Ruído (SNR)** |

### 1. Ganho Absoluto de Potência

A substituição da antena resultou em um ganho prático de aproximadamente **11 dBm**. Devido à natureza logarítmica da escala de decibéis em RF, um aumento de 10 dB representa que o estágio receptor do ESP32 passou a captar um sinal com potência cerca de **10 vezes maior** em comparação à antena original.

### 2. Estabilidade e Imunidade a Ruído

Os logs visuais do _Dashboard_ evidenciaram que a antena de trilha original sofria intensa atenuação pelo próprio substrato dielétrico (FR4) da placa, resultando em quedas bruscas de sinal. O elemento irradiante externo eliminou essas perdas resistivas, proporcionando uma propagação estável e constante no ar.

### 3. Sensibilidade de Descoberta

O sistema modificado demonstrou maior precisão na leitura contínua de redes mais distantes e fracas (abaixo de -75 dBm), eliminando a perda de pacotes de dados que ocorria no hardware de fábrica em ambientes saturados.

## 🎯 Conclusão

A aplicação do dimensionamento físico de antenas provou-se altamente eficaz na prática. A modificação para um monopolo de 1/4 de onda de 3,1 cm não apenas amplificou o alcance de recepção do ESP32, mas entregou um fluxo de dados de telemetria altamente confiável, comprovando a eficácia da teoria eletromagnética aplicada ao desenvolvimento de hardware.
