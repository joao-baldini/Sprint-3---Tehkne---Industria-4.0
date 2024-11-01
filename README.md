# Sistema de Monitoramento Inteligente - John Deere

## Introdução
O projeto visa resolver os principais desafios de rastreamento e gerenciamento de carrinhos de transporte na fábrica da John Deere, utilizando o ESP32 e triangulação de Wi-Fi para coletar dados de localização em tempo real. A implementação do Sistema de Monitoramento Inteligente tem como foco otimizar a eficiência operacional, melhorar a gestão de recursos e aumentar a segurança.

## Objetivos
1. **Integrar Dados em Tempo Real**: Conectar dispositivos ESP32 para rastrear os carrinhos de transporte por meio de triangulação de Wi-Fi.
2. **Aumentar a Eficiência Operacional**: Otimizar a movimentação dos carrinhos e reduzir o tempo de localização.
3. **Melhorar a Gestão de Recursos**: Utilizar os dados de localização para uma alocação mais eficiente.
4. **Elevar a Segurança Operacional**: Monitorar zonas de risco e prevenir acidentes.
5. **Facilitar a Tomada de Decisões**: Implementar uma interface administrativa para análises detalhadas e estratégicas, desenvolvida em Streamlit.

## Desenvolvimento

### Arquitetura do Sistema
A solução foi desenvolvida com os seguintes componentes principais:
1. **Mapeamento da Área de Operação**: Delimitação das áreas de alto tráfego e zonas de espera.
2. **Infraestrutura de Rastreamento**: Utilização de ESP32 e triangulação de Wi-Fi para rastrear os carrinhos em tempo real.
3. **Desenvolvimento do Software de Monitoramento**: Visualização centralizada dos dados coletados e alertas de proximidade.

![Diagrama_sem_nome](https://github.com/user-attachments/assets/d803cd81-e19e-48e0-a0cf-dd7ee77ffead)
![Diagrama_sem_nome_1](https://github.com/user-attachments/assets/857c384d-ede3-43b2-b423-a4d12430a60c)

## Resultados

Estamos desenvolvendo um Sistema de Monitoramento Inteligente para a John Deere, com foco no rastreamento de carrinhos de transporte dentro das instalações da fábrica. O projeto utiliza ESP32 para coletar dados de localização via triangulação Wi-Fi, fornecendo atualizações em tempo real sobre a posição dos carrinhos. Esses dados são processados e armazenados em um banco de dados SQLite, permitindo visualização e controle através de uma interface web interativa desenvolvida com Streamlit, que serve tanto para o backend quanto para o frontend.

O sistema possui uma sessão de cadastro e login para controle de acesso, diferenciando operadores e administradores. Os operadores podem monitorar os carrinhos em um mapa interativo, que exibe a localização precisa dos ESP32 acoplados aos carrinhos, enquanto os administradores têm acesso a um painel para análise avançada, facilitando a tomada de decisões estratégicas.

Além de otimizar a eficiência operacional, o sistema visa melhorar a segurança ao monitorar áreas de risco e trajetos de alto tráfego, contribuindo para uma melhor gestão de recursos e redução de custos. Esse projeto se alinha à visão da John Deere de incorporar tecnologias de ponta e soluções IoT, posicionando a empresa na vanguarda da Indústria 4.0.

### Vídeo do funcionamento

- https://youtu.be/XP4SES_xFI0

## Testes de Desempenho 

### Definição da Ferramenta de Teste
No teste de estabilidade de sinal o objetivo principal é verificar a consistência das leituras de RSSI (Received Signal Strength Indicator) ao longo do tempo e como essa estabilidade afeta a precisão da localização do ESP32 através da triangulação.
Passos do Teste de Estabilidade de Sinal:
⦁	Posicionamento dos Roteadores:
⦁	Os roteadores são dispostos em formato quadrado, com cada um em uma posição fixa e conhecida, formando os vértices de uma área de cobertura quadrada.
⦁	Cada roteador possui um SSID (identificação de rede) único para facilitar a identificação e o mapeamento de cada ponto no processo de medição.
⦁	Coleta de RSSI pelo ESP32:
⦁	O ESP32 realiza leituras de RSSI para cada um dos quatro roteadores. O RSSI é uma medida da intensidade do sinal recebido, que diminui com a distância. Leituras de RSSI mais fortes (valores maiores) indicam que o ESP32 está mais próximo do roteador, enquanto valores mais baixos indicam maior distância.
⦁	No teste de estabilidade, várias leituras de RSSI são coletadas em um período contínuo ou intervalos específicos para cada roteador, verificando se os valores de RSSI permanecem consistentes.
⦁	Avaliação da Estabilidade do Sinal:
⦁	A estabilidade do sinal é avaliada pela variação nos valores de RSSI. Caso o RSSI de um roteador varie muito em leituras consecutivas, isso indica que o sinal é instável, o que pode ser causado por fatores ambientais, interferências de outros dispositivos, obstáculos no ambiente, entre outros.
⦁	A estabilidade também pode ser analisada observando a consistência das coordenadas estimadas ao longo do tempo. Se a posição estimada do ESP32 varia significativamente, mesmo quando o dispositivo está parado, isso indica uma instabilidade na medição do RSSI.

### Evidências de Testes
Código usado para teste: 
#include <WiFi.h>
// Defina os SSIDs dos roteadores que você quer monitorar
const char* ssid1 = "TBN";
const char* ssid2 = "SniffySage's Galaxy S23+";
const char* ssid3 = "wifi joao";
const char* ssid4 = "Motorola XL";
// Função para obter o RSSI de uma rede específica
int getRSSI(const char* ssid) {
  int n = WiFi.scanNetworks();
  for (int i = 0; i < n; i++) {
    if (WiFi.SSID(i) == ssid) {
      return WiFi.RSSI(i);
    }
  }
  return -100; // Retorna -100 se a rede não for encontrada (valor padrão de sinal fraco)
}
void setup() {
  Serial.begin(115200);
  WiFi.mode(WIFI_STA);
  WiFi.disconnect();
  delay(100);
  Serial.println("Iniciando escaneamento...");
}
void loop() {
  // Obter o RSSI de cada roteador
  int rssi1 = getRSSI(ssid1);
  int rssi2 = getRSSI(ssid2);
  int rssi3 = getRSSI(ssid3);
  int rssi4 = getRSSI(ssid4);
  // Exibir os valores de RSSI no formato desejado
  Serial.print("SSID: ");
  Serial.print(ssid1);
  Serial.print(" - RSSI: ");
  Serial.println(rssi1);
  Serial.print("SSID: ");
  Serial.print(ssid2);
  Serial.print(" - RSSI: ");
  Serial.println(rssi2);
  Serial.print("SSID: ");
  Serial.print(ssid3);
  Serial.print(" - RSSI: ");
  Serial.println(rssi3);
  Serial.print("SSID: ");
  Serial.print(ssid4);
  Serial.print(" - RSSI: ");
  Serial.println(rssi4);
  delay(5000); // 5 segundos entre cada leitura para observar a estabilidade
}




Print do monitor serial, após Run do código:

![image](https://github.com/user-attachments/assets/721c586d-3fc0-4cf0-8292-99757ced7f90)

 
### Discussão dos Resultados

Para cada um dos quatro roteadores, o RSSI apresentou flutuações relevantes de um escaneamento para o outro. Por exemplo, o roteador “TBN” registrou valores variando entre -62 dBm e -54 dBm, enquanto o roteador “SniffySage’s Galaxy S23+” teve variações de -77 dBm até -69 dBm. O roteador “Motorola XL” apresentou ainda mais variabilidade, com leituras entre -78 dBm e -64 dBm, enquanto o roteador “wifi joao” também mostrou variações frequentes, com valores entre -57 dBm e -68 dBm. Essas variações são consideráveis para um sistema de localização baseado em RSSI, já que alterações de 5 a 10 dBm representam mudanças significativas na intensidade do sinal, o que dificulta a determinação de uma posição estável.
Devido à grande oscilação dos valores de RSSI, a estimativa de posição calculada pelo ESP32 com base nesses dados se torna pouco confiável. Em um cenário ideal, o RSSI deveria apresentar pouca variação em leituras consecutivas, especialmente se o dispositivo e os roteadores estão em posições fixas e o ambiente é estável. A instabilidade observada sugere que fatores externos, como interferências de outros dispositivos, reflexões de sinal em superfícies ou até mesmo variações no ambiente físico, podem estar comprometendo a estabilidade das leituras.

Em ambientes internos, o sinal de Wi-Fi pode ser afetado por diversos elementos, como paredes, móveis, outros dispositivos eletrônicos e até pessoas em movimento, que podem causar interferência. Além disso, a presença de redes Wi-Fi concorrentes e outras fontes de ruído eletromagnético podem contribuir para as flutuações no RSSI. O ESP32, embora seja uma ferramenta útil para testes de RSSI, é sensível a essas interferências, de modo que o RSSI captado pode não refletir a real distância até os roteadores, o que prejudica a confiabilidade de um sistema de localização baseado exclusivamente em RSSI.

### Soluções Futuras

Para melhorar a precisão do teste de estabilidade de sinal com o ESP32 e pontos de acesso, o que poderia ser feito é controlar o ambiente e minimizar interferências. Idealmente, o teste deve ser realizado em um local onde não haja redes Wi-Fi concorrentes, dispositivos eletrônicos ativos ou grandes estruturas metálicas, pois esses fatores contribuem para flutuações no RSSI. Além disso, é importante manter o ESP32 e os roteadores em posições fixas e evitar a movimentação de objetos ou pessoas durante o teste, pois qualquer mudança no ambiente pode afetar o caminho do sinal e introduzir variações indesejadas. Outra medida que pode ajudar é ajustar a disposição dos roteadores em diferentes alturas, criando uma configuração tridimensional que reduz problemas de reflexão e melhora a confiabilidade das leituras.
Em termos de processamento dos dados, é recomendável realizar várias leituras de RSSI em cada posição e calcular a média dessas leituras. Isso ajuda a suavizar variações momentâneas e resulta em uma estimativa de sinal mais estável. Aplicar um filtro de Kalman pode ser ainda mais eficaz, pois esse filtro combina leituras passadas e ajusta as novas leituras para eliminar ruídos, proporcionando uma estimativa mais consistente. Outra alternativa é o uso de uma média móvel das leituras, o que também ajuda a suavizar flutuações bruscas. Além disso, realizar uma calibração do RSSI no ambiente antes do teste principal pode melhorar a interpretação dos valores de sinal: ao mapear o RSSI em diferentes posições conhecidas, é possível ajustar o comportamento dos dados de acordo com as características específicas do local.
Por fim, é possível explorar alternativas tecnológicas para melhorar a precisão. O Bluetooth Low Energy (BLE), que é suportado pelo ESP32, pode ser uma opção mais estável do que o Wi-Fi para medir intensidade de sinal em curtas distâncias, uma vez que o BLE tende a ter menos variabilidade. Além disso, combinar dados de RSSI do Wi-Fi e do BLE pode criar um sistema de localização mais robusto, aproveitando a estabilidade do BLE e a maior cobertura do Wi-Fi. Outra estratégia útil é integrar sensores de movimento, como acelerômetros e giroscópios, caso o ESP32 esteja em movimento, pois isso complementa as leituras de RSSI com dados de movimentação, resultando em uma estimativa de posição mais precisa. Com essas estratégias aplicadas em conjunto, o teste de estabilidade de sinal tem maiores chances de fornecer dados confiáveis e consistentes para localização em ambientes internos.








