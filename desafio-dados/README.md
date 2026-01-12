# 📁 Dados do Desafio Técnico - Analista de Suporte N2

Este diretório contém todos os dados necessários para realizar o desafio técnico.

## 📂 Estrutura de Diretórios

```
desafio-dados/
├── logs/
│   ├── application_2024-01-15.log      # Logs do dia do incidente
│   └── application_2024-01-08.log      # Logs de 7 dias antes (para comparação)
├── metrics/
│   └── prometheus_2024-01-15.csv       # Métricas exportadas do Prometheus
├── alerts/
│   └── noc_alerts_2024-01-15.json      # Alertas do NOC em formato JSON
├── incidents/
│   └── historical_incidents.json       # Histórico de incidentes similares
└── templates/
    ├── relatorio_tecnico_template.md    # Template para relatório técnico
    └── runbook_template.md              # Template para runbook operacional
```

## 📋 Descrição dos Arquivos

### Logs

#### `logs/application_2024-01-15.log`
Arquivo de log completo do dia 15/01/2024, contendo:
- Logs de inicialização do serviço
- Requisições de pagamento processadas
- Erros e warnings
- Métricas de latência e pool de conexões

**Formato:** Uma linha por evento, com timestamp ISO 8601

**Comandos úteis:**
```bash
# Contar erros
grep -i "error" logs/application_2024-01-15.log | wc -l

# Primeiro erro
grep -i "error" logs/application_2024-01-15.log | head -1

# Erros por tipo
grep -i "error" logs/application_2024-01-15.log | sort | uniq -c | sort -rn
```

#### `logs/application_2024-01-08.log`
Arquivo de log de 7 dias antes (08/01/2024) para comparação. Este dia teve comportamento normal, sem incidentes significativos.

### Métricas

#### `metrics/prometheus_2024-01-15.csv`
Métricas exportadas do Prometheus no formato CSV, contendo:
- `http_request_duration_seconds_p95`: Latência p95 em segundos
- `http_requests_total`: Total de requisições HTTP (com status code)
- `error_rate`: Taxa de erro (0-1)
- `request_rate`: Taxa de requisições por minuto

**Formato CSV:**
- Colunas: `timestamp`, `metric_name`, `metric_value`, `labels`
- Timestamps em ISO 8601
- Valores numéricos

**Comandos úteis:**
```bash
# Filtrar por métrica específica
grep "http_request_duration_seconds_p95" metrics/prometheus_2024-01-15.csv

# Usar jq para JSON (se converter)
# Usar awk para processar CSV
```

### Alertas

#### `alerts/noc_alerts_2024-01-15.json`
Alertas disparados pelo NOC no dia 15/01/2024, contendo:
- ID do alerta
- Timestamp
- Severidade (info, warning, critical)
- Nome e descrição do alerta
- Métrica e valor
- Status (firing, resolved)

**Formato JSON** com array de objetos

**Comandos úteis:**
```bash
# Contar alertas
jq 'length' alerts/noc_alerts_2024-01-15.json

# Alertas críticos
jq '.[] | select(.severity == "critical")' alerts/noc_alerts_2024-01-15.json

# Primeiro alerta
jq '.[0]' alerts/noc_alerts_2024-01-15.json
```

### Histórico de Incidentes

#### `incidents/historical_incidents.json`
Histórico de incidentes similares que ocorreram anteriormente, contendo:
- ID do incidente
- Data e horário
- Duração
- Severidade
- Sintomas
- Causa-raiz
- Resolução
- Impacto
- Padrão de recorrência

**Formato JSON** com array de objetos

**Comandos úteis:**
```bash
# Listar todos os incidentes
jq '.[].incident_id' incidents/historical_incidents.json

# Incidentes de alta severidade
jq '.[] | select(.severity == "high")' incidents/historical_incidents.json

# Incidentes com padrão de recorrência
jq '.[] | select(.recurrence_pattern != null)' incidents/historical_incidents.json
```

### Templates

#### `templates/relatorio_tecnico_template.md`
Template para criação do relatório técnico (Tarefa 4).

#### `templates/runbook_template.md`
Template para criação do runbook operacional (Tarefa 5).

## 🛠️ Ferramentas Recomendadas

Para análise dos dados, você pode usar:

- **grep/awk/sed**: Análise de logs
- **jq**: Processamento de JSON
- **csvkit** ou **awk**: Processamento de CSV
- **Excel/Google Sheets**: Visualização de dados (opcional)
- **Python/Node.js**: Scripts personalizados (opcional)

## 📊 Dicas de Análise

1. **Comece pelos logs**: Identifique o primeiro erro e trace a sequência de eventos
2. **Correlacione com métricas**: Compare timestamps dos logs com métricas do Prometheus
3. **Valide com alertas**: Verifique se os alertas correspondem aos problemas identificados
4. **Compare com histórico**: Veja se há padrões similares em incidentes anteriores
5. **Seja específico**: Sempre referencie linhas de log, timestamps ou valores de métricas em suas respostas

## ⚠️ Observações Importantes

- Todos os dados são simulados para fins de avaliação
- Os timestamps estão em UTC (Z no final)
- Alguns dados podem conter informações irrelevantes que precisam ser filtradas
- Nem todos os alertas são necessariamente relevantes para o problema principal

## 📝 Notas para o Candidato

- **Seja específico**: Sempre referencie dados concretos (linhas de log, timestamps, valores de métricas)
- **Mostre seu trabalho**: Inclua comandos que você executou para chegar às conclusões
- **Justifique decisões**: Não apenas diga "o que fazer", explique "por que fazer"
- **Seja honesto**: Se não tiver certeza sobre algo, indique o nível de confiança e o que você faria para aumentar a confiança

Boa sorte! 🚀

