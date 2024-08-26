Sistema de Monitoramento Ambiental com ESP32
Este projeto consiste em um sistema de monitoramento ambiental utilizando dois ESP32, sensores de temperatura e umidade, servos motores e comunicação MQTT. O sistema é capaz de monitorar a temperatura e a umidade e acionar alarmes visuais e sonoros dependendo dos valores recebidos.

Componentes Utilizados
2x ESP32
1x Sensor DHT22 (Temperatura e Umidade)
2x Servo Motor
1x LED
1x Buzzer
2x Slide Switch
Conexão WiFi
Funcionamento Geral
ESP1
O primeiro ESP32 (ESP1) é responsável por:

Monitorar a temperatura e a umidade através do sensor DHT22.

Controlar dois servos motores:

O primeiro servo é ajustado em 50° quando a temperatura ultrapassa 60°C e retorna para 0° quando a temperatura está abaixo de 60°C.
O segundo servo é ajustado em 180° quando a temperatura ultrapassa 60°C e retorna para 0° quando a temperatura está abaixo de 60°C.
Publicar alertas de umidade via MQTT:

"Umidade baixa" é publicada quando a umidade é inferior a 20%.
"Umidade normal" é publicada quando a umidade é igual ou superior a 20%.
Ação baseada no Slide Switch:

Quando o slide switch está na posição 0, o sistema monitora e reage às condições ambientais.
Quando o slide switch está na posição 1, os servos retornam à posição 0° independentemente da temperatura.
ESP2
O segundo ESP32 (ESP2) é responsável por:

Receber mensagens MQTT sobre a umidade e acionar um alarme.
Quando a mensagem "Umidade baixa" é recebida, um alarme visual (LED) e sonoro (buzzer) é ativado.
Quando a mensagem "Umidade normal" é recebida, o alarme é desativado.
Ação baseada no Slide Switch:
Se o slide switch estiver na posição 0, o sistema ativa/desativa o alarme baseado nas mensagens recebidas.
Se o slide switch estiver na posição 1, o alarme é desativado, mesmo se "Umidade baixa" for recebida.
Como Rodar o Projeto
Desenvolvimento no Wokwi:

Este projeto foi desenvolvido e simulado no ambiente Wokwi, uma plataforma para simulação de projetos de eletrônica com ESP32.
Configuração do Ambiente de Desenvolvimento:

Caso deseje rodar o código em hardware real, utilize o Thonny para escrever e carregar os códigos nos ESP32.
Certifique-se de que as bibliotecas necessárias (como umqtt.simple e dht) estejam instaladas.
Carregar o Código:

Carregue o código esp1 no primeiro ESP32 e o código esp2 no segundo ESP32.
Conexão à Rede WiFi:

Ambos os ESP32 se conectam à rede WiFi configurada (Wokwi-GUEST).
Monitoramento e Ações:

Assim que os ESP32 estiverem conectados, o ESP1 começará a monitorar a temperatura e a umidade, enquanto o ESP2 aguarda mensagens MQTT para acionar ou desativar o alarme.
Considerações Finais
Certifique-se de que ambos os ESP32 estejam conectados à mesma rede WiFi para garantir a comunicação MQTT.
Verifique a posição dos slide switches antes de testar o sistema para garantir o comportamento esperado.
