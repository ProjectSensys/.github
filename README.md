# SENSYS

### Monitoramento Inteligente de Equipamentos

O **Sensys** é uma plataforma de monitoramento de equipamentos industriais desenvolvida como **Projeto Integrador**, unindo as áreas de **Análise e Desenvolvimento de Sistemas** e **Mecatrônica Industrial**.

O projeto tem como objetivo realizar o monitoramento contínuo de uma bomba elétrica por meio de sensores e tecnologias IoT, permitindo acompanhar dados operacionais em tempo real, armazenar históricos e identificar situações anormais que possam indicar possíveis falhas no equipamento.

A proposta busca contribuir para uma abordagem de **manutenção preditiva**, possibilitando que alterações no comportamento do equipamento sejam identificadas antes que resultem em falhas mais graves.

---

## 🎯 Objetivo

Desenvolver uma solução integrada capaz de:

- Coletar dados reais de uma bomba elétrica;
- Transmitir as informações através de MQTT;
- Processar e armazenar as medições;
- Disponibilizar monitoramento em tempo real;
- Manter histórico das medições;
- Identificar condições de alerta;
- Disponibilizar dashboards Web e Mobile;
- Auxiliar na análise do comportamento do equipamento.

---

## 📊 Variáveis monitoradas

Inicialmente, o Sensys trabalhará com:

- 🌡️ **Temperatura**
- 📳 **Vibração**
- ⚡ **Corrente elétrica**

A arquitetura será preparada para a futura integração de outras variáveis do projeto, como:

- Tensão;
- Pressão;
- Vazão.

---

## 🏗️ Arquitetura

O Sensys será dividido em diferentes frentes de desenvolvimento:

```text
                    EQUIPAMENTO
                         │
                         ▼
               Sensores + ESP32
                   MECATRÔNICA
                         │
                         │ MQTT
                         ▼
                  MQTT BROKER
                         │
                         ▼
                     BACK-END
                         │
              ┌──────────┼──────────┐
              │          │          │
              ▼          ▼          ▼
          Banco de      API      Tempo Real
           Dados
                         │
                 ┌───────┴───────┐
                 │               │
                 ▼               ▼
             FRONT WEB      FRONT MOBILE
```

---

## 🧩 Frentes do projeto

### 🔧 Mecatrônica

Responsável pela parte física do sistema:

- Sensores;
- ESP32;
- Leitura das variáveis;
- Calibração;
- Processamento local;
- Comunicação MQTT;
- Testes com o equipamento.

### 🌐 Front-end Web

Responsável pela interface principal de monitoramento.

Principais funcionalidades previstas:

- Dashboard;
- Monitoramento em tempo real;
- Visualização dos sensores;
- Histórico de medições;
- Gráficos;
- Alertas;
- Equipamentos;
- Relatórios;
- Gestão de usuários;
- Perfis de acesso.

### 📱 Front-end Mobile

Aplicativo voltado principalmente ao acompanhamento rápido do equipamento.

Funcionalidades previstas:

- Login;
- Status do equipamento;
- Monitoramento;
- Valores atuais dos sensores;
- Gráficos;
- Alertas;
- Perfil do usuário.

### ⚙️ Back-end

Responsável pela centralização das regras e dos dados do Sensys.

Principais responsabilidades:

- Consumo das mensagens MQTT;
- Processamento das medições;
- Persistência dos dados;
- API para Web e Mobile;
- Comunicação em tempo real;
- Autenticação;
- Autorização;
- Gestão de usuários;
- Gestão de equipamentos;
- Histórico;
- Alertas.

### ☁️ Nuvem

Responsável pela infraestrutura necessária para disponibilização do sistema.

Inclui:

- Hospedagem das aplicações;
- Banco de dados;
- Containers;
- Broker MQTT;
- Deploy;
- HTTPS;
- Variáveis de ambiente;
- Monitoramento da infraestrutura;
- Backup dos dados.

### 📚 Documentação

Responsável pela documentação técnica e funcional do projeto.

Entre os documentos previstos estão:

- Visão geral;
- Requisitos funcionais e não funcionais;
- Arquitetura;
- Diagramas;
- Modelo de dados;
- Contrato MQTT;
- Documentação da API;
- Regras de negócio;
- Perfis e permissões;
- Infraestrutura;
- Testes;
- Manual de utilização.

---

## 👥 Perfis de acesso

O Sensys prevê inicialmente três perfis:

| Perfil | Responsabilidade |
|---|---|
| **Administrador** | Administração completa da plataforma |
| **Técnico** | Monitoramento e análise técnica dos equipamentos |
| **Gestor** | Acompanhamento de indicadores, históricos e relatórios |

As permissões serão controladas tanto nas interfaces quanto no Back-end.

---

## 📡 Comunicação IoT

Os dispositivos utilizarão **MQTT** para comunicação entre o ESP32 e a plataforma.

Fluxo básico:

```text
Sensor
   ↓
ESP32
   ↓
MQTT
   ↓
Back-end
   ↓
Banco de Dados
   ↓
API / Tempo Real
   ↓
Web / Mobile
```

Exemplo de informação transmitida:

```json
{
  "device_id": "bomba_01",
  "temperatura": 38.42,
  "vibracao": 12.35,
  "corrente": 1.82,
  "falha": false
}
```

---

## 🚨 Monitoramento e alertas

A plataforma acompanhará continuamente as medições recebidas.

Quando uma variável ultrapassar os limites definidos e validados para o equipamento, o sistema poderá registrar uma ocorrência.

Exemplo:

```text
Bomba #01

Temperatura:  38.4 °C     NORMAL
Vibração:     12.3 mm/s   NORMAL
Corrente:      1.82 A     NORMAL

Status: ● OPERANDO NORMALMENTE
```

Em uma situação anormal:

```text
Bomba #01

Vibração: 34.8 mm/s

⚠ ALERTA DE VIBRAÇÃO

Status: ATENÇÃO
```

---

## 🛠️ Tecnologias

A stack poderá evoluir durante o desenvolvimento. Inicialmente, estão previstas tecnologias como:

**Web**
- React
- Vite
- TypeScript

**Mobile**
- React Native
- Expo

**Back-end**
- Python
- FastAPI

**Dados**
- PostgreSQL

**IoT**
- ESP32
- MQTT

**Infraestrutura**
- Docker
- AWS

**Versionamento**
- Git
- GitHub

---

## 📁 Organização

Os projetos do Sensys serão separados por responsabilidade dentro da organização.

```text
Sensys
│
├── sensys-web
│
├── sensys-mobile
│
├── sensys-backend
│
├── sensys-iot
│
├── sensys-infra
│
└── sensys-docs
```

Cada repositório deverá possuir sua própria documentação contendo instruções específicas para configuração, execução e desenvolvimento.

---

## 🚧 Status

> 🟡 **Projeto em desenvolvimento**

O Sensys está sendo desenvolvido como Projeto Integrador, com evolução incremental entre as equipes de Desenvolvimento de Sistemas e Mecatrônica.

As funcionalidades, tecnologias e regras apresentadas nesta documentação poderão sofrer alterações conforme os testes, validações e evolução do projeto.

---

<p align="center">
  <strong>SENSYS</strong><br>
  Monitoramento Inteligente de Equipamentos
</p>