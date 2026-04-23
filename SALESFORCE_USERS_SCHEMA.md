# 📊 Documentação - Schema de Usuários Salesforce

## Visão Geral
Esta documentação descreve a estrutura de dados da tabela `raw__salesforce__arco.current__user`, que contém informações centralizadas dos usuários do Salesforce.

## Tabela: `raw__salesforce__arco.current__user`

### Campos de Identificação

| Campo | Tipo | Descrição |
|-------|------|-----------|
| `id` | String (PK) | Identificador único do usuário |
| `username` | String | Nome de usuário para login |
| `email` | String | Endereço de email do usuário |
| `alias` | String | Apelido/alias do usuário |

### Informações Pessoais

| Campo | Tipo | Descrição |
|-------|------|-----------|
| `name` | String | Nome completo do usuário |
| `firstname` | String | Primeiro nome |
| `lastname` | String | Sobrenome |
| `title` | String | Cargo/título profissional |

### Informações Organizacionais

| Campo | Tipo | Descrição |
|-------|------|-----------|
| `companyname` | String | Nome da empresa |
| `department` | String | Departamento |
| `division` | String | Divisão |
| `managerid` | String | ID do gerente direto |
| `profileid` | String | ID do perfil Salesforce |
| `user_role_id` | String | ID da função/papel na hierarquia |
| `usertype` | String | Tipo de usuário (Standard, CRM, etc) |

### Campos Customizados (Custom Fields)

| Campo | Tipo | Descrição |
|-------|------|-----------|
| `brand__c` | String | Marca associada |
| `mainbrand__c` | String | Marca principal |
| `segment__c` | String | Segmento de negócio |
| `profilename__c` | String | Nome do perfil customizado |
| `position__c` | String | Posição/Cargo customizado |
| `core__c` | String | Core de negócio |
| `departament__c` | String | Departamento customizado |
| `directorship__c` | String | Diretoria |
| `insidesales__c` | Boolean | Indicador de vendas internas |

### Campos de Status

| Campo | Tipo | Descrição |
|-------|------|-----------|
| `isactive` | Boolean | Status ativo/inativo do usuário |
| `lastlogindate` | DateTime | Data do último login |

### Campos de Auditoria

| Campo | Tipo | Descrição |
|-------|------|-----------|
| `createddate` | DateTime | Data de criação do registro |
| `lastmodifieddate` | DateTime | Data da última modificação |
| `lastmodifiedbyid` | String | ID do usuário que fez a última modificação |
| `systemmodstamp` | DateTime | Timestamp de modificação do sistema |

### Campos de Integração/Pipeline

| Campo | Tipo | Descrição |
|-------|------|-----------|
| `_sdc_received_at` | DateTime | Data de recebimento (Singer Data Connector) |
| `ingestion_at` | DateTime | Data de ingestão no sistema |
| `processed_at` | DateTime | Data de processamento |

## Relacionamentos

- **managerid** → Referência para outro usuário (gerente)
- **profileid** → Referência para perfil de segurança
- **user_role_id** → Referência para hierarquia de funções
- **lastmodifiedbyid** → Referência para usuário que modificou

## Observações Importantes

1. **Fonte de Dados**: Dados originários do Salesforce via Singer Data Connector
2. **Atualização**: Processado regularmente através do pipeline de ingestão
3. **Campos Customizados**: Campos com sufixo `__c` são customizações específicas de negócio ARCO
4. **Dados Sensíveis**: Email e outras informações de contato requerem tratamento conforme LGPD/GDPR
5. **Status do Usuário**: Sempre verificar `isactive` antes de usar dados

## Exemplo de Query

```sql
SELECT
  id,
  name,
  email,
  department,
  isactive,
  brand__c,
  segment__c
FROM
  raw__salesforce__arco.current__user
WHERE
  isactive = true
ORDER BY
  name ASC
```

## Histórico de Atualizações

| Data | Versão | Alteração |
|------|--------|-----------|
| 2026-04-23 | 1.0 | Documentação inicial do schema |