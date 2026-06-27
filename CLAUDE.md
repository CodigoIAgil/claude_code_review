# Simulador Cognitivo — Direção do Projeto

## Identidade do Produto

**O que é:** Um sistema de agentes de IA para preparação de certificações que substitui o estudo passivo por assimilação forçada via recall ativo.

**O que NÃO é:** Um agregador de conteúdo, um clone de NotebookLM, um gerador de quiz simples, ou uma plataforma de vídeos.

**Diferencial central:** O estudante não escolhe o que estudar — o sistema extrai o que o edital exige e força a demonstração de compreensão antes de avançar.

**Certificação MVP:** CompTIA Security+ SY0-701

---

## Arquitetura dos Agentes

### Agente 1 — Mapeador de Edital
- **Input:** Material de estudo bruto (PDFs, textos, cheat sheets) + objetivos oficiais do exame
- **Output:** Extrato mapeado: conteúdo validado contra o edital, com indicação de domínio e sub-objetivo coberto
- **Critério de qualidade:**
  - Recall ≥ 85% (≥85% das questões do exame respondíveis a partir do extrato)
  - Ruído ≤ 20% (≤20% do extrato irrelevante para o exame)
- **Lógica:** Cross-reference sistemático entre conteúdo e objetivos SY0-701. Gaps são explicitados, não ignorados.

### Agente 2 — Extrator de Ouro
- **Input:** Extrato do Mapeador
- **Output:** "Pepitas" — os conceitos, definições e distinções que têm maior probabilidade de aparecer em questão
- **Lógica:** Filtra ruído residual, prioriza por domínio e frequência histórica de questões

### Agente 3 — Inquisidor
- **Input:** Pepitas do Extrator + histórico de erros do estudante
- **Output:** Sessão de recall ativo (perguntas, sem múltipla escolha no núcleo — o estudante explica)
- **Lógica:** Técnica de Feynman invertida — o estudante ensina o conceito; o agente avalia se a explicação cobre o que o exame exige
- **Não é:** Um gerador de questões de múltipla escolha passivo

### Agente 4 — Sintetizador
- **Input:** Log de erros e lacunas da sessão do Inquisidor
- **Output:** Plano de revisão personalizado para a próxima sessão
- **Lógica:** Identifica padrões de erro, propõe ordem de revisão por peso no exame

---

## Domínios SY0-701 (referência do Mapeador)

| Domínio | Título | Peso |
|---------|--------|------|
| 1.0 | General Security Concepts | 12% |
| 2.0 | Threats, Vulnerabilities, and Mitigations | 22% |
| 3.0 | Security Architecture | 18% |
| 4.0 | Security Operations | 28% |
| 5.0 | Security Program Management and Oversight | 20% |

**Arquivo de referência canônico:** Objetivos oficiais CompTIA SY0-701 (versão em português — carregado na Fase 0)

---

## Decisões Técnicas (Fase 0)

### Escopo V1 (MVP)
- Apenas texto/conceitual — sem simulação de terminal
- Sem interface gráfica no MVP — interação via prompt direto
- Sem persistência de banco de dados no MVP — sessão stateless
- Sem autenticação/LGPD no MVP — uso individual do desenvolvedor

### Escopo Excluído (V1)
- Simulação de comandos Linux (RHCSA seria isso — fora do escopo)
- Interface web/mobile
- Multi-usuário
- Sistema de gamificação

### V1.1 (pós-validação do MVP)
- Expandir para AWS SAA-C03 (segundo ativo de certificação priorizável)
- Interface simples para acesso via browser

### Stack (provisória — será confirmada no início da Fase 1)
- Python (lingua franca para LLM tooling)
- Anthropic SDK (agentes via Claude)
- PDFMiner ou pdfplumber para ingestão de material (pendente — ambiente teve problemas de dependência)

---

## Validações da Fase 0 (o que foi provado)

1. **Mecanismo funciona:** Teste conceitual do Mapeador contra Domínio 1.0 confirmou que o agente detecta gaps corretamente. O Cheat Sheet Station X (SY0-601, versão antiga) foi identificado como coberta parcial — ~35% recall, ~70% precisão. Isso prova que o Mapeador rejeita ruído.

2. **Modelo online de desenvolvimento validado:** Claude Code via browser Android → container Linux remoto → GitHub. O protocolo de commit+push ao final de cada sessão é essencial para containers efêmeros.

3. **SY0-601 vs SY0-701:** O Cheat Sheet anexado (Station X) cobre a versão ANTIGA do exame. Isso não é erro — é dado. O Mapeador deve tratar como material legado com ruído estrutural.

---

## Pendências que Entram na Fase 1

| Item | Status | Criticidade |
|------|--------|-------------|
| Prompt do Mapeador Agent | **Fase 1, Task 1** | Bloqueante |
| Teste com questões reais SY0-701 | Fase 1, Task 2 (usuário provê 10-15 questões manualmente) | Alta |
| Material Professor Messer | Fase 1, Task 3 (usuário provê quando possível) | Alta |
| PDF de Q&A (dbe2a1b4) | Ilegível — cegueira técnica controlada | Não bloqueante |
| Arquivo .docx de arquitetura | Ilegível — formato binário | Não bloqueante |

---

## Protocolo de Sessão

Este projeto segue o **Protocolo de Desenvolvimento Verificado v2.2**.

- Cada sessão abre com leitura deste CLAUDE.md e do STATUS.md
- Cada sessão fecha com commit + push + atualização do STATUS.md
- Decisões de arquitetura são registradas aqui, não nos commits
- O STATUS.md registra o estado de execução (o que foi feito, o que está pendente)
