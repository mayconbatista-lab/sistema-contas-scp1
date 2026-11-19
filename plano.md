# Plano — Sistema de Contas a Pagar (SCP)

**Versão:** 2.0 — 17/11/2026  
**Status:** proposta técnica; decisões pendentes indicadas abaixo.

## 1. Caminho de implementação

A escolha é livre conforme orientação da disciplina. A proposta inicial da equipe é Google Forms + Google Sheets, com Google Apps Script como camada de aplicação. Essa escolha só será confirmada após protótipo técnico demonstrar autenticação, autorização por conta, integridade dos registros e auditoria. Se não demonstrar, a equipe deverá escolher outra plataforma sem alterar os requisitos aprovados.

## 2. Componentes lógicos

1. Interface de cadastro/consulta.
2. Serviço de validação e identificação única.
3. Controle de identidade, perfis, responsabilidades e alçadas.
4. Fluxo de aprovação/rejeição.
5. Registro de confirmação de pagamento.
6. Repositório de contas, decisões, pagamentos e logs.
7. Relatórios e alertas.

## 3. Modelo mínimo de dados

- **Contas:** id, fornecedor, documento do fornecedor, referência/NF, descrição, categoria, valor, emissão, vencimento, forma de pagamento, solicitante, gestor responsável, status, timestamps.
- **Aprovações:** id, conta_id, gestor_id, decisão, justificativa, data_hora.
- **Pagamentos:** id, conta_id, valor_pago, data_pagamento, responsável_id, comprovante/referência.
- **Logs:** id, conta_id, usuário_id, ação, data_hora, campo, valor_anterior, valor_novo, justificativa quando aplicável.
- **Usuários/perfis:** identificador autenticado, perfil, responsabilidades, alçadas e situação ativa.

Os campos definitivos, identificadores e política de retenção precisam ser aprovados pela equipe. Não usar nome/e-mail digitado livremente como autenticação.

## 4. Status

`Pendente de aprovação`, `Aprovado`, `Rejeitado`, `Pago`, `Cancelado`. `Vencida` será indicador calculado, não status que apaga o estado principal. A interface pode exibir os dois, por exemplo: `Aprovado · Vencida`.

## 5. Riscos e respostas

| Risco | Resposta planejada |
|---|---|
| Acesso indevido a dados | Autenticação e autorização no servidor em cada ação; teste com perfis distintos |
| Alteração/exclusão indevida | Logs protegidos; correção por fluxo auditável; teste de integridade |
| Pagamento sem aprovação | Regra no servidor bloqueando transição; teste negativo |
| Duplicidade | Alerta por combinação de campos e revisão humana |
| Duas edições simultâneas | Controle de concorrência/versão do registro; definir solução técnica após escolha da plataforma |
| Perda de dados | Backup e restauração testados |
| Limites da plataforma | Protótipo técnico antes de assumir a ferramenta |
| Requisitos indefinidos | Resolver decisões da seção 9 da especificação antes de implementar tarefas dependentes |

## 6. Decisões pendentes

Alçadas; múltiplos aprovadores; separação do responsável pelo pagamento; prazos de alerta; retenção; volume; plataforma definitiva; critérios de duplicidade. A equipe deve registrar decisão, responsável e data antes de iniciar tarefas dependentes.

## 7. Critério para escolha da ferramenta

A plataforma será aceita se permitir: autenticar usuários; validar autorização por registro e operação; manter histórico não editável por usuários comuns; impedir pagamento sem aprovação; preservar dados originais; produzir evidências de teste; e ser viável no prazo e recursos da equipe.
