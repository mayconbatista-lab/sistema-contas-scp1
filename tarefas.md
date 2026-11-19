# Tarefas — Sistema de Contas a Pagar (SCP)

**Versão:** 2.1 — 17/11/2026  
**Status:** backlog proposto; tarefas não devem ser marcadas como concluídas sem evidência.

## 1. Backlog rastreável

| ID | Tarefa | Requisitos/CA relacionados | Dependência | Responsável | Status inicial |
|---|---|---|---|---|---|
| T-01 | Aprovar constituição e especificação; resolver decisões pendentes | P1–P5; RF-01 a RF-12; CA-01 a CA-12 | — | Equipe | Pendente |
| T-02 | Fazer revisão por pares e monitoria; preencher checklist e revisar spec | Todos | T-01 | Equipe + outra equipe/monitoria | Pendente |
| T-03 | Comparar plataformas e provar autenticação/autorização e auditoria em protótipo | RNF-01 a RNF-03 | T-01, T-02 | Equipe com sugestões da IA | Pendente |
| T-04 | Definir modelo de dados e identificadores | RF-01, RF-02, RF-10; CA-01, CA-07 | T-03 | Equipe/implementador | Pendente |
| T-05 | Implementar cadastro e validação de campos | RF-01; CA-01, CA-02 | T-04 | Implementador | Pendente |
| T-06 | Implementar detecção/alerta de duplicidade | RF-03; CA-08 | T-05 | Implementador | Pendente |
| T-07 | Implementar autenticação e autorização por registro/operação | RF-04, RNF-01; CA-03 | T-03, T-04 | Implementador | Pendente |
| T-08 | Implementar aprovação e rejeição com justificativa | RF-05, RF-06; CA-05 | T-05, T-07 | Implementador | Pendente |
| T-09 | Implementar bloqueio de pagamento sem aprovação | RF-08; CA-04 | T-08 | Implementador | Pendente |
| T-10 | Implementar confirmação manual de pagamento | RF-07; CA-06 | T-09 | Implementador | Pendente |
| T-11 | Implementar auditoria protegida e correção/cancelamento/estorno | RF-10, RF-12; CA-07, CA-10 | T-04, T-07 | Implementador | Pendente |
| T-12 | Implementar indicador de vencimento | RF-09; CA-11 | T-05, T-10 | Implementador | Pendente |
| T-13 | Implementar relatórios com filtros e permissões | RF-11; CA-09 | T-07, T-08, T-10 | Implementador | Pendente |
| T-14 | Implementar e testar backup/restauração | RNF-05; CA-12 | T-04 | Implementador/equipe | Pendente |
| T-15 | Preparar pacote do SPT, instruções de execução e evidências | Todos | T-05 a T-14 | Equipe | Pendente |
| T-16 | Executar validação manual, registrar falhas e retestar após correção | CA-01 a CA-12 | T-15 | Equipe, sem IA | Pendente |
| T-17 | Consolidar relatório final e repositório | Entregáveis da disciplina | T-02, T-15, T-16 | Equipe | Pendente |
| T-18 | Revisar e aprovar critérios de detecção de possíveis duplicidades; validar bloqueio de aprovação sem conferência | RF-13/CA-13 propostos | T-01, T-06 | Equipe + implementador | Pendente |
| T-19 | Revisar eventos e permissões da linha do tempo; validar sequência cronológica | RF-14/CA-14 propostos | T-07, T-11 | Equipe + implementador | Pendente |
| T-20 | Revisar horizonte de vencimento e indicadores do painel preventivo | RF-15/CA-15 propostos | T-12 | Equipe + implementador | Pendente |

## 2. Ordem de execução

A sequência preferencial é T-01 → T-02 → T-03 → T-04 → T-05 → T-06/T-07 → T-08 → T-09 → T-10 → T-11/T-12/T-13/T-14 → T-15 → T-16 → T-17. As tarefas T-18 a T-20 dependem da revisão do adendo v1.1 e podem ser executadas em paralelo após a aprovação dos critérios pela equipe. Tarefas paralelas só podem ocorrer quando suas dependências estiverem satisfeitas.

## 3. Registro do uso de IA

| Data | Assistente | Tarefa | Material gerado/sugerido pela IA | Revisão/correção humana | Responsável | Situação |
|---|---|---|---|---|---|---|
| 17/11/2026 | ChatGPT (OpenAI) | Revisão documental e organização de artefatos | Sugestões de estrutura, redação, requisitos, critérios, plano, tarefas e matriz de rastreabilidade | Equipe deve revisar, aprovar, corrigir e registrar suas decisões antes de usar como versão oficial | Equipe | Em revisão |
| 17/11/2026 | ChatGPT (OpenAI) | Evolução técnica do protótipo v1.1 | Implementação inicial de alerta de duplicidade com confirmação, linha do tempo e painel preventivo; adendo e novos casos de teste | Equipe deve revisar código, deliberar sobre os requisitos propostos e executar os testes manuais CT-14 a CT-16 | Equipe | Aguardando revisão e validação |

**Regra:** atualizar esta tabela durante a implementação, indicando claramente o que a IA gerou e o que uma pessoa revisou, corrigiu ou aprovou. Não é necessário arquivar prompts.
