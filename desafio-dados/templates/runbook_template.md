# Runbook: [NOME DO CENÁRIO]

**Última atualização:** [DATA]  
**Versão:** [VERSÃO]  
**Responsável:** [NOME]

---

## 📋 Informações Gerais

**Serviço:** [NOME DO SERVIÇO]  
**Ambiente:** [PRODUÇÃO/STAGING]  
**SLA:** [SLA DO SERVIÇO]  
**Contatos de Emergência:**
- N2: [CONTATO]
- N3/Dev: [CONTATO]
- Infraestrutura: [CONTATO]

---

## 🚨 Sintomas

### Como Identificar o Problema

**Métricas:**
- [Métrica 1]: [Valor normal] → [Valor de alerta]
- [Métrica 2]: [Valor normal] → [Valor de alerta]

**Alertas:**
- [Nome do alerta]: [Descrição]
- [Nome do alerta]: [Descrição]

**Logs:**
- [Padrão de log a procurar]
- [Comando para verificar]

**Dashboards:**
- [Link para dashboard 1]
- [Link para dashboard 2]

---

## 🔍 Passos de Verificação

Execute na ordem exata:

### 1. Verificar Status do Serviço
```bash
# Comando 1
[COMANDO]

# Resultado esperado
[RESULTADO ESPERADO]
```

### 2. Verificar Métricas
```bash
# Comando ou query
[COMANDO/QUERY]

# Valores normais
[VALORES NORMAIS]
```

### 3. Verificar Logs
```bash
# Comando
[COMANDO]

# O que procurar
[PADRÃO ESPERADO]
```

### 4. Verificar Recursos
```bash
# Comando
[COMANDO]

# Valores normais
[VALORES NORMAIS]
```

### 5. [Outra verificação se necessário]
```bash
# Comando
[COMANDO]
```

---

## ⚙️ Limites de Atuação do N2

### ✅ O que o N2 PODE fazer:
- [Ação permitida 1]
- [Ação permitida 2]
- [Ação permitida 3]

### ❌ O que o N2 NÃO PODE fazer:
- [Ação proibida 1]: [Razão]
- [Ação proibida 2]: [Razão]
- [Ação proibida 3]: [Razão]

---

## 🚨 Critérios de Escalonamento

Escale para **N3/Desenvolvimento** quando:
- [Critério 1]: [Métrica/condição específica]
- [Critério 2]: [Métrica/condição específica]
- [Critério 3]: [Métrica/condição específica]

Escale para **Infraestrutura** quando:
- [Critério 1]: [Métrica/condição específica]
- [Critério 2]: [Métrica/condição específica]

Escale para **Segurança** quando:
- [Critério 1]: [Métrica/condição específica]

**Informações para incluir no escalonamento:**
- [Item 1]
- [Item 2]
- [Item 3]

---

## 🔧 Ações de Mitigação

### Mitigação 1: [Nome da ação]
**Quando usar:** [Condição]  
**Como executar:**
```bash
# Comando
[COMANDO]

# Validação
[Como validar se funcionou]
```

**Riscos:** [Riscos desta ação]  
**Reversão:** [Como reverter se necessário]

### Mitigação 2: [Nome da ação]
**Quando usar:** [Condição]  
**Como executar:**
```bash
# Comando
[COMANDO]
```

**Riscos:** [Riscos desta ação]  
**Reversão:** [Como reverter se necessário]

---

## ✅ Checklist Pós-Normalização

Antes de considerar o incidente resolvido, validar:

- [ ] **Métricas normalizadas:**
  - [ ] [Métrica 1] está dentro do normal
  - [ ] [Métrica 2] está dentro do normal

- [ ] **Logs sem erros:**
  - [ ] Sem erros críticos nos últimos [X] minutos
  - [ ] Padrão de logs normalizado

- [ ] **Alertas resolvidos:**
  - [ ] Todos os alertas críticos resolvidos
  - [ ] Alertas de warning dentro do esperado

- [ ] **Funcionalidade validada:**
  - [ ] [Funcionalidade 1] funcionando
  - [ ] [Funcionalidade 2] funcionando

- [ ] **Recursos normalizados:**
  - [ ] CPU/Memória dentro do normal
  - [ ] Conexões de rede estáveis

- [ ] **Comunicação:**
  - [ ] N1 notificado da resolução
  - [ ] Stakeholders informados (se necessário)

---

## 📚 Referências

### Dashboards
- [Nome do dashboard]: [URL]
- [Nome do dashboard]: [URL]

### Documentação
- [Documento 1]: [URL]
- [Documento 2]: [URL]

### Runbooks Relacionados
- [Runbook relacionado 1]: [Link]
- [Runbook relacionado 2]: [Link]

### Contatos
- **N2 Plantão:** [CONTATO]
- **N3/Dev:** [CONTATO]
- **Infraestrutura:** [CONTATO]
- **Segurança:** [CONTATO]

---

## 📝 Notas Adicionais

[Espaço para notas, observações, ou lições aprendidas]

---

## 🔄 Histórico de Alterações

| Data | Versão | Alteração | Autor |
|------|--------|-----------|-------|
| [DATA] | 1.0 | Criação inicial | [NOME] |
| [DATA] | 1.1 | [Descrição da alteração] | [NOME] |

