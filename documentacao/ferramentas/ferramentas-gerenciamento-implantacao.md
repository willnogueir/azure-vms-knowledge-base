# 🛠️ Ferramentas de Gerenciamento e Implantação no Azure

> Resumo: este documento descreve as principais ferramentas e métodos para **gerenciar e implantar** recursos no Microsoft Azure — desde a interface gráfica até automação, infraestrutura como código e gerenciamento híbrido (Azure Arc). Inclui quando usar cada ferramenta, melhores práticas, exemplos e referências.

---

## Índice
1. Visão Geral  
2. Matriz de Ferramentas (comparativo rápido)  
3. Portal do Azure  
4. Azure Cloud Shell (CLI + PowerShell no navegador)  
5. Azure CLI  
6. Azure PowerShell  
7. Azure Resource Manager (ARM) e Modelos ARM  
8. Bicep, Terraform e Infraestrutura como Código (IaC)  
9. Azure Arc (gerenciamento híbrido/multicloud)  
10. Integração com CI/CD (Azure DevOps / GitHub Actions)  
11. Segurança, RBAC e Boas Práticas de Governança  
12. Troubleshooting e dicas práticas  
13. Referências

---

## 1. Visão Geral

O Azure disponibiliza várias formas de **criar, configurar e operar** recursos. A escolha da ferramenta depende do objetivo:

- Ações manuais e inspeção visual → **Portal do Azure**  
- Execução rápida de comandos sem instalar nada → **Azure Cloud Shell**  
- Automação cross-platform → **Azure CLI**  
- Automação orientada a PowerShell/Windows → **Azure PowerShell**  
- Implantação padronizada e reprodutível → **ARM Templates / Bicep / Terraform**  
- Gerenciamento de recursos on-premises/multicloud → **Azure Arc**

---

## 2. Matriz de Ferramentas (comparativo rápido)

| Ferramenta / Recurso | Interface | Propósito principal | Quando usar |
|----------------------|-----------|---------------------|-------------|
| Portal do Azure      | GUI (web) | Gestão visual, monitoramento e configuração pontual | Prototipagem, onboarding, dashboards |
| Azure Cloud Shell    | Shell web (Bash / PowerShell) | Terminal pronto com Azure CLI & PowerShell | Trabalhar de qualquer máquina sem setup |
| Azure CLI            | CLI (bash, cmd, powershell) | Automação e scripts multiplataforma | Pipelines, scripts, automações CI |
| Azure PowerShell     | PowerShell module | Scripts PowerShell com cmdlets Azure | Admins Windows, scripts complexos |
| ARM Templates        | JSON | IaC nativa Azure | Deploys reprodutíveis via ARM |
| Bicep                | DSL (decl.) | Sintaxe moderna para ARM (compila em ARM) | IaC legível no Azure |
| Terraform            | DSL HashiCorp | IaC multiplataforma | Multi-cloud, reuso de módulos |
| Azure Arc            | Agente / Control Plane | Gerenciar recursos on-prem / multicloud | Híbrido, políticas centralizadas |

---

## 3. Portal do Azure

**O que é:** interface web oficial (portal.azure.com) para criar, configurar e monitorar recursos.

**Principais usos:**
- Criação de recursos via UI (wizards)
- Painéis (dashboards) personalizados com métricas
- Configuração inicial de RBAC, tags e políticas
- Visualização de logs e alertas (monitoring)

**Dicas práticas:**
- Monte dashboards por responsabilidade (cost, ops, security).
- Use “Cloud Shell” direto do Portal para comandos rápidos.
- Crie templates a partir de recursos já configurados (Export template).

---

## 4. Azure Cloud Shell

**O que é:** terminal online (Bash ou PowerShell) hospedado pela Microsoft, integrado ao Portal.

**Vantagens:**
- Não precisa instalar nada localmente.
- Inclui Azure CLI, Azure PowerShell, Git, editores (code), e utilitários.
- Persiste arquivos em um *File Share* do Azure (storage account ligada).

**Exemplo de uso (abrir Bash e criar resource group):**
```bash
az group create --name rg-exemplo --location brazilsouth

---

## ⌨️ 5. CLI do Azure

A **Azure Command-Line Interface (CLI)** é multiplataforma (Windows, macOS e Linux) e utiliza comandos simples para gerenciar recursos.  
Exemplo de uso:
```bash
az group create --name MeuGrupoRecursos --location eastus

---

# 5. Azure CLI
O que é: Ferramenta de linha de comando multiplataforma (az) para gerenciar recursos Azure.

**Instalação:** Documentação oficial

**Exemplo:**

```bash
# Login
az login

# Criar Resource Group
az group create --name meu-rg --location eastus

# Criar VM simples
az vm create --resource-group meu-rg --name minhaVM --image UbuntuLTS --admin-username azureuser
```

**Quando usar:**

- Automação via scripts shell
- Pipelines CI cross-platform
- Workflows consistentes em Linux/macOS/Windows

---

# 6. Azure PowerShell
O que é: Módulo PowerShell (Az) com cmdlets para o Azure.

Ideal para administradores Windows e automações PowerShell.

**Exemplo:**

```powershell
# Instalar módulo
Install-Module -Name Az -Scope CurrentUser -Repository PSGallery -Force

# Login
Connect-AzAccount

# Criar Resource Group
New-AzResourceGroup -Name "meu-rg" -Location "Brazil South"
```

---

# 7. Azure Resource Manager (ARM) e Modelos ARM
ARM: Plano de controle do Azure para provisionamento e gerenciamento de recursos.

Modelos ARM: JSON declarativos para deploy idempotente.

**Características:**

- Suportam parâmetros, variáveis e outputs
- Permitem versionamento e automação
- Integram RBAC e tags no provisionamento

**Exemplo JSON:**

```json
{
  "$schema": "https://schema.management.azure.com/schemas/2019-04-01/deploymentTemplate.json#",
  "contentVersion": "1.0.0.0",
  "parameters": {
    "location": { "type": "string" }
  },
  "resources": [
    {
      "type": "Microsoft.Storage/storageAccounts",
      "apiVersion": "2021-04-01",
      "name": "[concat('st', uniqueString(resourceGroup().id))]",
      "location": "[parameters('location')]",
      "sku": { "name": "Standard_LRS" },
      "kind": "StorageV2",
      "properties": {}
    }
  ]
}
```

---

# 8. Bicep, Terraform e IaC

## Bicep
- DSL declarativo da Microsoft
- Mais legível que JSON
- Compila para ARM

**Exemplo Bicep:**

```bicep
param location string = resourceGroup().location
resource st 'Microsoft.Storage/storageAccounts@2021-04-01' = {
  name: 'st${uniqueString(resourceGroup().id)}'
  location: location
  sku: { name: 'Standard_LRS' }
  kind: 'StorageV2'
}
```

## Terraform
- Multi-cloud, da HashiCorp
- Usa state (preferencialmente remoto)
- Bom para ambientes híbridos

**Recomendação:**

- Use Bicep se o foco é Azure puro
- Use Terraform se há multi-cloud

---

# 9. Azure Arc
O que é: Extensão do Azure para gerenciar recursos fora do Azure.

**Capacidades:**

- Registrar servidores, Kubernetes e bancos de dados
- Aplicar políticas e RBAC a recursos híbridos
- Centralizar inventário e monitoramento

**Casos de uso:**

- Gestão híbrida/multicloud
- Governança unificada
- Modernização gradual de workloads

---

# 10. Integração com CI/CD

**Boas práticas:**

- Armazenar templates no Git
- Usar pipelines para validação, teste e deploy
- Preferir credenciais seguras (SP ou Managed Identity)

**Exemplo (GitHub Actions + Bicep):**

```yaml
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: azure/login@v1
        with:
          creds: ${{ secrets.AZURE_CREDENTIALS }}
      - uses: azure/cli@v1
        with:
          inlineScript: az deployment group create -g meu-rg --template-file infra/main.bicep
```

---

# 11. Segurança, RBAC e Governança

- Princípio do menor privilégio
- Managed Identities em vez de secrets
- Azure Policy + Blueprints para padronização
- Auditorias com Activity Logs
- Secrets no Azure Key Vault

---

# 12. Troubleshooting e dicas

- Validar templates antes do deploy (az deployment group validate)
- Monitorar quotas no Portal
- Usar --debug / --verbose para detalhes
- Testar primeiro em ambientes de dev

---

# 13. Referências

Portal do Azure — https://portal.azure.com

Azure Cloud Shell — https://learn.microsoft.com/azure/cloud-shell/overview

Azure CLI — https://learn.microsoft.com/cli/azure/

Azure PowerShell — https://learn.microsoft.com/powershell/azure/

Azure Resource Manager — https://learn.microsoft.com/azure/azure-resource-manager/management/overview

Bicep — https://learn.microsoft.com/azure/bicep/

Terraform + Azure — https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs

Azure Arc — https://learn.microsoft.com/azure/azure-arc/overview

