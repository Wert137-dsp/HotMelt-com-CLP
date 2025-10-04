# Sistema de Controle de Temperatura Multizona com CLP

## 📄 Resumo
Este projeto é uma solução de automação industrial para o controle de processo térmico de um equipamento de aplicação de hot melt. O software, desenvolvido para um CLP compatível com o ambiente Mitsubishi, gerencia cinco zonas de aquecimento de forma independente e segura, garantindo a estabilidade e a precisão da temperatura através de um sistema de controle em malha fechada.

## 🏗️ Arquitetura do Software
A arquitetura do software foi a principal prioridade do desenvolvimento, focando em modularidade, manutenibilidade e robustez. A lógica foi decomposta em Blocos de Função (FBs) coesos e de baixo acoplamento, seguindo o princípio de Separação de Responsabilidades (SoC).

O programa principal (`POU_01`) atua como um orquestrador, gerenciando o ciclo de vida e a interação entre os módulos, sem conter lógica de controle de baixo nível.

```
[ POU_01 (Orquestrador Principal) ]
    |
    |--> [ FB config_PID ]         (Parametrização inicial do sistema)
    |
    |--> [ FB ajuste_medicao ]     (Escalonamento e validação dos sensores)
    |
    |--> [ FB controle_temperatura (x5) ] (Execução do algoritmo PID para cada zona)
    |
    |--> [ FB alarm_geral ]        (Gerenciamento de falhas e estados de segurança)
```

## ✨ Funcionalidades em Geral
- **Controle de Processo PID:** Algoritmo Proporcional-Integral-Derivativo para regulação precisa da temperatura.
- **Gerenciamento Multizona:** Controle simultâneo de 5 zonas (tanque, mangueiras, aplicadores) com setpoints independentes.
- **Acionamento PWM:** Modulação por Largura de Pulso para controle fino da potência dos aquecedores.
- **Segurança e Intertravamento:** Sistema que condiciona operação à ausência de alarmes, garantindo segurança.
- **Detecção de Falha de Hardware:** Identificação de falhas (ex: sensor desconectado) e transição para estado seguro.
- **Gerenciamento de Estados:** Transição entre Parado, Standby e Operação.

## 🛠️ Demonstração de Capacidade (Do Hardware ao Software)
Este projeto abrange três pilares da automação industrial:
- **Projeto Elétrico:** Diagrama elétrico, especificação, seleção de componentes (CLP Coolmay, fonte, disjuntores, relés, etc.).
- **Implementação Física:** Montagem completa do painel, disposição em trilho DIN, organização em canaletas e fiação.
- **Desenvolvimento do Software:** Arquitetura, programação, teste e depuração da lógica de controle.

## 💡 Conceitos Aplicados

### Engenharia de Software
- Arquitetura Modular e Separação de Responsabilidades (SoC)
- Encapsulamento e Abstração
- Reutilização de Código (DRY)
- Programação Defensiva e Tolerância a Falhas
- Gerenciamento de Estado (Máquina de Estados Finitos)

### Engenharia de Controle e Automação
- Controle PID e Sintonia de Controladores
- Controle em Malha Fechada
- Intertravamento e Lógica de Segurança
- Instrumentação Industrial (Sensores e Atuadores)
- Modulação por Largura de Pulso (PWM)
- Escalonamento e Condicionamento de Sinais

### Hardware e Software
- **Controlador:** CLP Coolmay, compatível com Mitsubishi.
- **Ambiente de Desenvolvimento:** MELSOFT GX Works2.

## 👤 Autor
**Diego Campos**

