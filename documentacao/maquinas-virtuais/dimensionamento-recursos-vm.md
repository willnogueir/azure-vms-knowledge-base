## 🔧 Recursos Personalizáveis ao Criar uma VM

Ao provisionar uma VM no Azure, você pode ajustar os seguintes parâmetros:

### 🔹 Tamanho (SKU)

- Representa o conjunto de recursos alocados: CPU, RAM, tipo de disco, etc.
- Classificações comuns:
  - **B-series**: Econômicas, ideais para cargas intermitentes.
  - **D-series**: Uso geral, bom equilíbrio entre CPU e RAM.
  - **E-series**: Otimizada para memória.
  - **F-series**: Otimizada para CPU.
  - **NV/NC/ND**: GPU para computação gráfica e científica.
- O tamanho afeta diretamente o custo **por hora** da instância.

### 🔹 Tipo de Disco

- **Standard HDD**: Mais barato, menor performance.
- **Standard SSD**: Intermediário, boa relação custo/benefício.
- **Premium SSD**: Alta performance, ideal para bancos e apps críticos.
- **Ultra Disk**: Altíssima IOPS e latência mínima (uso específico).

### 🔹 Sistema Operacional

- Windows Server (várias versões)
- Distribuições Linux (Ubuntu, CentOS, Debian, RHEL, SUSE)

### 🔹 Região

- Determina onde fisicamente a VM será hospedada.
- Impacta: latência, conformidade e custo.

---

## 📈 Dimensionamento Vertical e Horizontal

### 🔸 Dimensionamento Vertical (Scale-Up)

- Alterar para uma VM maior (mais vCPU/RAM).
- Necessário reiniciar a VM.
- Ideal para cargas únicas com picos previsíveis.

### 🔸 Dimensionamento Horizontal (Scale-Out)

- Adição de múltiplas instâncias da mesma VM.
- Utiliza **Conjuntos de Dimensionamento (VMSS)**.
- Ideal para cargas distribuídas (web apps, APIs).

---

## 🧠 Conhecimentos Necessários para Dimensionamento Eficiente

1. **Carga de Trabalho Esperada**:
   - Número de usuários simultâneos
   - Aplicações executadas
   - Consumo de CPU/RAM durante picos

2. **SLAs e Disponibilidade**:
   - Se for necessário SLA de 99,99%, use Zonas de Disponibilidade ou VMSS.

3. **Escalabilidade**:
   - Precisa de elasticidade automática? Considere VMSS ou PaaS.

4. **Custos**:
   - Utilize a [Calculadora do Azure](https://azure.microsoft.com/pt-br/pricing/calculator/)
   - Considere licenças incluídas (ex: Windows Server) ou BYOL.

---

## 💡 Boas Práticas

- Teste o desempenho em uma VM menor e vá escalando.
- Use **monitoramento via Azure Monitor** para avaliar consumo real.
- Planeje o **uso de tags** para rastrear custos e propósito das VMs.
- Utilize **Templates ARM ou Bicep** para padronizar configurações.

---

## 🔗 Recursos Úteis

- [Tamanhos de VMs no Azure](https://learn.microsoft.com/pt-br/azure/virtual-machines/sizes)
- [Azure Pricing Calculator](https://azure.microsoft.com/pt-br/pricing/calculator/)
- [Documentação de Discos Gerenciados](https://learn.microsoft.com/pt-br/azure/virtual-machines/disks-types)
