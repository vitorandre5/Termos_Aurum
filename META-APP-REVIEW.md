# Preparacao de App Review da Meta - ZapDetail

**Status:** integracao planejada; nao ativa. Este documento nao afirma elegibilidade, acesso concedido ou aprovacao da Meta.
**Atualizado:** 2026-10-09

## Produto e caso de uso

ZapDetail e um software de agendamento para negocios de estetica automotiva em geral. E destinado a varias empresas, cada uma usando o servico para apoiar sua propria operacao; nao e uma ferramenta exclusiva de uma unica empresa.

Agendamentos e dados operacionais podem ser inseridos pelo dashboard web ou enviados por WhatsApp. A integracao planejada com a Plataforma WhatsApp Business recebera mensagens do proprietario e de funcionarios autorizados e apoiara a organizacao de horarios e agendamentos. Um cliente tambem podera iniciar uma conversa para solicitar atendimento ou horario. O conteudo necessario podera ser processado em workflows n8n e enviado a API da OpenAI para gerar uma resposta automatizada, conforme a configuracao efetivamente implementada.

A automacao para clientes respondera dentro da janela de atendimento de 24 horas aberta ou renovada pela mensagem mais recente do cliente. Fora dela, mensagens iniciadas pelo negocio exigem modelos aprovados e cumprimento das regras aplicaveis da Meta. Deve haver um caminho direto para atendimento humano. O produto nao deve iniciar contato sem permissao, enviar campanhas ou fazer envio em massa. O fluxo nao depende de mensagens em grupos.

## Dados e provedores

Os dados podem incluir conteudo e identificadores de mensagens, numero e nome de perfil quando disponiveis, data e hora e informacoes de agendamento (servico, data, horario, cliente e profissional). Dados necessarios podem transitar pela Meta, n8n e API da OpenAI. Google Drive e Google Sheets permanecem listados como integracoes existentes nas paginas; confirmar se continuam no produto ZapDetail e em quais fluxos antes de submeter.

A politica publica descreve os dados de mensagens e agendamento, provedores, uso, retencao conhecida e pedidos de acesso ou exclusao. Retencao e configuracoes reais do n8n/OpenAI ainda precisam ser verificadas antes da ativacao. A pagina publica inclui uma captura demonstrativa do painel com valores ficticios. Ela contextualiza a interface do produto, mas nao demonstra o fluxo de mensagens e agendamentos pelo WhatsApp; esse fluxo precisa aparecer na demonstracao submetida.

## Permissoes a avaliar no painel

- `whatsapp_business_messaging`: envio e recebimento de mensagens da Plataforma WhatsApp Business.
- `whatsapp_business_management`: ativos WhatsApp e assinatura da WABA para webhooks, conforme endpoints efetivamente usados.
- `business_management`: nao solicitar por padrao; avaliar somente se algum endpoint requerido exigir essa permissao.
- Confirmar o fluxo de App Review, nivel de acesso, requisitos de onboarding de clientes e permissoes exatas no painel da Meta.

## Requisitos antes da submissao

1. Confirmar a elegibilidade do app, da WABA, dos numeros e do fluxo de onboarding para oferecer o produto a varios negocios.
2. Demonstrar que mensagens e agendamentos de cada negocio permanecem isolados e acessiveis somente por usuarios autorizados desse negocio.
3. Definir e implementar avisos, opt-in verificavel e opt-out para clientes e funcionarios; respeitar pedidos de interrupcao.
4. Confirmar configuracoes de retencao do n8n e endpoint/armazenamento da OpenAI; atualizar a politica com os prazos reais.
5. Implementar e demonstrar a opcao clara de escalonamento humano indicada na politica: `vitorandregsilva@gmail.com`.
6. Gravar uma demonstracao fiel do fluxo completo: autorizacao/onboarding, mensagem de proprietario ou funcionario, pedido de agendamento do cliente, resposta, opcao humana e respeito a janela de 24 horas/modelos aprovados. Nao mostrar recursos ainda nao habilitados.
7. Confirmar se Google Drive e Sheets fazem parte do produto ZapDetail e alinhar politica, escopos e telas com o comportamento real.

## Texto-base para revisar no painel da Meta

> ZapDetail e um software de agendamento para diferentes negocios de estetica automotiva. Cada negocio usa o servico para apoiar a propria operacao. O sistema permite inserir agendamentos e dados pelo dashboard web ou enviar essas informacoes por WhatsApp. Com a Plataforma WhatsApp Business, recebera mensagens do proprietario e de funcionarios autorizados para ajudar a organizar horarios. Clientes poderao iniciar conversas para solicitar atendimento ou agendamento. O sistema processara somente os dados necessarios para responder e organizar a agenda, usando n8n e a API da OpenAI conforme configurado. Respostas automatizadas a clientes ocorrerao dentro da janela de atendimento de 24 horas; fora dela, somente com modelos aprovados e conforme as regras aplicaveis. Havera um caminho direto de atendimento humano. O servico nao enviara campanhas, mensagens em massa ou mensagens nao solicitadas. A integracao permanece inativa enquanto permissao, elegibilidade, onboarding e configuracoes sao confirmados.

Revisar este texto para corresponder exatamente ao produto implementado e ao video submetido; nao afirmar capacidades indisponiveis.

## Fontes oficiais

- [WhatsApp Business Messaging Policy](https://whatsappbusiness.com/policy/) - atualizada em 2026-09-23; opt-in, opt-out, janela de 24 horas, modelos e escalonamento humano.
- [WhatsApp Cloud API - documentacao oficial Meta no Postman](https://www.postman.com/meta/whatsapp-business-platform/documentation/wlk6lh4/whatsapp-cloud-api) - requisitos gerais, ativos e permissoes devem ser verificados novamente no painel.
