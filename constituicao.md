# Constituição do Projeto — Sistema de Contas a Pagar (SCP)

**Versão:** 2.0 — 17/11/2026  
**Status:** proposta consolidada para aprovação expressa da equipe.

## 1. Problema e objetivo

Controles manuais ou dispersos de contas a pagar podem dificultar o acompanhamento de vencimentos, gerar erros de lançamento e aumentar o risco de pagamentos duplicados. O SCP pretende centralizar o cadastro, a análise, a aprovação e a confirmação de pagamentos, mantendo histórico verificável.

## 2. Princípios inegociáveis

> **Atenção:** estes princípios foram consolidados a partir do material original da equipe. A equipe deve confirmar formalmente esta versão antes de tratá-la como aprovada.

- **P1 — Simplicidade:** o sistema deve ter linguagem clara, campos compreensíveis e fluxo objetivo.
- **P2 — Acesso autorizado:** cada usuário só pode consultar e executar ações compatíveis com seu perfil, responsabilidade e alçada.
- **P3 — Rastreabilidade:** operações relevantes devem registrar usuário autenticado, data, horário, ação e conta; alterações devem preservar informação anterior e nova, quando aplicável.
- **P4 — Integridade:** registros financeiros e seu histórico não podem ser apagados ou alterados silenciosamente. Correções devem ocorrer por fluxo autorizado, justificado e auditável.
- **P5 — Segregação e confirmação:** cadastro, aprovação e confirmação de pagamento são etapas distintas. Uma conta só pode ser considerada paga após confirmação por usuário autorizado, com referência ou comprovante.

## 3. Limites

- O SCP apoia o controle administrativo; não realiza transferência bancária nesta versão.
- A confirmação no SCP ocorre depois do pagamento feito fora do sistema.
- A ferramenta escolhida não pode enfraquecer os princípios acima.
- Forms/Sheets isoladamente não garantem autorização por registro nem logs protegidos; uma camada de aplicação e testes de segurança serão necessários se essa plataforma for escolhida.

## 4. Critério geral de sucesso

O projeto será considerado concluído quando o SPT atender aos critérios de aceitação aprovados, os testes forem executados pela equipe, as falhas forem tratadas ou registradas e houver evidências verificáveis.
