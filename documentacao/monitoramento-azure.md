# Ferramentas de Monitoramento no Azure

Este documento traz um resumo didático e detalhado das principais ferramentas de monitoramento do Azure. Apresenta conceitos, funcionalidades, benefícios e exemplos práticos para cada ferramenta.

---

## 1. Assistente do Azure (Azure Advisor)

O **Assistente do Azure** é uma ferramenta gratuita e automatizada que avalia suas configurações e uso do Azure para fornecer recomendações práticas que ajudam a otimizar seu ambiente em cinco pilares:

| Pilar                  | O que significa                               | Benefícios principais                               |
|------------------------|-----------------------------------------------|----------------------------------------------------|
| **Confiabilidade**     | Garantir disponibilidade e recuperação        | Minimiza downtime, aumenta resiliência              |
| **Segurança**          | Fortalecer segurança do ambiente               | Reduz riscos de vulnerabilidades                      |
| **Desempenho**         | Melhorar velocidade e eficiência dos recursos | Otimiza uso e tempo de resposta                       |
| **Custo**              | Reduzir gastos desnecessários                   | Economia financeira sem perda de qualidade           |
| **Excelência Operacional** | Melhores práticas em governança e operação     | Facilita manutenção e escalabilidade                   |

### Como funciona?
- O Azure Advisor analisa automaticamente sua assinatura e recursos.
- Gera relatórios com recomendações acionáveis.
- Você pode filtrar as recomendações por categoria e prioridade.

### Exemplo prático:
> Um recurso com baixa utilização pode ser redimensionado para uma SKU menor, gerando economia imediata, recomendação que o Advisor sugere com detalhes.

---

## 2. Integridade do Serviço do Azure (Azure Service Health)

O **Azure Service Health** é a sua fonte confiável para acompanhar o status do Azure e seu impacto nos seus recursos.

| Tipo de Informação     | Descrição                                      | Como ajuda                                         |
|-----------------------|------------------------------------------------|---------------------------------------------------|
| **Alertas de Incidente** | Problemas ativos que impactam serviços          | Permite ação rápida para mitigar impacto           |
| **Manutenção Planejada** | Eventos futuros programados no Azure            | Ajuda a planejar atualizações e evitar surpresas   |
| **Recomendações Personalizadas** | Impactos específicos em seus recursos          | Informação focada no que realmente importa para você |

### Funcionalidades principais:
- Notificações configuráveis via email, SMS, webhook ou eventos.
- Painel centralizado para visualizar incidentes em todas as regiões.
- Histórico de incidentes para análise e auditoria.

---

## 3. Resource Health

O **Resource Health** é focado no estado de saúde dos recursos individuais. Ele responde à pergunta: "Por que meu recurso está com problema?"

| Aspecto                | Descrição                                      | Exemplo prático                                   |
|------------------------|------------------------------------------------|-------------------------------------------------|
| **Status atual**       | Disponível, Intermitente, Indisponível         | Indica se a VM está ativa ou em falha             |
| **Causa do problema**  | Se o problema foi causado pelo Azure ou pelo usuário | Ajuda a direcionar o suporte correto                |
| **Histórico de eventos** | Registro dos incidentes passados                | Facilita análise de tendências de problemas       |

### Benefícios:
- Diagnóstico rápido e localizado.
- Transparência sobre a responsabilidade do problema.
- Base para troubleshooting detalhado.

---

## 4. Azure Monitor

O **Azure Monitor** é a solução mais completa para monitoramento e análise, cobrindo infraestrutura, aplicações e dados.

### Principais componentes

| Componente            | Finalidade                                     | Exemplos de uso                                   |
|-----------------------|------------------------------------------------|-------------------------------------------------|
| **Azure Log Analytics** | Coleta e análise de logs e dados de telemetria  | Pesquisa customizada em logs de VMs e apps       |
| **Alertas do Azure Monitor** | Notificações baseadas em métricas e logs         | Alertar equipe se CPU ultrapassar 90%             |
| **Application Insights** | Monitoramento avançado para aplicações         | Métricas detalhadas de performance e erros web    |

### Funcionalidades adicionais

- Dashboards personalizáveis para visão consolidada.
- Integração com Power BI e outras ferramentas analíticas.
- Suporte a análises preditivas e automações via Logic Apps.

---

## Exemplo: Criar um alerta básico no Azure Monitor

```powershell
New-AzMetricAlertRuleV2 -ResourceGroupName "meu-rg" -Name "AlertaCPUAlta" `
  -TargetResourceId "/subscriptions/{subscriptionId}/resourceGroups/meu-rg/providers/Microsoft.Compute/virtualMachines/minhaVM" `
  -Condition "Percentage CPU > 80" -WindowSize 5 -Frequency 1 -ActionGroupId "/subscriptions/{subscriptionId}/resourceGroups/meu-rg/providers/microsoft.insights/actionGroups/myActionGroup"
