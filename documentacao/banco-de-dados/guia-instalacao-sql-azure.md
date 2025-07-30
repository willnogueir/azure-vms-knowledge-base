# 🗄️ Guia de Instalação e Configuração de Banco de Dados no Azure

Este documento apresenta as etapas e considerações para criar e gerenciar uma instância de banco de dados SQL no Azure, incluindo detalhes de arquitetura, custos estimados e impacto do modelo de serviço (IaaS).

---

## 🧱 Configurando uma Instância de Banco de Dados no Azure

### 🎨 Imagem e Arquitetura

A criação de um banco de dados pode ser feita de duas formas principais:

- **Plataforma como Serviço (PaaS)**: Usando o serviço `Azure SQL Database`, onde a Microsoft gerencia infraestrutura, backup e alta disponibilidade.
- **Infraestrutura como Serviço (IaaS)**: Criando uma **VM com SQL Server instalado**. Oferece mais controle, porém maior responsabilidade do cliente.

> Para ambientes com alta customização, o modelo IaaS é recomendado. Para simplicidade e escalabilidade automática, PaaS é ideal.

---

### 💰 Relacionar Tamanho da Instância com Previsibilidade de Custo

| Tamanho da Instância | vCPU | RAM  | Uso Ideal                 | Custo Estimado (mensal) |
|----------------------|------|------|---------------------------|--------------------------|
| Basic (DTU)          | 1    | 2 GB | Desenvolvimento / testes  | ~R$ 25                   |
| Standard S2          | 2    | 50 GB| Aplicações médias         | ~R$ 260                  |
| Premium P1           | 4    | 125 GB| Alta performance          | ~R$ 1.200+               |
| VM SQL personalizada | 2–16 | Até 128 GB | Full controle (IaaS) | Depende da SKU + licenças |

> Os valores são estimativas médias baseadas em preços públicos do Azure. Use a [Calculadora do Azure](https://azure.microsoft.com/pt-br/pricing/calculator/) para dados atualizados.

---

## ⚙️ Etapas de Criação de uma VM com Banco de Dados SQL

Caso opte por IaaS (SQL em VM), siga as seguintes etapas:

1. **Básico**: Nome da VM, região, sistema operacional (ex: Windows Server + SQL)
2. **Disco**: Tipo de disco (Premium SSD recomendado para performance)
3. **Rede**: VNet, sub-rede e regras de firewall / NSG
4. **Gerenciamento**: Habilitar Auto-shutdown, identidade gerenciada
5. **Monitoramento**: Log Analytics e diagnóstico
6. **Avançado**: Extensões (ex: agentes de segurança ou backup)
7. **Marcas**: Tags de organização e custo

---

## 🛠️ Criar Banco de Dados SQL (PaaS)

Para utilizar `Azure SQL Database` como serviço gerenciado:

- **Opções disponíveis**:
  - **DTU-based model**: Simples, baseado em recursos combinados.
  - **vCore model**: Mais previsível e personalizável.
  - **Hyperscale**: Alta performance e escalabilidade.

- **Fatores que influenciam o custo**:
  - Nível de serviço (Basic, Standard, Premium)
  - Região
  - Licenciamento (com ou sem Software Assurance)
  - Alta disponibilidade e replicação

| Nível | SLA        | Ideal para            | Observação                |
|-------|------------|-----------------------|---------------------------|
| Basic| 99.9%      | Testes e POCs         | Mais barato               |
| Standard | 99.99% | Aplicações médias     | Boa relação custo/benefício |
| Premium | 99.99%  | Apps críticas         | Alta performance e IOPS   |

---

## ☁️ IaaS: Infraestrutura como Serviço

Quando usamos **SQL Server em uma VM (IaaS)**:

| Aspecto                  | Cliente (Você)      | Microsoft           |
|--------------------------|---------------------|---------------------|
| Infraestrutura           | ⚙️ Instala e gerencia | 🛠️ Fornece host     |
| Sistema Operacional      | ⚙️ Responsável       |                     |
| Patches e atualizações   | ⚙️ Deve aplicar      |                     |
| Backup / HA              | ⚙️ Deve configurar   |                     |
| Suporte / SLA            | 🛠️ VM = 99.9–99.95%  |                     |

### 💡 Impacto na Demanda e Preço:

- O cliente tem **mais responsabilidade operacional**, o que exige mais tempo e equipe qualificada.
- Em contrapartida, **ganha controle total** sobre configurações e recursos.
- O custo tende a ser **mais imprevisível**, pois depende do uso da VM, licenciamento e disco.

---

## 🔗 Recursos Recomendados

- [Documentação Azure SQL Database](https://learn.microsoft.com/pt-br/azure/azure-sql/)
- [SQL Server em Máquinas Virtuais](https://learn.microsoft.com/pt-br/azure/virtual-machines/workloads/sql/sql-server-on-azure-vm)
- [Calculadora de Preços do Azure](https://azure.microsoft.com/pt-br/pricing/calculator/)
