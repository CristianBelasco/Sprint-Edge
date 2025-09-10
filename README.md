# Sprint-Edge
# grupo:
Cristian Belasco Arancibia - RM565710
João Lucas Ferreira dos Santos - RM562608
Felipe Yamaguchi Mesquita - RM556170
Samuel de Oliveira da Silva - RM566245
Rafael Felix - RM565855

# Link projeto:
https://wokwi.com/projects/441663235442064385

# 📝 Descrição Geral do Projeto:

Este projeto utiliza um ESP32 conectado a sensores e LEDs para monitorar uma mini-partida de futebol (ou treino) e enviar informações em tempo real via MQTT para um servidor. Ele mede número de passes, jogador ativo, distância de objetos (bola ou jogador) e condições climáticas (temperatura e umidade). O sistema aciona LEDs de sinalização de acordo com o número de passes (verde, amarelo ou vermelho) e publica todos os dados em tópicos separados no broker MQTT.

Resumo:
Sensores → Captam distância, temperatura e umidade.
ESP32 → Processa os dados, conta passes, alterna jogador e decide o LED correto.
MQTT → Envia informações para monitoramento remoto em tempo real.
LEDs → Informam visualmente a situação do jogo (poucos passes = verde, intermediário = amarelo, muitos passes = vermelho).

# Arquitetura Proposta:
A arquitetura pode ser vista como um sistema IoT simples:
Camada de Sensores:
  Sensor Ultrassônico (HC-SR04 ou similar): mede distância para detectar passagem da bola/jogador.
  DHT22: mede temperatura e umidade do ambiente.
Camada de Processamento (ESP32):
  Recebe dados dos sensores.
  Processa o estado atual (passagem detectada, contagem de passes, troca de jogador).
  Decide o acionamento dos LEDs.
  Publica dados no broker MQTT.
Camada de Comunicação (MQTT):
  Broker (ex.: test.mosquitto.org) recebe os dados.
  Possibilidade de outros dispositivos ou dashboards (Node-RED, Home Assistant, App customizado) se inscreverem nos tópicos para visualização em tempo real.
Camada de Atuação (Feedback Visual):
  LEDs sinalizam status do jogo localmente.
  Possibilidade de controle remoto do LED verde via MQTT (exemplo implementado no callback).

# Recursos Necessários:
ESP32
Sensor DHT22
Sensor Ultrassônico HC-SR04
3 Leds
Jumpers
Protoboard
