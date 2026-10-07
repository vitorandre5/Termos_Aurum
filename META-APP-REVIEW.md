# Rascunho para acesso à API do WhatsApp Business — Aurum Dashboard

**Status:** preparação; integração não ativa. Este material não confirma elegibilidade, acesso concedido ou aprovação da Meta.

## Descrição do caso de uso

O Aurum Dashboard é uma ferramenta interna usada pela própria Aurum Detailing. A integração planejada usará a Plataforma WhatsApp Business, n8n e a API da OpenAI para apoiar o controle operacional em grupos internos restritos a funcionários e responder a conversas individuais iniciadas pelos próprios clientes.

O fluxo enviará respostas automáticas. Nas conversas individuais com clientes, só responderá dentro da janela de atendimento de 24 horas aberta e renovada pela mensagem mais recente do cliente. Quando a janela expirar, este fluxo não enviará mensagens. A resposta automática oferecerá um caminho direto para atendimento humano pelo e-mail vitorandregsilva@gmail.com. O fluxo não iniciará conversas, não fará campanhas, publicidade nem envio em massa.

Nas mensagens processadas, podem ser tratados conteúdo, identificadores de mensagens, grupos e contas, nomes de perfil disponíveis, data e hora e anexos efetivamente enviados ao fluxo. O conteúdo necessário poderá transitar pela Meta, ser processado pelo n8n e ser enviado à API da OpenAI para gerar respostas. A política de privacidade do site descreve os dados, provedores, retenção conhecida, solicitações de exclusão e pendências de configuração.

## Permissões e recursos previstos

- `whatsapp_business_messaging`: envio e recebimento de mensagens da Plataforma WhatsApp Business.
- `whatsapp_business_management`: gestão de ativos WhatsApp e assinatura da WABA para recebimento de webhooks, conforme os endpoints utilizados.
- `business_management`: não solicitar por padrão; só avaliar se a implementação passar a consultar endpoints do portfólio empresarial que exijam essa permissão.
- A WABA precisa estar inscrita para entregar webhooks ao app. A concessão efetiva das permissões e o token de produção ainda precisam ser verificados no painel da Meta.
- O app é de uso próprio da Aurum. Confirmar no painel da Meta o nível de acesso aplicável a essa relação de propriedade antes de definir se esta solicitação é uma revisão de permissões ou outro fluxo de ativação.

## Limite específico de grupos

A Groups API oficial não deve ser tratada como acesso genérico aos grupos comuns já existentes. A documentação consultada indica requisito de Conta Comercial Oficial (OBA), adesão dos participantes por convite e limite de até oito participantes por grupo. A compatibilidade desta WABA, o acesso ao recurso de grupos e a possibilidade de usar cada grupo operacional pretendido não foram confirmados. Não submeter a capacidade de ler ou responder nos grupos atuais como fato; confirmar se será necessário criar grupos compatíveis pela API e migrar o uso operacional.

## Texto curto para adaptar no painel da Meta

> O Aurum Dashboard é uma ferramenta interna da Aurum Detailing. Planejamos usar a Plataforma WhatsApp Business para processar mensagens de grupos operacionais internos elegíveis e responder automaticamente a conversas individuais iniciadas por clientes. As respostas individuais serão limitadas à janela de atendimento de 24 horas, renovada pela mensagem mais recente do cliente; após o vencimento, o fluxo não enviará mensagens. A resposta automática dará acesso direto ao atendimento humano pelo e-mail informado na política de privacidade. O fluxo usa n8n e a API da OpenAI para processar o conteúdo necessário à resposta. Não iniciamos conversas com clientes e não fazemos campanhas nem envio em massa. A integração permanece inativa enquanto verificamos elegibilidade, permissões e limites da Meta.

## Evidências e pendências antes de submeter

1. Confirmar se a WABA e o número da Aurum são elegíveis à Cloud API e à Groups API, incluindo status OBA, permissões, modo de onboarding e disponibilidade do recurso no app.
2. Identificar quais grupos internos são pretendidos, seus participantes e se atendem ao limite e ao modelo de convite. Não presumir acesso aos grupos atuais.
3. Confirmar no painel da Meta as permissões `whatsapp_business_messaging` e `whatsapp_business_management`, o nível de acesso necessário e a assinatura da WABA para webhooks.
4. Definir e implementar como funcionários e clientes receberão aviso sobre automação e compartilhamento, como serão obtidos e registrados opt-ins/consentimentos aplicáveis e como pedidos de interrupção serão respeitados.
5. Verificar hospedagem, versão e configurações do n8n, incluindo gravação/poda das execuções; definir o endpoint da OpenAI e se haverá armazenamento de estado. Ajustar a Política de Privacidade depois dessas escolhas.
6. Implementar e demonstrar a opção de escalonamento humano na própria resposta automática. O e-mail publicado é o canal informado; confirmar que o fluxo o apresentará de forma direta.
7. Preparar uma demonstração fiel do fluxo aprovado: mensagem de funcionário em grupo elegível, mensagem de cliente iniciando conversa, resposta automática e opção humana, além do bloqueio de envio após 24 horas. Não demonstrar grupos ou permissões ainda não habilitados.

## Referências oficiais consultadas

- [WhatsApp Business Messaging Policy](https://whatsappbusiness.com/policy/) — opt-in, janela de atendimento de 24 horas, automação com escalonamento humano e avisos/consentimentos.
- [Meta WhatsApp Groups API](https://developers.facebook.com/docs/whatsapp/cloud-api/groups/) — elegibilidade e limites de grupos; confirmar novamente no painel da WABA antes da submissão.
- [Coleção oficial da Meta para WhatsApp Cloud API no Postman](https://www.postman.com/meta/whatsapp-business-platform/documentation/wlk6lh4/whatsapp-cloud-api) — permissões da API e uso de webhooks.
- [n8n: Manage execution data](https://docs.n8n.io/hosting/scaling/execution-data/) — gravação e poda de execuções.
- [OpenAI API: Data controls](https://developers.openai.com/api/docs/guides/your-data) — treinamento, logs de abuso e retenção por endpoint.