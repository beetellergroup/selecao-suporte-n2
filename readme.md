# 🛠️ Desafio Técnico — Analista de Suporte N2

Bem-vindo(a) ao desafio técnico para a vaga de **Analista de Suporte N2** da Beeteller.

Este desafio simula situações reais enfrentadas pelo time de Operações e Suporte Técnico N2 em ambientes produtivos críticos. O objetivo é avaliar sua capacidade de diagnóstico, tomada de decisão, comunicação técnica e organização operacional.

---

## 🎯 Objetivo

Avaliar sua atuação como **Analista de Suporte N2**, considerando:

- Atendimento e resolução de incidentes escalados pelo N1 ou identificados pelo NOC;
- Análise de logs, métricas, filas e alertas;
- Identificação de falhas recorrentes e causa-raiz;
- Comunicação técnica com N1, NOC e times internos;
- Produção de documentação técnica e runbooks.

---

## 🧩 Contexto

### Ambiente Técnico
- **Serviço**: API de pagamentos (Node.js/Express)
- **Infraestrutura**: Kubernetes (EKS), 3 réplicas
- **Monitoramento**: Prometheus + Grafana, ELK Stack (Elasticsearch, Logstash, Kibana)
- **SLA**: 99.9% disponibilidade, latência p95 < 200ms
- **Horário do incidente**: Sexta-feira, 23h15

### Situação
Nas últimas semanas, o **NOC** vem registrando alertas recorrentes de aumento de latência e erros intermitentes no serviço de pagamentos.

O **Suporte N1** também recebeu relatos pontuais de falha por parte dos usuários, principalmente em horários de pico (14h-16h e 20h-22h).

**Restrições Operacionais:**
- Você está sozinho no plantão
- Time de Desenvolvimento está offline até segunda-feira
- Não pode fazer deploy ou alterações de configuração sem aprovação
- Acesso apenas a logs dos últimos 7 dias

### Arquivos Fornecidos
Você recebeu os seguintes arquivos no repositório:
- `logs/application_2024-01-15.log` (arquivo de log completo do dia do incidente)
- `logs/application_2024-01-08.log` (arquivo de log de 7 dias antes, para comparação)
- `metrics/prometheus_2024-01-15.csv` (métricas exportadas do Prometheus)
- `alerts/noc_alerts_2024-01-15.json` (alertas do NOC em formato JSON)
- `incidents/historical_incidents.json` (histórico de incidentes similares)

---

## ⏳ Prazo

- Prazo total: **3 dias corridos**
- Tempo estimado de dedicação: **4 a 6 horas**

---

## 🧪 TAREFAS

### 📌 Tarefa 0 — Análise Inicial de Dados

Antes de começar as outras tarefas, você deve:

1. **Analisar os logs fornecidos:**
   - Identifique quantos erros ocorreram no arquivo `logs/application_2024-01-15.log`
   - Qual foi o timestamp exato do primeiro erro?
   - Qual foi o timestamp do último erro antes da normalização?
   - Liste os 3 tipos de erro mais frequentes (com contagem)

2. **Analisar as métricas:**
   - No arquivo `metrics/prometheus_2024-01-15.csv`, identifique:
     - Qual foi o pico de latência p95 e em que horário exato?
     - Qual foi a taxa de erro (erro_rate) máxima e quando ocorreu?
     - Compare a taxa de requisições (request_rate) entre 14h-16h e 20h-22h

3. **Analisar os alertas:**
   - Quantos alertas foram disparados no dia 15/01?
   - Qual foi o primeiro alerta disparado?
   - Há alertas que parecem falsos positivos? Justifique.

**Formato de entrega:** Crie um arquivo `TAREFA_0_ANALISE_INICIAL.md` com suas respostas, incluindo comandos utilizados (grep, awk, jq, etc.) e resultados.

---

### 📌 Tarefa 1 — Diagnóstico do Incidente

Com base na análise dos dados fornecidos:

1. Descreva seu **plano de ação inicial**, em ordem exata, referenciando:
   - Linhas específicas dos logs ou timestamps que justificam cada passo
   - Métricas que validam suas hipóteses
   - Comandos ou queries que você executaria

2. Liste até **3 hipóteses principais** para o problema, ordenadas por probabilidade, e para cada uma:
   - Evidência técnica específica (ex: "Linha 1247 do log mostra timeout na conexão com banco")
   - Métrica que valida ou invalida a hipótese
   - Ação de validação que você executaria

3. Que **evidências técnicas adicionais** você buscaria para validar cada hipótese? Seja específico:
   - Quais queries no Prometheus?
   - Quais filtros no Kibana?
   - Quais comandos kubectl?

4. Que **ações imediatas** você tomaria como N2? Especifique:
   - Ação exata (ex: "Escalar horizontalmente de 3 para 5 pods")
   - Justificativa técnica
   - Risco da ação
   - Como validar se a ação funcionou

5. O que você **não faria nesse momento** e por quê? Liste pelo menos 3 ações que parecem óbvias mas que você evitaria.

6. Em que momento e para qual time você **escalaria o incidente**? Defina:
   - Critérios objetivos (ex: "Se latência p95 > 500ms por mais de 10 minutos")
   - Para qual time escalar (Dev, Infra, Segurança)
   - Informações que você incluiria no escalonamento

---

### 📌 Tarefa 2 — Apoio ao Suporte N1

O N1 está recebendo chamados de usuários e precisa de orientação. Redija **duas versões** de comunicação:

**Versão A - Canal Slack (técnico):**
- Status do incidente
- O que já foi validado (com evidências)
- Orientações práticas enquanto o incidente está em análise
- Prazo estimado de resolução

**Versão B - Template de resposta para usuários (não-técnico):**
- Mensagem que o N1 pode usar para responder aos usuários
- Linguagem clara e sem jargão técnico
- Transparência sem criar pânico

**Formato:** Crie um arquivo `TAREFA_2_COMUNICACAO_N1.md` com ambas as versões.

---

### 📌 Tarefa 3 — Análise de Recorrência e Causa-Raiz

1. **Análise de recorrência:**
   - Compare os logs de `application_2024-01-15.log` com `application_2024-01-08.log`
   - Analise o arquivo `incidents/historical_incidents.json`
   - Identifique padrões recorrentes (dias da semana, horários, tipos de erro)
   - Crie uma tabela comparativa mostrando similaridades

2. **Causa-raiz:**
   - Qual a **causa-raiz mais provável** baseada em evidências?
   - Justifique com dados específicos (linhas de log, métricas, comparações)
   - Qual sua confiança (0-100%) nessa causa-raiz? Justifique o nível de confiança.

3. **Ações de prevenção:**
   - Que **ações técnicas** você sugeriria para evitar recorrência? (ex: ajuste de configuração, monitoramento adicional)
   - Que **ações de processo** você sugeriria? (ex: runbook, treinamento, alertas proativos)
   - Priorize as ações por impacto vs. esforço

---

### 📌 Tarefa 4 — Relatório Técnico

Produza um **relatório técnico resumido** (máx. 2 páginas) para os times de Desenvolvimento, Infraestrutura e Segurança.

Use o template fornecido em `templates/relatorio_tecnico_template.md` e preencha:

- **Descrição do problema**: O que aconteceu, quando, impacto
- **Evidências técnicas**: Logs, métricas, alertas (com referências específicas)
- **Causa-raiz identificada**: Hipótese principal e nível de confiança
- **Impacto**: Quantos usuários afetados, duração, métricas de negócio
- **Risco de recorrência**: Probabilidade e justificativa
- **Próximos passos**: O que o N2 fez, o que precisa do N3/Dev/Infra
- **Recomendações**: Melhorias técnicas e de processo

**Formato:** Arquivo `TAREFA_4_RELATORIO_TECNICO.md`

---

### 📌 Tarefa 5 — Runbook Operacional

Crie um **runbook operacional** para o cenário:
> "Aumento de latência e erro intermitente em serviço crítico de pagamentos"

O runbook deve seguir o template em `templates/runbook_template.md` e incluir:

- **Sintomas**: Como identificar o problema (métricas, alertas, logs)
- **Passos de verificação**: Ordem exata de checagens, com comandos específicos
- **Limites de atuação do N2**: O que pode fazer, o que não pode
- **Critérios de escalonamento**: Quando e para quem escalar (com métricas objetivas)
- **Ações de mitigação**: Workarounds temporários que o N2 pode aplicar
- **Checklist pós-normalização**: Validações antes de considerar resolvido
- **Referências**: Links para dashboards, documentação, contatos

**Formato:** Arquivo `TAREFA_5_RUNBOOK.md`

---

### 📌 Tarefa 6 — Priorização (Tarefa Opcional)

Você recebeu simultaneamente 3 incidentes diferentes:

1. **Incidente A**: API de pagamentos com latência alta (este desafio)
2. **Incidente B**: Dashboard de métricas offline (não crítico)
3. **Incidente C**: Alerta de segurança - possível tentativa de acesso não autorizado

Priorize a ordem de atendimento e justifique considerando:
- Impacto nos usuários
- Urgência (SLA, risco de degradação)
- Recursos disponíveis
- Dependências entre incidentes

**Formato:** Arquivo `TAREFA_6_PRIORIZACAO.md`

---

## 📬 Como enviar

1. Crie um repositório **privado no GitHub** com o nome:
   ```
   desafio-analista-suporte-n2-beeteller
   ```

2. Estruture o repositório assim:
   ```
   desafio-analista-suporte-n2-beeteller/
   ├── TAREFA_0_ANALISE_INICIAL.md
   ├── TAREFA_1_DIAGNOSTICO.md
   ├── TAREFA_2_COMUNICACAO_N1.md
   ├── TAREFA_3_RECORRENCIA_CAUSA_RAIZ.md
   ├── TAREFA_4_RELATORIO_TECNICO.md
   ├── TAREFA_5_RUNBOOK.md
   ├── TAREFA_6_PRIORIZACAO.md (opcional)
   └── README.md (com instruções de como executar seus comandos/scripts, se houver)
   ```

3. Compartilhe o acesso com:
   📧 **caio.vidal@beeteller.com**

---

## 📊 Avaliação

Serão avaliados:

### Critérios Técnicos (60%)
- ✅ Precisão na análise de logs e métricas (Tarefa 0)
- ✅ Lógica e ordem das decisões (Tarefa 1)
- ✅ Capacidade de diagnóstico em produção (Tarefa 1, 3)
- ✅ Uso correto de ferramentas e comandos (Tarefa 0, 1)
- ✅ Identificação correta de causa-raiz (Tarefa 3)

### Critérios de Comunicação (25%)
- ✅ Clareza na comunicação técnica (Tarefa 2, 4)
- ✅ Adaptação do nível técnico ao público (Tarefa 2)
- ✅ Estrutura e organização do relatório (Tarefa 4)

### Critérios de Documentação (15%)
- ✅ Qualidade e completude do runbook (Tarefa 5)
- ✅ Consistência entre análise, decisão e documentação
- ✅ Visão de melhoria contínua (Tarefa 3, 4)

### Red Flags (Eliminatórios)
- ❌ Análise de dados incorreta ou sem evidências
- ❌ Decisões que poderiam piorar o incidente
- ❌ Falta de justificativa técnica para ações
- ❌ Respostas genéricas que não referenciam os dados fornecidos

---

## ⚠️ Regras Importantes

1. **Não use IA generativa** (ChatGPT, Claude, etc.) para responder as tarefas. No dia a dia utilizeremos essas ferramentas, mas não para o teste prático. O desafio foi desenhado para detectar uso de IA.

2. **Seja específico**: Sempre referencie dados concretos (linhas de log, timestamps, métricas) em suas respostas.

3. **Justifique decisões**: Não apenas diga "o que fazer", explique "por que fazer" e "como validar".

4. **Seja honesto sobre incertezas**: Se não tiver certeza sobre algo, indique o nível de confiança e o que você faria para aumentar a confiança.

---

Boa sorte! 🚀
