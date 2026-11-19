# Relatório de Validação — Sistema de Contas a Pagar (SCP)

**Versão:** 1.1 — 17/11/2026  
**Status:** plano/matriz preparada; execução ainda não realizada.

## 1. Objetivo e método

A equipe deverá executar manualmente cada cenário contra o SPT entregue, comparar o resultado observado com o critério de aceitação e anexar evidência. A IA não deve executar nem declarar aprovados os testes de aceitação, pois a orientação da disciplina atribui essa validação à equipe.

## 2. Matriz requisito → critério → tarefa → status

| Requisito | Critério | Tarefa | Teste relacionado | Status inicial | Evidência/observação |
|---|---|---|---|---|---|
| RF-01, RF-02 | CA-01 | T-04, T-05 | CT-01 | Pendente | A preencher pela equipe |
| RF-01 | CA-02 | T-05 | CT-02 | Pendente | A preencher pela equipe |
| RF-04, RNF-01 | CA-03 | T-07 | CT-03 | Pendente | A preencher pela equipe |
| RF-05, RF-08 | CA-04 | T-08, T-09 | CT-04 | Pendente | A preencher pela equipe |
| RF-05, RF-06 | CA-05 | T-08 | CT-05, CT-06 | Pendente | A preencher pela equipe |
| RF-07 | CA-06 | T-10 | CT-07 | Pendente | A preencher pela equipe |
| RF-10 | CA-07 | T-11 | CT-08 | Pendente | A preencher pela equipe |
| RF-03 | CA-08 | T-06 | CT-09 | Pendente | A preencher pela equipe |
| RF-11 | CA-09 | T-13 | CT-10 | Pendente | A preencher pela equipe |
| RF-12, RNF-02 | CA-10 | T-11 | CT-11 | Pendente | A preencher pela equipe |
| RF-09 | CA-11 | T-12 | CT-12 | Pendente | A preencher pela equipe |
| RNF-05 | CA-12 | T-14 | CT-12 | Pendente | A preencher pela equipe |
| RF-13 (proposto) | CA-13 | T-18 | CT-14 | Pendente | Depende de aprovação do adendo |
| RF-14 (proposto) | CA-14 | T-19 | CT-15 | Pendente | Depende de aprovação do adendo |
| RF-15 (proposto) | CA-15 | T-20 | CT-16 | Pendente | Depende de aprovação do adendo |

## 3. Casos de teste propostos

| ID | Procedimento manual | Resultado esperado | Status |
|---|---|---|---|
| CT-01 | Cadastrar conta válida | ID único e status Pendente de aprovação | Pendente |
| CT-02 | Enviar cadastro sem campo obrigatório | Envio bloqueado e campo indicado | Pendente |
| CT-03 | Tentar acessar conta de outra responsabilidade com perfil sem permissão | Acesso negado sem revelar dados | Pendente |
| CT-04 | Tentar confirmar conta pendente ou rejeitada | Confirmação bloqueada | Pendente |
| CT-05 | Gestor autorizado aprova conta | Decisão, usuário e data/hora registrados | Pendente |
| CT-06 | Gestor rejeita sem justificativa e depois com justificativa | Primeira tentativa bloqueada; segunda registrada com justificativa | Pendente |
| CT-07 | Confirmar conta aprovada com valor, data e referência | Status Pago e confirmação registrada | Pendente |
| CT-08 | Criar/alterar registro e consultar trilha | Log completo; alteração guarda antes/depois | Pendente |
| CT-09 | Cadastrar possível duplicidade | Alerta exibido; nenhum registro apagado automaticamente | Pendente |
| CT-10 | Gerar relatório com filtros | Dados e totais coerentes com registros e permissões | Pendente |
| CT-11 | Tentar apagar pagamento/conta diretamente | Exclusão bloqueada; fluxo auditável exigido | Pendente |
| CT-12 | Simular data posterior ao vencimento | Indicador Vencida sem substituir status principal | Pendente |
| CT-12 | Fazer backup e restaurar em ambiente de teste | Dados recuperados e evidência documentada | Pendente |
| CT-13 | Executar cadastro, decisão e pagamento; consultar auditoria administrativa | Eventos principais aparecem na auditoria | Pendente |
| CT-14 | Cadastrar possível duplicidade e tentar aprovar sem confirmar conferência | Alerta aparece; aprovação exige confirmação explícita | Pendente |
| CT-15 | Abrir detalhes após cadastro, decisão e pagamento | Linha do tempo mostra ações, usuários e datas/horários | Pendente |
| CT-16 | Consultar painel com contas vencidas, próximas do vencimento e aprovadas não pagas | Indicadores e lista correspondem às permissões do perfil | Pendente |

## 4. Registro de execução por caso

Para cada CT, a equipe deverá registrar: data/hora, responsável, ambiente/versão, dados de teste, resultado observado, resultado esperado, aprovado/reprovado, evidência (arquivo/captura) e defeito/retorno à especificação, se houver.

## 5. Conclusão

O protótipo v1.1 foi atualizado com as três melhorias descritas no adendo proposto. Os requisitos RF-13 a RF-15 ainda dependem de aprovação da equipe. Não há conclusão de validação nesta versão. Todos os casos permanecem **Pendente** até execução manual pela equipe e inclusão de evidências. A aprovação final não pode ser inferida da existência desta matriz.
