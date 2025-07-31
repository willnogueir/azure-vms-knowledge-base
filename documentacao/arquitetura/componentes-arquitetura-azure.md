# 🏗️ Componentes Arquitetônicos Fundamentais do Microsoft Azure

Este documento descreve os principais componentes arquitetônicos da plataforma Microsoft Azure, essenciais para o planejamento, organização e controle de ambientes em nuvem de forma escalável, segura e bem estruturada.

---

## 🌍 Regiões, Pares de Regiões e Regiões Soberanas

### 📌 Regiões do Azure

São **áreas geográficas físicas** que contêm **um ou mais datacenters** próximos entre si. Cada região é independente em termos de fornecimento de serviços e infraestrutura.

**Exemplos:**
- Brazil South (São Paulo)
- East US
- West Europe

> Cada região é identificada por um nome lógico, usado na criação de recursos.

---

### 🔗 Pares de Regiões (Region Pairs)

Cada região do Azure é emparelhada com outra região dentro do mesmo continente. Isso garante:
- **Recuperação de desastres (DR)**
- **Atualizações planejadas com impacto minimizado**
- **Alta disponibilidade entre regiões**

**Exemplo:**
- Brazil South ↔ South Central US

---

### 🏛️ Regiões Soberanas

São regiões isoladas por motivos regulatórios, como:
- **Azure Government** (EUA)
- **Azure China** (operado por 21Vianet)

Essas regiões têm **acesso restrito e regras próprias**, separadas da rede global da Microsoft.

---

## 🧭 Zonas de Disponibilidade

São **localizações físicas únicas** dentro de uma mesma região, com:
- Energia, refrigeração e rede próprias
- Comunicação com baixa latência entre zonas

Elas permitem:
- Alta disponibilidade real
- Execução de cargas críticas tolerantes a falhas
- SLAs superiores (ex: 99.99%)

> Exemplo: `East US` tem Zonas 1, 2 e 3. VMs e serviços podem ser distribuídos entre elas.

---

## 🏢 Datacenters do Azure

São as **instalações físicas** que armazenam servidores, redes e dispositivos usados para prover os serviços do Azure. Um ou mais datacenters compõem uma região.

- Cada datacenter é projetado com **redundância física**.
- Não é possível escolher diretamente o datacenter, apenas a **região**.

---

## 🔧 Recursos e Grupos de Recursos

### 📦 Recurso (Resource)

Qualquer item gerenciado no Azure:
- VMs
- Contas de armazenamento
- Banco de dados SQL
- IPs públicos, etc.

### 📂 Grupo de Recursos (Resource Group)

É um **container lógico** para agrupar recursos relacionados.

- Compartilham ciclo de vida (criação, exclusão)
- Facilitam gerenciamento e automação
- Aplicam permissões (RBAC) em nível de grupo

> Cada recurso pertence a **um único Resource Group**, mas pode interagir com recursos de outros grupos.

---

## 🔑 Assinaturas (Subscriptions)

Uma **assinatura** define:
- **Limites de cobrança**
- **Isolamento administrativo**
- **Quota de recursos**

Cada assinatura:
- Pertence a um único tenant do Azure AD
- Pode conter vários grupos de recursos
- Recebe fatura independente

---

## 🏗️ Grupos de Gerenciamento (Management Groups)

São **níveis hierárquicos acima das assinaturas**, usados para:
- Agrupar e gerenciar múltiplas assinaturas
- Aplicar políticas, RBAC e compliance centralizado

---

## 🧱 Hierarquia da Organização no Azure

Visualmente, a estrutura organizacional segue a hierarquia abaixo:

```
Tenant (Azure Active Directory)
└── Management Groups
    └── Subscriptions
        └── Resource Groups
            └── Resources
```

| Nível              | Função Principal                          |
|--------------------|-------------------------------------------|
| Tenant             | Diretório de identidade e autenticação    |
| Management Group   | Agrupamento de assinaturas para governança |
| Subscription       | Fronteira de cobrança e isolamento        |
| Resource Group     | Container lógico para recursos            |
| Resource           | Entidade computacional ou de serviço      |

---

## 🔗 Referências

- [Regiões e pares de regiões do Azure](https://learn.microsoft.com/pt-br/azure/best-practices-availability-paired-regions)
- [Zonas de Disponibilidade](https://learn.microsoft.com/pt-br/azure/availability-zones/az-overview)
- [Hierarquia do Azure Resource Manager](https://learn.microsoft.com/pt-br/azure/governance/management-groups/overview)
