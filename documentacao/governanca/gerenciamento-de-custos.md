# 💰 Gerenciamento de Custos no Azure

Este documento oferece uma visão detalhada das ferramentas, conceitos e práticas para **controlar e otimizar custos** na Microsoft Azure.  
O objetivo é ajudar profissionais e equipes a planejarem, monitorarem e gerirem seus gastos de forma eficaz, utilizando recursos nativos da plataforma.

---

## 🧮 1. Calculadoras e Ferramentas de Custo

A **Microsoft Azure** disponibiliza ferramentas para estimar, acompanhar e analisar custos de forma prática:

### 1.1 Calculadora de Preços
- Disponível no portal público da Azure.
- Permite **estimar custos antes da implementação**.
- Útil para criar simulações e avaliar diferentes configurações.
- Fornece valores por região, camada de serviço e tipo de recurso.

### 1.2 Calculadora de Custo Total de Propriedade (TCO)
- Compara custos **on-premises** vs. **Azure**.
- Considera despesas com infraestrutura física, manutenção, energia, resfriamento e pessoal.
- Ideal para projetos de **migração para nuvem**.

### 1.3 Comparativo entre Calculadora de Preços e TCO
| Ferramenta       | Objetivo Principal                                  | Quando Usar |
|------------------|----------------------------------------------------|-------------|
| **Preços**       | Estimar custos futuros de um recurso/serviço       | Antes de criar recursos |
| **TCO**          | Comparar custos de nuvem vs. local                  | Planejamento de migração |

---

## 📊 2. Gerenciamento de Custos no Azure

A **Ferramenta de Gerenciamento de Custos e Cobrança** do Azure (Cost Management + Billing) oferece:
- **Monitoramento contínuo** de gastos.
- Relatórios personalizados por período, recurso ou grupo.
- Definição de **alertas** e **orçamentos**.
- Segmentação de custos por **marcas (tags)** ou assinaturas.

---

## 🏷️ 3. Marcas (Tags) no Azure

As **tags** são metadados atribuídos a recursos para organização e controle:

- **Formato**: pares `nome : valor`.
- **Objetivo**: classificar recursos de forma lógica (ex.: `Projeto:ERP`, `Ambiente:Produção`).
- **Benefícios**:
  - Agrupamento de custos por projeto, cliente ou departamento.
  - Facilita automação e políticas de governança.
  - Ajuda na cobrança interna (chargeback/showback).

> **Boas práticas**: definir um padrão corporativo de nomenclatura para tags e aplicá-las automaticamente via **Azure Policy**.

---

## 💡 4. Fatores que Afetam os Custos

O custo no Azure depende de vários fatores. Entre os principais:

| Fator             | Impacto no Custo                                                      |
|-------------------|-----------------------------------------------------------------------|
| **Tipo de recurso**| Recursos premium ou de alto desempenho custam mais                   |
| **Consumo**        | Cobrança proporcional ao uso (pay-as-you-go)                         |
| **Manutenção**     | Recursos inativos ainda podem gerar custo                            |
| **Área geográfica**| Preços variam entre regiões                                          |
| **Tráfego de rede**| Transferências entre regiões/saída para internet têm custo           |
| **Assinatura**     | Diferenças de preços por tipo de contrato/licenciamento              |

---

## 🛒 5. Azure Marketplace e Custos

O **Azure Marketplace** oferece soluções de terceiros integradas à nuvem.  
Ao considerar custos:
- Alguns serviços possuem cobrança separada da infraestrutura.
- Licenças de software e suporte podem ser incluídas na fatura Azure.
- É importante verificar modelos de precificação antes de implantar.

---

## 📏 6. Calculando o Custo Total no Azure

Ao projetar ou migrar soluções, o cálculo do **Custo Total de Propriedade (TCO)** é essencial para:
- Justificar investimentos.
- Comparar modelos de nuvem e local.
- Evitar custos inesperados no longo prazo.

A calculadora TCO da Microsoft permite:
- Inserir quantidades e tipos de recursos físicos existentes.
- Estimar economia em energia, manutenção e pessoal.
- Exportar relatórios para apresentação executiva.

---

## 📚 7. Revisão – Gerenciamento de Custos

O gerenciamento de custos no Azure combina:
- **Planejamento** (calculadoras, simulações).
- **Monitoramento** (Cost Management + Billing).
- **Otimização** (tags, políticas, ajustes de consumo).
- **Análise contínua** (identificação de desperdícios e ajustes).

> Uma estratégia eficaz de custos envolve **monitorar, otimizar e revisar** periodicamente as necessidades da empresa.

---

## 🔗 Referências

- [Calculadora de Preços Azure](https://azure.microsoft.com/pt-br/pricing/calculator/)
- [Calculadora TCO Azure](https://azure.microsoft.com/pt-br/pricing/tco/calculator/)
- [Azure Cost Management + Billing](https://learn.microsoft.com/pt-br/azure/cost-management-billing/)
- [Boas práticas de uso de Tags](https://learn.microsoft.com/pt-br/azure/azure-resource-manager/management/tag-resources)
- [Azure Marketplace](https://azuremarketplace.microsoft.com/)
