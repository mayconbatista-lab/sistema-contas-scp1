# Especificação de Requisitos — Sistema de Contas a Pagar (SCP)

**Versão:** 2.0 — 17/11/2026  
**Status:** versão revisada; depende de aprovação da equipe e revisão por pares/monitoria.

## 1. Contexto e problema

A gestão manual ou dispersa de obrigações financeiras dificulta localizar informações, acompanhar vencimentos e verificar quem cadastrou, aprovou ou confirmou uma conta. O SCP centraliza essas informações e organiza o fluxo, sem executar pagamentos bancários.

## 2. Usuários

- **Solicitante/contador:** cadastra contas, acompanha solicitações e corrige dados enquanto o fluxo permitir.
- **Gestor/aprovador:** analisa contas atribuídas à sua alçada, aprova ou rejeita e registra justificativa quando exigida.
- **Responsável pela confirmação:** registra pagamento realizado externamente, com valor, data e comprovante/referência.
- **Administrador:** gerencia usuários, perfis e parâmetros; suas ações também são auditadas.

Uma mesma pessoa pode acumular funções somente se a equipe definir isso e se não contrariar a regra de segregação adotada. As alçadas e incompatibilidades ainda precisam ser aprovadas.

## 3. Escopo incluído

Cadastro e consulta de contas; validação de campos; identificador único; alerta de possível duplicidade; encaminhamento para aprovação; aprovação/rejeição; confirmação manual de pagamento; controle de status; histórico/auditoria; alertas de vencimento; relatórios básicos.

## 4. Fora do escopo

Contas a receber; execução automática de transferências; integração bancária em tempo real; conciliação bancária automática; importação automática de OFX. Não se presume integração bancária porque o documento original mencionou essa possibilidade sem definir interface, dados ou autorização.

## 5. Requisitos funcionais em formato EARS

- **RF-01 — Cadastro:** Quando um solicitante autorizado enviar uma conta, o sistema deverá validar os campos obrigatórios e registrar os dados válidos.
- **RF-02 — Identificador:** Quando uma conta válida for registrada, o sistema deverá atribuir um identificador único.
- **RF-03 — Duplicidade:** Quando os dados de uma conta coincidirem com critérios de possível duplicidade, o sistema deverá exibir um alerta para análise humana, sem excluir automaticamente o registro.
- **RF-04 — Consulta:** Quando um usuário consultar contas, o sistema deverá retornar somente registros compatíveis com suas permissões e responsabilidades.
- **RF-05 — Aprovação:** Quando o gestor autorizado aprovar uma conta pendente, o sistema deverá registrar a decisão, o usuário autenticado e a data/hora.
- **RF-06 — Rejeição:** Quando o gestor autorizado rejeitar uma conta, o sistema deverá exigir justificativa e registrar a decisão e a data/hora.
- **RF-07 — Confirmação de pagamento:** Quando um usuário autorizado confirmar o pagamento de uma conta aprovada, o sistema deverá registrar valor pago, data e comprovante ou referência e atualizar o status para Pago.
- **RF-08 — Bloqueio de pagamento:** Se uma conta não estiver aprovada, o sistema deverá impedir sua confirmação como paga.
- **RF-09 — Status/vencimento:** Enquanto uma conta não estiver paga ou cancelada e sua data de vencimento tiver passado, o sistema deverá sinalizá-la como vencida sem apagar o status principal do fluxo.
- **RF-10 — Auditoria:** Quando ocorrer criação, edição permitida, aprovação, rejeição, confirmação, cancelamento ou estorno, o sistema deverá registrar usuário, data/hora, ação e dados relevantes; em alterações, deverá preservar valores anterior e novo.
- **RF-11 — Relatórios:** Quando um usuário autorizado solicitar relatório, o sistema deverá apresentar totais e listagens conforme filtros disponíveis, respeitando suas permissões.
- **RF-12 — Cancelamento/estorno:** Quando um usuário com permissão específica solicitar cancelamento ou estorno, o sistema deverá exigir justificativa e preservar o registro original e seu histórico.

## 6. Requisitos não funcionais

- **RNF-01 Segurança:** autenticação e autorização devem ser verificadas no servidor/camada de aplicação em cada operação; ocultar abas ou botões não é controle suficiente.
- **RNF-02 Integridade:** IDs devem ser únicos; usuários operacionais não podem apagar ou sobrescrever registros financeiros e logs.
- **RNF-03 Auditabilidade:** logs devem ser protegidos contra edição comum e consultáveis apenas por usuários autorizados.
- **RNF-04 Usabilidade:** mensagens de erro e instruções devem ser claras e em português.
- **RNF-05 Recuperação:** deve existir procedimento documentado de backup e restauração, testado antes da entrega final.
- **RNF-06 Desempenho:** limites de volume e tempo de resposta serão definidos após escolha da plataforma e dimensionamento do protótipo.

## 7. Regras de negócio

- **RN-01:** conta válida recém-cadastrada inicia como `Pendente de aprovação`.
- **RN-02:** somente gestor autorizado para aquela conta pode aprovar/rejeitar.
- **RN-03:** rejeição exige justificativa; eventual correção e reenvio preservam a decisão anterior.
- **RN-04:** somente conta aprovada pode ter pagamento confirmado.
- **RN-05:** aprovação não significa pagamento realizado.
- **RN-06:** `Vencida` é indicador calculado e pode coexistir com o status principal.
- **RN-07:** cancelamento/estorno exige permissão e justificativa e não apaga o lançamento original.
- **RN-08:** alerta de duplicidade solicita análise humana; não é exclusão automática.

## 8. Critérios de aceitação — Dado/Quando/Então

- **CA-01 (RF-01/RF-02):** Dado que o solicitante autenticado preencheu todos os campos obrigatórios com dados válidos, quando enviar a conta, então o sistema registra a conta com ID único e status `Pendente de aprovação`.
- **CA-02 (RF-01):** Dado que falta um campo obrigatório, quando o solicitante tentar enviar, então o sistema impede o cadastro e identifica o campo a corrigir.
- **CA-03 (RF-04/RNF-01):** Dado que o usuário não possui permissão para uma conta, quando tentar consultá-la ou alterá-la, então o sistema nega a operação e não revela os dados protegidos.
- **CA-04 (RF-05/RF-08):** Dado que uma conta está pendente ou rejeitada, quando alguém tentar confirmar seu pagamento, então o sistema bloqueia a confirmação.
- **CA-05 (RF-05/RF-06):** Dado que um gestor autorizado decide aprovar ou rejeitar, quando confirmar a decisão, então o sistema registra usuário, data/hora e decisão; se rejeitar, exige justificativa.
- **CA-06 (RF-07):** Dado que uma conta está aprovada, quando um usuário autorizado registrar pagamento com valor, data e comprovante/referência, então o sistema registra a confirmação e altera o status para `Pago`.
- **CA-07 (RF-10):** Dado que ocorre uma operação auditável, quando ela for concluída, então o log registra usuário, data/hora, ação e conta; se houver alteração, registra os valores anterior e novo.
- **CA-08 (RF-03):** Dado que uma conta coincide com os critérios de possível duplicidade, quando for cadastrada, então o sistema exibe alerta e permite análise autorizada sem apagar automaticamente nenhum registro.
- **CA-09 (RF-11):** Dado que um usuário autorizado seleciona filtros de relatório, quando solicitar a consulta, então o relatório apresenta os registros e totais correspondentes e respeita as permissões.
- **CA-10 (RF-12/RNF-02):** Dado que uma conta foi paga ou precisa ser cancelada/estornada, quando um usuário tentar apagá-la diretamente, então o sistema impede a exclusão; correção só ocorre por fluxo autorizado e auditável.
- **CA-11 (RF-09):** Dado que a data atual passou do vencimento e a conta não foi paga nem cancelada, quando a lista for exibida, então o sistema apresenta o indicador `Vencida` sem substituir o status principal.
- **CA-12 (RNF-05):** Dado que existe procedimento de backup configurado, quando a equipe executar restauração em ambiente de teste, então os dados restaurados correspondem ao conjunto salvo, conforme evidência registrada.

## 9. Pontos que a equipe precisa decidir antes da implementação

1. Alçadas/limites de aprovação por valor, categoria ou centro de custo.
2. Uma ou mais aprovações por conta e regra de substituição do gestor.
3. Se solicitante pode confirmar pagamento ou se essa função é sempre separada.
4. Prazo e canal dos alertas de vencimento.
5. Campos exatos do fornecedor/documento fiscal e critérios de duplicidade.
6. Prazo de retenção de logs e política de backup.
7. Volume esperado, número de usuários e restrições da plataforma.
8. Se a equipe aprova a regra de correção por cancelamento/estorno em vez de exclusão direta.

## 10. Dependências e restrições

A implementação depende da aprovação desta especificação, das decisões acima e da revisão por pares/monitoria. A integração bancária e o pagamento automático não fazem parte da versão atual.
