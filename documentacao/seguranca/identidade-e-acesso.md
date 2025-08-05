# 🔐 Identidade, Acesso e Segurança no Azure

A segurança em ambientes de nuvem como o Microsoft Azure começa com uma base sólida de **identidade e controle de acesso**. Este documento explora os principais componentes arquitetônicos relacionados à segurança, com foco na **autenticação**, **autorização**, **acesso condicional** e **serviços de diretório**, utilizando recursos como o **Microsoft Entra ID**.

---

## 🧭 1. Fundamentos de Identidade e Segurança no Azure

A arquitetura de segurança do Azure é baseada em **camadas de proteção** que abrangem desde os datacenters físicos até o acesso a dados e aplicativos. Essas camadas incluem:

1. **Segurança Física**
2. **Identidade e Acesso**
3. **Perímetro**
4. **Rede**
5. **Computação**
6. **Aplicativos**
7. **Dados**

🔐 A camada de **Identidade e Acesso** é a mais crítica, pois, na nuvem, a identidade é o novo perímetro.

---

## 📛 2. Microsoft Entra ID (anteriormente Azure Active Directory)

O **Microsoft Entra ID** é a solução de **gerenciamento de identidade e acesso baseada em nuvem da Microsoft**. Ele permite controlar o acesso a recursos do Azure, Microsoft 365 e aplicativos de terceiros.

### Principais recursos:

- Autenticação única (SSO)
- Multi-Factor Authentication (MFA)
- Integração com Active Directory local (sincronização híbrida)
- Atribuição de papéis (RBAC)
- Acesso condicional
- Gestão de identidades externas (B2B e B2C)

---

## 🧱 3. Serviços de Diretório e Domain Services

### Microsoft Entra Domain Services (anteriormente Azure AD DS)

- Fornece **domínio gerenciado** compatível com **Active Directory**, sem necessidade de implantar controladores de domínio.
- Suporta **autenticação NTLM/Kerberos**, **GPOs** e **ingresso de máquinas ao domínio**.
- Ideal para workloads legados em máquinas virtuais que exigem AD tradicional.

---

## 🔑 4. Métodos de Autenticação

O Azure oferece suporte a diversos métodos de autenticação, ajustando-se a diferentes níveis de segurança e cenários de integração.

| Método de Autenticação      | Descrição                                                   |
|-----------------------------|-------------------------------------------------------------|
| Senha (tradicional)         | Mais comum, mas menos seguro isoladamente                   |
| MFA                         | Requer dois ou mais fatores (senha + celular, por exemplo)  |
| Autenticação baseada em certificado | Comum em cenários corporativos e dispositivos gerenciados |
| FIDO2 / Chave de segurança  | Autenticação forte sem senha, baseada em hardware           |
| Smartcard                   | Utilizada em ambientes corporativos integrados              |

---

## 👥 5. Autorização e RBAC (Role-Based Access Control)

O controle de acesso baseado em função (RBAC) permite atribuir permissões específicas com base em **funções predefinidas** (como Leitor, Colaborador, Administrador).

Exemplo:
- Um usuário com papel de "Leitor" pode visualizar, mas não modificar recursos.
- "Colaborador" pode modificar recursos, mas não atribuir permissões.

---

## ⚙️ 6. Acesso Condicional

A **política de acesso condicional** permite aplicar controles granulares com base em condições como:

- Localização geográfica
- Dispositivo em conformidade
- Grupo de usuários
- Tipo de aplicativo
- Nível de risco da sessão

Exemplos de políticas:
- Exigir MFA ao acessar fora do país
- Bloquear acesso de dispositivos não gerenciados
- Restringir login de contas de convidados

---

## 🧷 7. Modelo de Segurança em Camadas – "Proteção Completa"

A Microsoft propõe uma abordagem de segurança baseada em **defesa em profundidade** com as seguintes camadas:

Segurança Física > Identidade e Acesso > Perímetro > Rede > Computação > Aplicativo > **Dados**

Cada camada é responsável por proteger a anterior e reforçar a próxima. A **Identidade** é o centro da estratégia, e a implementação adequada de autenticação, autorização e acesso condicional é a base da resiliência na nuvem.

---

## 🔁 8. Revisão: Identidade, Acesso e Segurança

| Conceito                         | Finalidade                                                                 |
|----------------------------------|----------------------------------------------------------------------------|
| **Microsoft Entra ID**           | Gerenciar identidades e acessos a recursos na nuvem                       |
| **Domain Services (Azure AD DS)**| Emular funcionalidades do AD tradicional na nuvem                         |
| **Autenticação**                 | Verificar identidade do usuário (senha, MFA, certificado, etc.)           |
| **Autorização (RBAC)**           | Definir o que o usuário pode fazer com base em sua função                 |
| **Acesso Condicional**           | Aplicar regras inteligentes para permitir ou bloquear o acesso            |
| **Modelo de Camadas**            | Defesa em profundidade com foco em identidade e proteção integrada        |

---

## 📌 Leitura complementar

- [Visão geral do Microsoft Entra ID](https://learn.microsoft.com/pt-br/entra/identity/)
- [Conceitos de Acesso Condicional](https://learn.microsoft.com/pt-br/azure/active-directory/conditional-access/)
- [Comparação entre Entra ID e Domain Services](https://learn.microsoft.com/pt-br/azure/active-directory-domain-services/compare-azure-ad)
- [Defesa em profundidade – Microsoft Docs](https://learn.microsoft.com/pt-br/security/zero-trust/deploy/defense-in-depth)


