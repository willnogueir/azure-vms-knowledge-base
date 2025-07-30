# 📊 SLA de Máquinas Virtuais na Azure

Este documento apresenta os Acordos de Nível de Serviço (SLA) oferecidos pela Microsoft para Máquinas Virtuais (VMs) na Azure, além de uma análise do tempo máximo estimado de indisponibilidade permitido para cada nível de SLA.

---

## 🛡️ O que é SLA?

SLA (Service Level Agreement) é o compromisso assumido pela Microsoft sobre a **disponibilidade mínima garantida** de um serviço.

No contexto das VMs da Azure, o SLA varia conforme a arquitetura da implantação (por exemplo, uso de instâncias isoladas, conjuntos de disponibilidade ou zonas de disponibilidade).

---

## 📈 Tabela de SLA e Indisponibilidade Estimada

| SLA Garantido | Tempo Máximo de Indisponibilidade por Semana | Por Mês (30 dias) | Por Ano (365 dias) |
|---------------|-----------------------------------------------|--------------------|---------------------|
| 99%           | 1 h 40 min 48 s                               | 7 h 18 min         | 87 h 36 min 30 s    |
| 99.9%         | 10 min 4 s                                    | 43 min 49 s        | 8 h 45 min 57 s     |
| 99.95%        | 5 min 2 s                                     | 21 min 54 s        | 4 h 22 min 58 s     |
| 99.99%        | 1 min 0 s                                     | 4 min 23 s         | 52 min 36 s         |
| 99.999%       | 6 s                                           | 26 s               | 5 min 15 s          |

> ℹ️ *Os valores são arredondados para facilitar a leitura e baseiam-se em semanas de 7 dias, meses de 30 dias e ano de 365 dias.*

---

## 🧠 Exemplos de Aplicação

- **99%**: Serviços legados ou workloads não críticos sem alta disponibilidade.
- **99.9%**: VM isolada sem conjunto de disponibilidade.
- **99.95%**: Duas ou mais VMs em um mesmo *Availability Set*.
- **99.99%**: VMs distribuídas em diferentes *Availability Zones*.
- **99.999%**: Exige soluções altamente distribuídas com redundância e balanceamento global, normalmente fora do escopo padrão de VMs.

---

## 📌 Observações

- A **Azure não oferece SLA** para uma única VM se ela estiver implantada sozinha sem medidas de alta disponibilidade.
- Em caso de descumprimento do SLA, o cliente pode solicitar **créditos financeiros** de acordo com a política da Microsoft.

---

## 🔗 Referências Oficiais

- [SLA da Azure para VMs (Documentação Microsoft)](https://learn.microsoft.com/pt-br/azure/virtual-machines/sla)
- [SLA oficial da Microsoft](https://azure.microsoft.com/pt-br/support/legal/sla/summary/)
