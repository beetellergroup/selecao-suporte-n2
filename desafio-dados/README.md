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

### Templates

#### `templates/relatorio_tecnico_template.md`
Template para criação do relatório técnico (Tarefa 4).

#### `templates/runbook_template.md`
Template para criação do runbook operacional (Tarefa 5).

## 🛠️ Ferramentas Disponíveis

Você pode usar qualquer ferramenta de sua preferência para análise:

- **Linha de comando**: grep, awk, sed, jq, csvkit, etc.
- **Planilhas**: Excel, Google Sheets, LibreOffice Calc
- **Scripts**: Python, Node.js, bash, etc.
- **Editores de texto**: Para análise manual se preferir

**Importante:** Documente os comandos/ferramentas que você utilizou em suas respostas.

## ⚠️ Observações Importantes

- Todos os dados são simulados para fins de avaliação
- Os timestamps estão em UTC (Z no final)
- Alguns dados podem conter informações irrelevantes que precisam ser filtradas
- Nem todos os alertas são necessariamente relevantes para o problema principal

## 📝 Notas para o Candidato

- **Seja específico**: Sempre referencie dados concretos (linhas de log, timestamps, valores de métricas) em suas respostas
- **Mostre seu trabalho**: Inclua os comandos/ferramentas que você executou para chegar às conclusões
- **Justifique decisões**: Não apenas diga "o que fazer", explique "por que fazer" com base nas evidências
- **Seja honesto**: Se não tiver certeza sobre algo, indique o nível de confiança e o que você faria para aumentar a confiança

Boa sorte! 🚀

