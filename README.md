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









