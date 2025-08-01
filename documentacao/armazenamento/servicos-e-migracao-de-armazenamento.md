# 📦 Armazenamento no Azure – Arquitetura e Serviços

Este documento apresenta uma visão geral dos serviços, opções e ferramentas de armazenamento na plataforma Microsoft Azure. É voltado para profissionais que desejam compreender como configurar, gerenciar, mover e comparar serviços de armazenamento em nuvem com eficiência.

---

## 🧰 1. Serviços de Armazenamento do Azure

| Serviço              | Finalidade                                                                 |
|----------------------|---------------------------------------------------------------------------|
| **Blob Storage**     | Armazenamento de objetos não estruturados (imagens, vídeos, backups etc.) |
| **File Storage**     | Compartilhamentos SMB/REST, ideal para servidores e aplicações             |
| **Queue Storage**    | Fila de mensagens para comunicação assíncrona entre componentes            |
| **Table Storage**    | Armazenamento NoSQL para dados estruturados simples                        |
| **Disk Storage**     | Discos gerenciados usados em Máquinas Virtuais                             |

---

## 🗃️ 2. Tipos de Conta de Armazenamento

| Tipo                   | Características principais                                                |
|------------------------|---------------------------------------------------------------------------|
| **General-purpose v2** | Suporta todos os serviços (blobs, arquivos, filas, tabelas, discos)       |
| **Blob Storage**       | Focado exclusivamente em blobs, com suporte a camadas de acesso           |
| **FileStorage**        | Otimizado para compartilhamentos de arquivos com alta performance         |
| **BlockBlobStorage**   | Armazenamento Premium otimizado para blobs em blocos                      |

---

## 🧊 3. Camadas de Acesso (Blob Storage)

| Camada      | Uso típico                        | Armazenamento 💰 | Acesso 📥 |
|-------------|------------------------------------|------------------|-----------|
| **Hot**     | Dados acessados com frequência     | Alto             | Baixo     |
| **Cool**    | Dados pouco acessados (≥30 dias)   | Médio            | Médio     |
| **Archive** | Dados raros (≥180 dias)            | Baixo            | Alto (com reidratação) |

---

## 🛡️ 4. Opções de Redundância

| Tipo      | Localização         | Cópias   | Ideal para...                    |
|-----------|---------------------|----------|----------------------------------|
| **LRS**   | Dentro do datacenter| 3        | Cenários locais, menor custo     |
| **ZRS**   | Zonas da mesma região| 3       | Alta disponibilidade local       |
| **GRS**   | Região secundária    | 6 (3+3)  | Continuidade de negócios         |
| **GZRS**  | Zonas + região extra | 6        | Alta resiliência + DR completo   |

---

## 🌐 5. Pontos de Extremidade Críticos

- **Público**: Acesso via internet por URLs como `https://<conta>.blob.core.windows.net`
- **Privado (Private Endpoint)**: Acesso interno via rede privada (VNet)

> Escolher corretamente entre público e privado é essencial para segurança e conformidade.

---

## 🧮 6. Comparando Serviços de Armazenamento

| Critério        | Blob Storage           | Azure Files             | Disk Storage        |
|------------------|------------------------|--------------------------|---------------------|
| Objetivo         | Objetos não estruturados| Compartilhamento de arquivos| Discos de VM    |
| Protocolos       | REST/HTTPS              | SMB / REST               | SCSI                |
| Redundância      | LRS, ZRS, GRS, GZRS     | LRS, ZRS                 | LRS, ZRS            |
| Performance      | Hot/Cool/Archive        | Standard / Premium       | Standard / Premium SSD |

---

## 🔄 7. Gerenciamento e Sincronização de Arquivos

Ferramentas úteis para copiar, sincronizar e administrar arquivos entre ambientes locais e a nuvem Azure:

- **AzCopy**  
  Ferramenta de linha de comando (CLI) otimizada para transferências de alto desempenho de dados entre seu sistema local e o Azure Storage (Blob, File e Table).  
  ✅ Ideal para automações, scripts e cargas recorrentes ou grandes.  
  🔧 Suporta autenticação com SAS Token, Azure AD e Chave de Conta.

- **Microsoft Azure Storage Explorer**  
  Interface gráfica gratuita que permite gerenciar dados no Azure Storage com facilidade.  
  ✅ Permite visualizar, mover, excluir, baixar ou fazer upload de arquivos Blob, Files, Queues e Tables.  
  🔍 Excelente para times não técnicos, ambientes de suporte e análise rápida de estruturas.

- **Azure File Sync**  
  Solução de sincronização bidirecional entre compartilhamentos de arquivos locais (servidores Windows) e o Azure Files.  
  ✅ Funciona como cache local com replicação automática para a nuvem.

---

## 🚚 8. Migrações para o Azure

### Opções disponíveis:

| Método/Ferramenta      | Descrição                                                                 |
|------------------------|---------------------------------------------------------------------------|
| **Azure Migrate**      | Plataforma unificada para descoberta, avaliação e migração de servidores, bancos de dados e arquivos. |
| **Azure Data Box**     | Solução física fornecida pela Microsoft para migração de grandes volumes de dados offline, ideal para locais com pouca conectividade ou projetos com alta sensibilidade de dados.  
Microsoft envia o dispositivo, o cliente o preenche localmente, e o devolve para upload nos datacenters Azure.  
Tipos disponíveis:  
  - **Data Box Disk** (até 40 TB)  
  - **Data Box** (até 100 TB)  
  - **Data Box Heavy** (até 1 PB) |
| **AzCopy / Storage Explorer** | Ferramentas recomendadas para cargas pequenas ou médias.  
AzCopy é voltado para automação e desempenho, enquanto o Storage Explorer oferece uma abordagem visual para administração pontual. |
| **Azure File Sync**    | Além da sincronização contínua, também pode ser usado como forma de migração progressiva e segura de dados para a nuvem. |

---

## 📌 Conclusão

Entender os serviços de armazenamento no Azure é essencial para soluções escaláveis e seguras. Escolher o tipo de armazenamento adequado, definir corretamente a camada de acesso e aplicar boas práticas de redundância pode impactar diretamente no desempenho, resiliência e custo de sua solução.

---

## 🔗 Referências

- [Azure Storage Overview](https://learn.microsoft.com/pt-br/azure/storage/)
- [Tipos de Redundância](https://learn.microsoft.com/pt-br/azure/storage/common/storage-redundancy)
- [Camadas de Acesso - Blob](https://learn.microsoft.com/pt-br/azure/storage/blobs/access-tiers-overview)
- [AzCopy](https://learn.microsoft.com/pt-br/azure/storage/common/storage-use-azcopy-v10)
- [Azure Migrate](https://learn.microsoft.com/pt-br/azure/migrate/)
- [Azure Data Box](https://learn.microsoft.com/pt-br/azure/databox/)
