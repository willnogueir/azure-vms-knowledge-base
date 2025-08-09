# 🛡️ Governança e Conformidade no Azure

A **Governança e Conformidade** no Azure garante que recursos sejam criados, gerenciados e monitorados de forma alinhada com requisitos de **segurança, normas legais, políticas corporativas e boas práticas de TI**.  

Este documento apresenta os principais recursos, ferramentas e práticas que auxiliam na implementação de governança efetiva e conformidade no Azure.

---

## 1. Visão Geral da Governança no Azure

A governança garante:
- **Conformidade** com requisitos regulatórios e internos.
- **Consistência** na criação e manutenção dos recursos.
- **Proteção** contra alterações acidentais ou maliciosas.
- **Monitoramento e auditoria** contínuos.

No Azure, a governança é aplicada por meio de **políticas, modelos, bloqueios e ferramentas de auditoria** que trabalham em conjunto para proteger e organizar o ambiente.

---

## 2. Azure Policy

O **Azure Policy** é o serviço responsável por criar, atribuir e gerenciar políticas que impõem regras sobre recursos.  
Ele **monitora, avalia e aplica** conformidade automaticamente.

**Exemplos de uso:**
- Permitir a criação de recursos apenas em regiões autorizadas.
- Exigir que todas as contas de armazenamento usem criptografia.
- Padronizar tamanhos de máquinas virtuais.

| Recurso | Objetivo | Benefício |
|---------|----------|-----------|
| **Política de Localização** | Restringir regiões de criação de recursos | Conformidade regulatória |
| **Política de Tag** | Exigir tags em recursos | Organização e gestão de custos |
| **Política de Criptografia** | Forçar criptografia em armazenamento | Segurança de dados |

**Benefícios:**
- Aplicação centralizada de regras.
- Automação da conformidade.
- Relatórios de auditoria em tempo real.

---

## 3. Azure Blueprints

O **Azure Blueprints** é utilizado para **padronizar a criação de ambientes** com configurações, políticas e recursos pré-definidos.

**O que pode incluir:**
- Modelos ARM.
- Políticas do Azure Policy.
- Grupos de recursos.
- Funções de RBAC.

**Vantagens:**
- Consistência entre ambientes de produção, teste e desenvolvimento.
- Redução de erros humanos na configuração.
- Facilita o cumprimento de padrões de conformidade desde a criação do recurso.

---

## 4. Bloqueios de Recursos

Bloqueios protegem recursos contra exclusões ou alterações acidentais.

**Tipos de bloqueio:**
| Tipo de Bloqueio | Ação Impedida | Uso Recomendado |
|------------------|--------------|-----------------|
| **Excluir (Delete)** | Impede exclusão do recurso | Recursos críticos |
| **Somente Leitura (ReadOnly)** | Impede exclusão e alteração | Recursos com configuração estável |

**Onde aplicar:**
- **Assinatura** → Protege todo o ambiente.
- **Grupo de Recursos** → Protege conjunto de recursos relacionados.
- **Recurso Individual** → Protege apenas aquele recurso específico.

---

## 5. Service Trust Portal (Portal de Confiança e Serviço)

O **Service Trust Portal** fornece:
- **Relatórios de auditoria e certificações** (ISO, SOC, GDPR, LGPD).
- **Documentação sobre práticas de segurança** da Microsoft.
- **Recursos de conformidade** para auditorias internas.

**Finalidade:**  
Dar visibilidade e transparência sobre a postura de segurança e conformidade da Microsoft, permitindo que empresas validem se o Azure atende suas obrigações regulatórias.

---

## 6. Microsoft Purview

O **Microsoft Purview** é a plataforma de **governança, risco e conformidade de dados** no Azure.

**Principais funcionalidades:**
- **Descoberta automatizada** de ativos de dados.
- **Classificação de dados confidenciais** (ex.: CPF, cartão de crédito, dados de saúde).
- **Linhagem de dados** para rastrear movimentações e transformações.
- **Políticas de retenção e prevenção de perda de dados (DLP)**.

**Quando usar:**
- Empresas que precisam cumprir LGPD, GDPR, HIPAA.
- Ambientes com grande volume de dados distribuídos em várias fontes.
- Necessidade de auditoria detalhada sobre fluxo e segurança dos dados.

---

## 7. Boas Práticas de Governança no Azure

- **Defina políticas no nível mais alto possível** (Assinatura ou Grupo de Gerenciamento).
- **Use Blueprints** para padronizar ambientes críticos.
- **Aplique bloqueios** em recursos de produção.
- **Monitore continuamente** a conformidade via Azure Policy.
- **Utilize o Microsoft Purview** para gestão de dados sensíveis.
- **Consulte o Service Trust Portal** para auditorias e certificações.

---

## 8. Resumo Visual

Governança no Azure:
├── Definição de Políticas → Azure Policy
├── Padronização de Ambientes → Azure Blueprints
├── Proteção de Recursos → Bloqueios
├── Transparência e Auditoria → Service Trust Portal
└── Governança de Dados → Microsoft Purview

---
