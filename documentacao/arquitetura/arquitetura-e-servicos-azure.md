
# ⚙️ Arquitetura e Serviços do Azure

Este documento apresenta uma visão geral dos principais serviços de computação, rede e hospedagem disponíveis no Microsoft Azure, incluindo opções de máquinas virtuais, contêineres, funções e plataformas gerenciadas.

---

## ☁️ Serviços de Computação: Máquinas Virtuais do Azure

As **Máquinas Virtuais (VMs)** são uma das formas mais flexíveis de executar cargas de trabalho no Azure. Permitem que você execute sistemas operacionais e aplicativos com controle completo sobre a configuração, segurança e armazenamento.

---

## 🧠 Computação e Rede

### 🔹 Tipos de Computação

| Tipo               | Descrição                                                                 |
|--------------------|---------------------------------------------------------------------------|
| Máquinas Virtuais   | Execução de sistemas operacionais completos (Windows/Linux) na nuvem.     |
| Instâncias de Contêiner | Execução leve e rápida de aplicativos isolados sem SO completo.       |
| Azure Functions     | Execução de código sob demanda em resposta a eventos (serverless).       |

### 🔧 Recursos exigidos para Máquinas Virtuais

- vCPUs e memória
- Tipo e tamanho do disco (HDD, SSD, Premium SSD)
- Regras de rede e IPs
- Diagnóstico e monitoramento
- Licenciamento (incluso ou BYOL)

### 🔸 Opções de Máquinas Virtuais

| Opção                          | Descrição                                                                 |
|--------------------------------|---------------------------------------------------------------------------|
| VM                            | Instância individual sob controle total do usuário.                       |
| Conjunto de Dimensionamento   | Conjunto elástico de VMs para balanceamento e autoescalonamento.         |
| Conjunto de Disponibilidade   | Grupo de VMs distribuídas para alta disponibilidade em domínios distintos.|
| Área de Trabalho Virtual      | Experiência de desktop Windows na nuvem para múltiplos usuários.          |

### 🌐 Hospedagem de Aplicativos

- Azure App Service (Web Apps, APIs)
- Containers gerenciados (Web App for Containers)
- Suporte a .NET, Java, Python, PHP, Node.js

### 🌐 Redes Virtuais

- Virtual Network (VNet): Rede lógica privada
- Sub-redes e NSG (Network Security Groups)
- Peering entre redes virtuais

### 📍 Pontos de Extremidade (Endpoints)

| Tipo        | Descrição                                  |
|-------------|----------------------------------------------|
| Público     | Acesso aberto via IP público                 |
| Privado     | Acesso interno via VNet (Private Endpoint)   |

---

## 🏘️ Conjuntos de Disponibilidade de Máquinas Virtuais

### 🔹 Conjuntos de Dimensionamento de VM

- Escalonamento automático de VMs
- Gerenciado como um único recurso
- Ideal para grandes aplicações distribuídas

### 🔹 Conjuntos de Disponibilidade de VM

- Aumentam a resiliência distribuindo VMs em domínios de falha e atualização
- Recomendado para alta disponibilidade

### 🔹 Domínio de Falha x Domínio de Atualização

- **Domínio de Falha**: Diferentes racks físicos (energia, rede)
- **Domínio de Atualização**: Agendamento de atualizações em momentos distintos

---

## 💻 Área de Trabalho Virtual e Contêineres

| Opção             | Descrição                                                             |
|------------------|-----------------------------------------------------------------------|
| VM               | Máquina completa com SO e apps                                         |
| Contêiner        | Execução isolada de apps, sem SO completo                              |
| AKS              | Orquestração de contêineres com Kubernetes no Azure                    |

---

## 🧬 Azure Functions e Serviços de Aplicativos

### 🔸 Azure Functions

- Modelo serverless
- Execução de código por eventos (timer, HTTP, fila, etc.)
- Ideal para microsserviços, automações e integrações

### 🔸 Comparação entre Opções de Computação

| Opção               | Características Principais                                                                 |
|---------------------|---------------------------------------------------------------------------------------------|
| Máquinas Virtuais   | Controle total, lift-and-shift, pacote completo de SO e host                               |
| Área de Trabalho    | Desktop virtual Windows, acesso via navegador, multiusuário                                |
| Contêineres         | Leves, isolados, prontos para orquestração (AKS), ideais para microsserviços               |
| Serviços de Aplicativos | PaaS gerenciado para Web Apps e APIs com linguagens modernas, segurança e escalabilidade |
| Azure Functions     | Serverless, execução sob demanda, cobrança por execução                                    |

---

## 🌐 Serviços de Rede

- **Rede Virtual (VNet)**: Criação de rede privada na nuvem
- **Gateway de VPN**: Conexão segura entre on-premises e Azure
- **ExpressRoute**: Conexão privada dedicada ao Azure, sem internet
- **DNS do Azure**: Gerenciamento de domínios e registros DNS internos/externos

---

## 🔗 Referências

- [Documentação oficial do Azure](https://learn.microsoft.com/pt-br/azure/)
- [Serviços de Computação Azure](https://learn.microsoft.com/pt-br/azure/virtual-machines/)
- [Azure Functions](https://learn.microsoft.com/pt-br/azure/azure-functions/)
- [AKS – Azure Kubernetes Service](https://learn.microsoft.com/pt-br/azure/aks/)
