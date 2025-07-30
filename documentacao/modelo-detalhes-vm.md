# 🧾 Modelo de Documentação: Detalhes de Instância de VM no Azure

Este modelo serve como referência para registrar os principais detalhes técnicos de uma Máquina Virtual (VM) criada na Azure, incluindo configurações de hardware, rede, armazenamento, diagnóstico, e informações críticas sobre disponibilidade e SLA.

---

## 🆔 Identificação

| Item                      | Valor Exemplo                  |
|---------------------------|--------------------------------|
| Nome da VM                | vm-app-producao-01             |
| Resource Group            | rg-prod-infra                  |
| Subscription ID           | xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx |
| Data de Criação           | 2025-07-30                     |
| Estado da Instância       | Running                        |

---

## 🌎 Localização

| Item                      | Valor Exemplo      |
|---------------------------|--------------------|
| Região (Region)           | Brazil South       |
| Zona de Disponibilidade   | 1                  |
| Opções de Disponibilidade | Availability Zone  |

---

### 🛡️ SLA baseado na Opção de Disponibilidade

| Opção de Disponibilidade       | Descrição                                                                            | SLA Estimado     |
|-------------------------------|----------------------------------------------------------------------------------------|------------------|
| Nenhuma (sem redundância)     | VM isolada sem alta disponibilidade                                                   | **sem SLA**      |
| Conjunto de Disponibilidade   | Múltiplas VMs distribuídas em domínios de falha e atualização                         | **99,95%**       |
| Zona de Disponibilidade       | VMs em zonas físicas distintas dentro da mesma região                                 | **99,99%**       |

> 📌 O uso de **Zonas de Disponibilidade** garante maior resiliência e aumenta o SLA da aplicação.  
> Para obter o SLA mais alto, implante **duas ou mais VMs em zonas distintas** com balanceamento de carga.

---

## ⚙️ Tamanho e Desempenho

| Item                   | Valor Exemplo       |
|------------------------|---------------------|
| Tamanho (SKU)          | Standard_D2s_v3     |
| vCPUs                  | 2                   |
| Memória RAM            | 8 GiB               |
| Geração                | V3                  |
| Tipo de Disco do SO    | Premium SSD         |
| Disco do SO (tamanho)  | 128 GiB             |
| Discos de Dados        | 1 x 256 GiB SSD     |

---

## 🌐 Rede

| Item                    | Valor Exemplo       |
|-------------------------|---------------------|
| IP Público              | 20.201.100.5        |
| IP Privado              | 10.0.1.4            |
| Virtual Network (VNet)  | vnet-infra-prod     |
| Sub-rede                | subnet-app          |
| NSG (grupo de segurança)| nsg-app-prod        |

---

## 🖥️ Sistema Operacional

| Item                    | Valor Exemplo        |
|-------------------------|----------------------|
| Tipo de Imagem          | Ubuntu 22.04 LTS     |
| Licença                 | Linux (inclusa)      |
| Diagnóstico de Boot     | Habilitado           |

---

## 🔐 Acesso

| Item                    | Valor Exemplo        |
|-------------------------|----------------------|
| Método de Acesso        | SSH                  |
| Usuário padrão          | azureadmin           |
| Porta liberada          | 22                   |

---

## 🧪 Diagnóstico e Monitoramento

| Item                          | Valor Exemplo           |
|-------------------------------|-------------------------|
| Boot Diagnostics              | Habilitado              |
| Conta de Armazenamento        | diagvmstorageprod       |
| Log Analytics                 | Vinculado (workspace)   |

---

## 📌 Observações

- Adicionar etiquetas (tags) para gerenciamento e automação.
- Verificar se há backup configurado via Azure Backup.
- Validar regras de NSG e portas abertas para produção.

---

## 📎 Referências

- [Documentação oficial de VMs – Azure](https://learn.microsoft.com/pt-br/azure/virtual-machines/)
- [Opções de alta disponibilidade no Azure](https://learn.microsoft.com/pt-br/azure/virtual-machines/availability)
- [SLA de Máquinas Virtuais](https://learn.microsoft.com/pt-br/azure/virtual-machines/sla)

