# Proposta de Arquitetura para Aplicação IoT

## 1. Visão Geral da Arquitetura
A arquitetura IoT proposta será composta por três camadas principais:

- **Dispositivos de Borda (Edge Devices)**: Sensores e atuadores que capturam dados ou executam comandos.
- **Gateway**: Conecta os dispositivos de borda ao servidor, agregando e transmitindo os dados.
- **Nuvem/Servidor Local**: Responsável pelo processamento, armazenamento dos dados e fornecimento de uma plataforma para o gerenciamento dos dispositivos e visualização das informações.

## 2. Componentes da Arquitetura

### 2.1 Dispositivos de Borda
- **Sensores**: Coletam informações físicas, como temperatura, umidade, pressão, etc.
- **Atuadores**: Executam ações com base em comandos, como ligar uma lâmpada, ativar um motor, etc.
- **Exemplos de Hardware**: ESP32, Arduino, sensores de temperatura (DHT11), sensores de movimento (PIR), relés.

### 2.2 Gateway
O gateway é responsável por fazer a ponte entre os dispositivos de borda e a rede principal (nuvem ou servidor local).
- **Função**: Consolida as informações recebidas dos dispositivos de borda e utiliza protocolos de comunicação (como MQTT) para enviá-las ao servidor.
- **Hardware**: Raspberry Pi, ESP32.

### 2.3 Servidor/Nuvem
Responsável por:
- Processamento e armazenamento dos dados recebidos.
- Gerenciamento dos dispositivos conectados.
- Execução de regras ou automações baseadas nos dados recebidos.
- **Plataforma IoT**: Pode ser baseada em uma solução de IoT na nuvem (ex: AWS IoT, Google Cloud IoT) ou um servidor local configurado com ferramentas como Node-RED ou Grafana para visualização.

### 2.4 Protocolo de Comunicação
- **MQTT (Message Queuing Telemetry Transport)**: Escolhido por ser leve e eficiente para troca de mensagens em redes de baixa largura de banda.
- **Alternativa**: HTTP pode ser usado para algumas operações de comunicação.

## 3. Fluxo de Dados
1. **Coleta de Dados**: Os dispositivos de borda, como sensores, captam os dados do ambiente (ex.: temperatura e umidade).
2. **Transmissão via Gateway**: Os dados são enviados via MQTT do dispositivo de borda para o gateway.
3. **Servidor ou Nuvem**: O gateway transmite os dados ao servidor, que processa e armazena as informações.
4. **Visualização**: Os dados são exibidos em um dashboard (ex.: Grafana ou uma interface web personalizada).
5. **Automação**: Com base nos dados recebidos, o sistema pode executar ações automáticas, como acionar um atuador ou enviar notificações.

## 4. Dashboards e Monitoramento
- Dashboards personalizados mostram dados em tempo real (gráficos de temperatura, umidade, etc.).
- Interface para controlar atuadores remotamente (ex.: ligar/desligar dispositivos).

## 5. Segurança
- Utilização de chaves API e autenticação via JWT (JSON Web Token).
- Comunicação segura com criptografia TLS/SSL para proteger os dados em trânsito.

---

# README para o Projeto IoT

## Projeto IoT - Monitoramento e Controle Remoto

### Descrição
Este projeto implementa uma arquitetura de IoT que permite monitorar sensores e controlar atuadores remotamente. A arquitetura consiste em dispositivos de borda, gateways e uma plataforma de visualização de dados em tempo real.

### Funcionalidades
- Coleta de dados de sensores (ex.: temperatura, umidade).
- Transmissão de dados usando o protocolo MQTT.
- Controle remoto de dispositivos (ex.: ligar/desligar atuadores).
- Exibição de dados em dashboards (ex.: gráficos em tempo real).
- Automação de ações com base nas leituras dos sensores.

### Componentes

#### Dispositivos de Borda:
- **ESP32**
- **Sensores de Temperatura (DHT11)**
- **Relés**

#### Gateway:
- **Raspberry Pi ou ESP32**
- **Comunicação via MQTT**

#### Servidor/Plataforma:
- **Plataforma de monitoramento** (ex.: Node-RED, Grafana)
- **Banco de dados** (ex.: InfluxDB)

### Requisitos do Sistema

#### Hardware:
- **ESP32**
- **Sensores de temperatura/umidade** (DHT11)
- **Atuadores** (Relés)
- **Raspberry Pi** (opcional como gateway)

#### Software:
- **Node-RED** para o processamento de dados
- **Grafana** para visualização de dashboards
- **Mosquitto MQTT Broker**
- **Python ou C++** para a programação dos dispositivos

### Instalação e Configuração

#### Configuração dos Dispositivos de Borda:
- Configure os sensores e atuadores no ESP32.
- Carregue o código no dispositivo com suporte ao protocolo MQTT.

#### Configuração do Gateway:
- Instale o Mosquitto MQTT Broker no Raspberry Pi ou utilize um serviço MQTT online.
- Configure o gateway para enviar dados dos dispositivos para o servidor.

#### Servidor e Visualização:
- Instale o Node-RED para processar os dados recebidos via MQTT.
- Configure o banco de dados InfluxDB para armazenar os dados de sensores.
- Configure o Grafana para visualizar os dados em tempo real.

### Uso

#### Suba o Broker MQTT:
- Inicie o servidor MQTT (Mosquitto) localmente ou conecte-se a um broker na nuvem.

#### Monitore os Sensores:
- Veja os dados dos sensores aparecendo em tempo real nos dashboards.

#### Controle Remoto:
- Use o dashboard para acionar/desligar atuadores remotamente, como ligar uma lâmpada.

### Automação
- Crie regras de automação no Node-RED, como ligar um ventilador quando a temperatura ultrapassar certo nível.

### Segurança
- Utilize autenticação com chaves de API para proteger o acesso aos dispositivos.
- Certifique-se de que o tráfego MQTT esteja protegido com SSL/TLS.
