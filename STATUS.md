# STATUS — Simulador Cognitivo

**Projeto:** Simulador Cognitivo para Certificações  
**Certificação MVP:** CompTIA Security+ SY0-701  
**Repositório:** CodigoIAgil/claude_code_review  
**Branch de desenvolvimento:** claude/review-attached-files-sbzf1o  
**Protocolo:** Desenvolvimento Verificado v2.2  

---

## Fase Atual: FASE 1 — Construção

**Aberta em:** 2026-06-27  
**Status:** Em andamento  

---

## Fase 0 — Discovery ✅ CONCLUÍDA

**Fechada em:** 2026-06-27

### O que foi estabelecido

- **Direção bloqueada:** Simulador Cognitivo com 4 agentes (Mapeador → Extrator → Inquisidor → Sintetizador)
- **Alvo MVP:** CompTIA Security+ SY0-701 (escolha justificada sobre RHCSA e AWS SAA-C03)
- **Mecanismo validado conceitualmente:** Mapeador testado contra Domínio 1.0 — detectou corretamente gaps do material SY0-601 vs objetivos SY0-701
- **Modelo de desenvolvimento validado:** Claude Code via Android + GitHub como desenvolvimento online puro
- **Critérios de qualidade definidos:** Recall ≥ 85%, Ruído ≤ 20%

### Materiais carregados e analisados

| Arquivo | Conteúdo | Status |
|---------|----------|--------|
| Objetivos SY0-701 (PT) | Referência canônica do edital | ✅ Lido e incorporado |
| Cheat Sheet Station X | Material de estudo — cobre SY0-601 (versão antiga) | ✅ Lido — classificado como ruído estrutural |
| Q&A PDF (dbe2a1b4) | Questões e respostas | ❌ Ilegível — cegueira técnica controlada |
| .docx de arquitetura | Documento de arquitetura do protocolo | ❌ Ilegível — formato binário |

### Pendências classificadas como não-bloqueantes para Fase 0

- Q&A PDF ilegível → migra para Fase 1 (usuário provê questões manualmente)
- Material Professor Messer ausente → migra para Fase 1 (usuário provê quando possível)

---

## Fase 1 — Construção: Backlog

### Task 1 — Prompt do Mapeador Agent 🔄 EM ANDAMENTO
**Objetivo:** Construir o system prompt completo do Agente Mapeador de Edital  
**Critério de conclusão:** Prompt capaz de receber material bruto + objetivos SY0-701 e produzir extrato mapeado com recall ≥ 85% e ruído ≤ 20%  
**Status:** Iniciando agora

---

### Task 2 — Teste do Mapeador com questões reais
**Objetivo:** Validar o prompt do Mapeador contra 10-15 questões SY0-701 reais  
**Dependência:** Task 1 concluída + usuário fornece questões manualmente  
**Status:** Aguardando Task 1

---

### Task 3 — Teste com material de qualidade (Professor Messer)
**Objetivo:** Testar Mapeador com material de alta qualidade para validar métricas  
**Dependência:** Task 1 concluída + usuário fornece material Professor Messer  
**Status:** Aguardando Task 1 + material

---

### Task 4 — Prompt do Agente Extrator de Ouro
**Dependência:** Task 2 validada  
**Status:** Backlog

---

### Task 5 — Prompt do Agente Inquisidor
**Dependência:** Tasks 2-3 validadas  
**Status:** Backlog

---

### Task 6 — Prompt do Agente Sintetizador
**Dependência:** Task 5 validada  
**Status:** Backlog

---

## Última Sessão

**Data:** 2026-06-27  
**O que foi feito:**
- Fase 0 concluída e fechada
- CLAUDE.md gerado (direção do projeto)
- STATUS.md gerado (este arquivo)
- Fase 1 aberta, Task 1 iniciada

**Próxima ação imediata:** Construir o prompt do Agente Mapeador de Edital
