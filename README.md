# Monitoramento Delta Sharing (D2O) — Dashboard AI/BI

> ⚠️ **Aviso importante**
>
> Este **não é um produto oficial da Databricks**. Trata-se de um exemplo construído de forma independente, disponibilizado "como está" (*as is*), sem garantias de qualquer tipo.
>
> **Não existe suporte** para esta solução — nem da Databricks, nem da autora. Use, adapte e valide por sua conta e risco antes de utilizá-la em qualquer ambiente.

## O que é

Dashboard AI/BI (Lakeview) para monitorar o uso de **Delta Sharing Databricks-to-Open (D2O)** a partir das *system tables* do Unity Catalog.

### Páginas

- **Inventário de Sharing** — shares ativos, recipients, mapeamento share x recipient e status dos tokens
- **Atividade dos Parceiros** — queries por dia, top recipients, atividade por dia/hora, tipo de conector, top tabelas acessadas
- **Volume de Dados** — bytes escaneados por dia e por recipient, egress por recipient
- **Segurança & Compliance** — IPs de origem, acessos negados por IP, alterações recentes em shares/recipients
- **Custos Delta Sharing** — custo total, por dia, por recipient, por SKU e DBUs de materialização
- **Global Filters** — filtros de data, shares e recipients

### Tabelas utilizadas

- `system.access.audit`
- `system.billing.usage`
- `system.billing.list_prices`
- `system.sharing.materialization_history`
- `system.information_schema.shares`
- `system.information_schema.recipients`
- `system.information_schema.recipient_tokens`
- `system.information_schema.share_recipient_privileges`

## Pré-requisitos

- Workspace com Unity Catalog habilitado
- *System schemas* `access`, `billing` e `sharing` habilitados
- Permissão de `SELECT` nas tabelas acima
- Um SQL Warehouse para executar o dashboard

## Como importar

1. Faça o download do arquivo `Monitoramento Delta Sharing (D2O).lvdash.json`
2. No workspace Databricks, vá em **Dashboards** → **Create dashboard** → **Import dashboard from file** (ou importe o arquivo pelo **Workspace** → **Import**)
3. Selecione o SQL Warehouse e publique

Alternativamente, via CLI:

```bash
databricks workspace import "/Users/<seu-usuario>/Monitoramento Delta Sharing (D2O).lvdash.json" \
  --file "Monitoramento Delta Sharing (D2O).lvdash.json" --format AUTO
```

## Licença

Fornecido "como está", sem garantias e sem suporte.
