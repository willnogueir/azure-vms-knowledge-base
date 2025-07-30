# 💾 Contas de Armazenamento no Azure e Tipos de Replicação

## O que é uma Conta de Armazenamento?

Uma Conta de Armazenamento no Azure é um recurso que permite armazenar dados na nuvem, como blobs (arquivos), arquivos, tabelas e filas. É o container lógico que organiza e gerencia esses dados, definindo políticas de segurança, acesso e replicação.

## Tipos de Replicação no Azure Storage

A replicação garante que seus dados estejam disponíveis e seguros, mesmo em casos de falhas físicas ou desastres. Veja os principais tipos:

| Sigla  | Nome Completo                  | Descrição                                                                                           |
|--------|-------------------------------|---------------------------------------------------------------------------------------------------|
| **LRS**  | Locally Redundant Storage     | Replicação local com 3 cópias síncronas dentro de um mesmo datacenter. Protege contra falhas de hardware locais. |
| **GRS**  | Geo-Redundant Storage         | Replicação local + replicação assíncrona para outro datacenter em uma região diferente, protegendo contra desastres regionais. |
| **ZRS**  | Zone-Redundant Storage        | Replicação síncrona entre zonas de disponibilidade dentro da mesma região, garantindo alta disponibilidade. |
| **GZRS** | Geo-Zone-Redundant Storage    | Combinação de ZRS + replicação assíncrona para outra região, proporcionando máxima durabilidade e resiliência. |

## Quando usar cada tipo?

| Tipo | Uso Recomendado                                    | Custo           |
|-------|---------------------------------------------------|-----------------|
| **LRS** | Aplicações menos críticas que precisam de proteção contra falhas locais. | Baixo           |
| **GRS** | Aplicações que precisam garantir durabilidade e recuperação contra desastres regionais. | Médio           |
| **ZRS** | Aplicações que precisam de alta disponibilidade dentro da mesma região. | Médio-Alto      |
| **GZRS**| Aplicações críticas que necessitam máxima durabilidade e resiliência geográfica. | Mais alto       |

## Resumo

- **LRS**: 3 cópias no mesmo datacenter.
- **GRS**: LRS + replicação para região geograficamente separada.
- **ZRS**: 3 cópias distribuídas entre zonas dentro da mesma região.
- **GZRS**: ZRS + replicação para outra região geográfica.

---

## Referências

- [Visão geral da replicação no Azure Storage](https://learn.microsoft.com/pt-br/azure/storage/common/storage-redundancy)
- [Tipos de conta e replicação do Azure Storage](https://learn.microsoft.com/pt-br/azure/storage/common/storage-account-overview)
