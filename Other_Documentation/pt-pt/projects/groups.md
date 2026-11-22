<!-- Source: https://create.roblox.com/docs/pt-pt/projects/groups -->

Grupos (equipes) | Documentation - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Projects](/docs/en-us/projects)
6. /
7. [Work in teams](/docs/en-us/projects/groups)

# Grupos (equipes)

English

* This content is translated using AI (Beta) and may contain errors. To view this page in English, click [here] .

Um grupo  do Roblox permite que vários criadores trabalhem no mesmo jogo, usem os mesmos ativos, compartilhem lucros e deem crédito a todos os colaboradores.

A propriedade de grupos de jogos ajuda os criadores a colaborar e operar como estúdios independentes. Se um conflito surgir dentro de um grupo, o Roblox não pode ajudar a arbitrar ou resolver desavenças.

## [Criação de grupos](#criação-de-grupos)[](#criação-de-grupos)

Criar um grupo custa 100 Robux. Você pode gerenciar seus [papéis e permissões](#pap%C3%A9is-e-permiss%C3%B5es)  a partir do [Painel do Criador](https://create.roblox.com/dashboard/creations)  ou [Comunidades](https://www.roblox.com/communities) .

Antes de criar um grupo, leia atentamente as [regras e expectativas](/docs/en-us/projects/group-guidelines)  para a gestão de grupos.

Para criar um novo grupo:

1.

Navegue até o [Painel do Criador](https://create.roblox.com/dashboard/creations) , expanda o seletor de conta no canto superior esquerdo e clique no botão mais (+) .

2.

Na página Criar Grupo , faça o upload de uma imagem para o logotipo do grupo e insira o nome do grupo.

3.

Quando estiver pronto, clique no botão Comprar . Assim que o grupo for criado, você será direcionado para a página de perfil do grupo, onde poderá modificar os detalhes do grupo, incluindo adicionar até três links sociais.

## [Papéis e permissões](#papéis-e-permissões)[](#papéis-e-permissões)

Os membros do grupo podem ser atribuídos a um ou vários papéis  dentro de um grupo, e cada papel tem permissões  que especificam as habilidades de seus membros.

A configuração de papéis só é acessível se você for o proprietário do grupo ou tiver permissão para criar, configurar e atribuir papéis do grupo.

Para gerenciar as atribuições de papéis do grupo programaticamente a partir de um servidor de jogo, use [HttpService](/docs/en-us/reference/engine/classes/HttpService)  para chamar os endpoints suportados do Open Cloud Groups. Para configuração e código de exemplo, veja [Usar com Open Cloud](/docs/en-us/cloud-services/http-service#use-with-open-cloud) .

1.

A partir do [Painel do Criador](https://create.roblox.com/dashboard/creations) , expanda o seletor de conta no canto superior esquerdo e selecione o grupo.

2.

Expanda o seletor de conta novamente e selecione Papéis .

3.

Para cada papel, confirme cuidadosamente as permissões na aba Permissions .

As permissões estão organizadas nas categorias General , Creation  e Community . As seções abaixo descrevem as permissões disponíveis em cada categoria.

### [Geral](#geral)[](#geral)

Permissões gerais

| Manage roles | | Membros com esta permissão podem criar, editar, excluir, reordenar e atribuir ou desatribuir papéis abaixo de seu papel mais alto. Eles só podem editar permissões que já possuem. |
| --- | --- |
| Assign or remove roles from members | | Membros com esta permissão podem atribuir ou desatribuir papéis abaixo de seu papel mais alto a qualquer membro. |
| Invite or approve members | | Membros com esta permissão podem convidar pessoas para o grupo e aprovar solicitações de adesão. |
| Kick members | | Membros com esta permissão podem remover membros cujo papel mais alto está abaixo do seu. |
| Ban members | | Membros com esta permissão podem banir membros cujo papel mais alto está abaixo do seu. |
| Configure group profile | | Membros com esta permissão podem configurar o perfil do grupo. |
| View audit logs | | Membros com esta permissão podem visualizar [logs de auditoria do grupo](#logs-de-auditoria-do-grupo) . |
| Manage allies and enemies | | Membros com esta permissão podem gerenciar os aliados e inimigos do grupo. |

### [Criação](#criação)[](#criação)

Creations

| Playtest experiences | | Membros com este papel podem jogar todos os jogos de propriedade do grupo, mesmo que não estejam lançados para um público mais amplo. Disponível opcionalmente como uma [permissão por jogo](/docs/en-us/projects/configure-games) . |
| Edit experiences | | Membros com este papel podem editar todos os jogos e [ativos](/docs/en-us/projects/assets)  de propriedade do grupo e usar todos os recursos no [Gerenciador de Armazenamento de Dados](/docs/en-us/cloud-services/data-stores/data-stores-manager) . Não inclui editar um jogo fora de uma sessão [colaborativa](/docs/en-us/projects/collaboration)  ou salvar um lugar de um jogo em outro jogo. Disponível opcionalmente como uma [permissão por jogo](/docs/en-us/projects/configure-games) . |
| Publish experiences | | Membros com este papel podem tanto editar jogos, como acima, quanto publicar jogos no Roblox. Disponível opcionalmente como uma [permissão por jogo](/docs/en-us/projects/configure-games) . |
| Manage share links | | Membros com este papel podem criar/configurar [links de compartilhamento](/docs/en-us/production/promotion/share-links) . |
| Manage experience events | | Membros com este papel podem criar/configurar [eventos de experiência](/docs/en-us/production/promotion/experience-events) . |
| Moderate experiences | | Membros com este papel podem visualizar todas as mensagens de chat no jogo (somente leitura; o membro deve ter 18 anos ou mais) e banir ou gerenciar usuários banidos em todos os jogos de propriedade do grupo. |
| Manage monetization for experiences | | Membros com este papel podem gerenciar produtos de monetização, como [passes](/docs/en-us/production/monetization/passes) , [produtos de desenvolvedor](/docs/en-us/production/monetization/developer-products) , [assinaturas](/docs/en-us/production/monetization/subscriptions)  e mais. Disponível opcionalmente como uma [permissão por jogo](/docs/en-us/projects/configure-games) . |
| Manage secrets for experiences | | Membros com este papel podem ver a lista de [segredos](/docs/en-us/cloud-services/secrets)  e podem criar, atualizar e excluir segredos para todos os jogos de propriedade do grupo. Membros com este papel requerem a permissão Edit experiences  para visualizar a página de Segredos. Disponível opcionalmente como uma [permissão por jogo](/docs/en-us/projects/configure-games) . |

Analytics

| View analytics for experiences | | Membros com este papel podem acessar as [análises](/docs/en-us/production/analytics)  de todos os jogos de propriedade do grupo, mesmo que não tenham acesso de edição. Disponível opcionalmente como uma [permissão por jogo](/docs/en-us/projects/configure-games) . |
| Manage alerts | | Membros com este papel podem criar e gerenciar alertas de análise. Combine esta permissão com View analytics for experiences  para ver anotações de alerta diretamente nos gráficos de métricas. |

Monetization

| View group revenue | | Membros com este papel podem visualizar o saldo de Robux do grupo, quaisquer pagamentos recorrentes configurados e recursos de registro de receita. |
| Manage and spend group revenue | | Membros com este papel podem visualizar toda a receita do grupo, como acima, e também gerenciá-la diretamente. Isso inclui configurar [pagamentos recorrentes](#pagamentos-recorrentes)  e enviar [pagamentos únicos](#pagamentos-%C3%BAnicos)  para colaboradores. |
| Create ad campaigns for the group | | Membros com este papel podem anunciar o grupo. |

Avatar items

| Create avatar items | | Membros com este papel podem criar itens de avatar, como roupas. |
| Configure avatar items | | Membros com este papel podem configurar detalhes de vendas, reabastecimentos e patrocínios para itens de avatar existentes do grupo. |

API

| Manage API keys | | Membros com este papel podem gerenciar [chaves de API do Open Cloud](/docs/en-us/cloud/auth/api-keys)  para o grupo. |

Development items

| View development items | | Membros com este papel podem visualizar itens de desenvolvimento de propriedade do grupo, por exemplo Áudio . |
| Manage development items | | Membros com este papel podem fazer upload e configurar itens de desenvolvimento de ativos, como Decais . |
| Manage development item permissions | | Membros com este papel podem configurar permissões de itens de desenvolvimento, por exemplo, compartilhamento de áudio. |

Data Stores

| View Data Stores for experiences | | Membros com este papel podem visualizar armazenamentos de dados para todos os jogos do grupo através do [Gerenciador de Armazenamento de Dados](/docs/en-us/cloud-services/data-stores/data-stores-manager) , mas não podem excluir dados. Disponível opcionalmente como uma [permissão por jogo](/docs/en-us/projects/configure-games) . |
| Edit Data Stores for experiences | | Membros com este papel podem excluir chaves específicas dentro de armazenamentos de dados para todos os jogos do grupo através do [Gerenciador de Armazenamento de Dados](/docs/en-us/cloud-services/data-stores/data-stores-manager) . Disponível opcionalmente como uma [permissão por jogo](/docs/en-us/projects/configure-games) . |
| Delete Data Stores for experiences | | Membros com este papel podem excluir armazenamentos de dados inteiros para todos os jogos do grupo através do [Gerenciador de Armazenamento de Dados](/docs/en-us/cloud-services/data-stores/data-stores-manager) . Disponível opcionalmente como uma [permissão por jogo](/docs/en-us/projects/configure-games) . |

Notifications

| Manage webhooks for experiences | | Membros com este papel podem listar, criar, atualizar e excluir webhooks para todas as experiências do grupo. |

Communication

| Manage support tickets for experiences | | Membros com este papel podem gerenciar tickets de suporte para todas as experiências do grupo. |

Legacy

| Gerenciar acesso aos recursos deste grupo | | Membros com este papel podem criar e editar o acesso aos recursos do grupo. |

### [Comunidade](#comunidade)[](#comunidade)

Posts

| View community announcements | | Membros com este papel podem visualizar anúncios da comunidade. |
| Create community announcements | | Membros com este papel podem criar anúncios da comunidade. |

Forums

| Manage categories | | Membros com este papel podem gerenciar categorias de fórum. |
| Create posts | | Membros com este papel podem criar postagens no fórum. |
| Remove posts | | Membros com este papel podem remover postagens do fórum. |
| Lock posts | | Membros com este papel podem bloquear postagens do fórum. |
| Pin posts | | Membros com este papel podem fixar postagens do fórum. |
| Create comments | | Membros com este papel podem criar comentários em postagens do fórum. |
| Remove comments | | Membros com este papel podem remover comentários de postagens do fórum. |

Content moderation

| View content moderation | | Membros com este papel podem visualizar a moderação de conteúdo. |
| Manage content moderation | | Membros com este papel podem gerenciar a moderação de conteúdo. |

Miscellaneous

| Bypass slow mode | | Membros com este papel podem ignorar o modo lento. |
| View community analytics | | Membros com este papel podem visualizar análises da comunidade. |

4.

IMPORTANTE

 Clique no botão Save  para aplicar as configurações de permissão.

5.

OPCIONAL

 Clique na aba Settings  e escolha uma cor e configuração de visibilidade para o papel, em seguida clique no botão Save .

A seção Settings  de um papel é também onde os proprietários do grupo e membros com permissões suficientes podem remover um papel completamente através do botão Excluir Papel .

Os papéis são listados em ordem hierárquica: um papel mais alto na lista tem mais autoridade do que um papel abaixo dele. Esta ordem é importante porque algumas permissões só permitem que os membros gerenciem papéis abaixo de seu próprio papel mais alto.

Cada papel é público  ou privado . Papéis públicos podem ser exibidos em uma página da Comunidade e em experiências. Papéis privados são exibidos apenas em superfícies de gerenciamento de papéis e permissões para membros autorizados, ou para membros que possuem o papel privado. A visibilidade altera onde um papel aparece; não altera as permissões que o papel concede.

Para conceder Manage roles , Assign or remove roles from members , Manage access to this group’s resources , Manage and spend group revenue  ou Delete Data Stores for experiences , você deve ter a verificação em duas etapas ativada.

## [Gerenciar membros](#gerenciar-membros)[](#gerenciar-membros)

A configuração de membros só é acessível se você for o proprietário do grupo ou tiver permissão para gerenciar outros membros e seus papéis.

Para gerenciar membros a partir do Painel do Criador:

1.

Expanda o seletor de conta no canto superior esquerdo e selecione o grupo.

2.

Expanda o seletor de conta novamente e selecione Members .

3.

Use a aba Membro  para pesquisar membros existentes ou filtrá-los por papel. Use a aba Convidados  para revisar convites pendentes.

Para adicionar um membro, clique no botão Invite  e pesquise pelo nome de usuário deles. O Roblox notifica os criadores convidados de acordo com suas preferências de notificação. Você também pode copiar o link do grupo e compartilhá-lo diretamente.

### [Gerenciar papéis](#gerenciar-papéis)[](#gerenciar-papéis)

Você pode gerenciar as atribuições de papéis a partir da página Members  ou de um papel específico:

-

Na página Members , clique no botão mais (+)  ao lado de um membro para abrir o menu de papéis. Para atribuir um papel, clique no botão mais (+)  ao lado dele em Adicionar papéis . Para desatribuir um papel, clique no botão menos (-)  ao lado dele em Papéis atuais , ou clique no botão ×  em um papel atribuído ao lado do nome do membro.

-

Na página Papéis , selecione um papel e abra sua aba Members . Clique no botão Add members  para pesquisar membros do grupo e atribuí-los ao papel. Para desatribuir um membro, clique no botão menos (-)  no final da linha deles.

### [Remoção de membros](#remoção-de-membros)[](#remoção-de-membros)

Para remover um membro do grupo, clique no botão ⋮  no final da linha deles, selecione Expulsar usuário  e confirme a ação.

## [Gerenciar pagamentos](#gerenciar-pagamentos)[](#gerenciar-pagamentos)

Se você for o proprietário do grupo ou tiver a [permissão](#pap%C3%A9is-e-permiss%C3%B5es)  correta dentro de Receita do Grupo , você encontrará uma página Pagamentos  em Finanças  na navegação à esquerda. Aqui, você pode enviar pagamentos únicos, bem como definir divisões percentuais com outros membros.

Alguns grupos podem não ter esta página desbloqueada inicialmente por vários motivos, como a idade do grupo ou fundos insuficientes para pagamento.

Os pagamentos não podem ser compartilhados entre membros do grupo para jogos que cobram por [acesso pago em moeda local](/docs/en-us/production/monetization/paid-access-local-currency) .

### [Pagamentos únicos](#pagamentos-únicos)[](#pagamentos-únicos)

Pagamentos únicos podem ser feitos a membros em um lote, selecionando um valor definido para cada um. Recursos de segurança incluem desafios de 2FA, diálogos de confirmação e verificações em torno da elegibilidade dos membros a serem pagos.

 ![Botão de pagamento único indicado na seção de Pagamentos do Painel do Criador.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Group-Payouts-One-Time.png)

Uma vez que você clique no botão Enviar Robux , você pode escolher os destinatários do pagamento na janela pop-up ou fazer upload de um arquivo de planilha .csv  com as colunas userId  e payoutInRobux , por exemplo:

| userId | | payoutInRobux |
| 012345 | | 5000 |
| 098765 | | 7000 |

### [Pagamentos recorrentes](#pagamentos-recorrentes)[](#pagamentos-recorrentes)

Pagamentos recorrentes também podem ser feitos em todo o grupo e  por jogo, atribuindo um pagamento percentual a cada membro antes que o restante entre no saldo geral do grupo.

 ![Botões de pagamento dividido indicados na seção de Pagamentos do Painel do Criador.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Group-Payouts-Split-Options.png)

Considere o seguinte cenário onde um jogo do grupo Laser Maze  é dividido 40%–30%–10% entre três membros, com um restante de 20%.

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-A.png)

Assumindo que o jogo ganha 1000 Robux, os três membros recebem 400, 300 e 100 Robux, respectivamente (40%–30%–10%).

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-B.png)

O restante de 200 Robux (20% da divisão do jogo) passa para as porcentagens de divisão do grupo , definidas em 20%–20%–10% entre os mesmos três membros; eles recebem um adicional de 40, 40 e 20 Robux, respectivamente.

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-C.png)

O restante de 100 Robux (50% da divisão do grupo) é colocado no saldo geral do grupo.

 ![Exemplo de fluxograma de como as divisões de jogos são distribuídas primeiro para os membros do grupo, com o restante sendo considerado nas divisões do grupo para a distribuição final entre o grupo.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Group-Payouts-Splits-Example.png)

Observe que a receita de assinaturas de [servidores privados](/docs/en-us/production/monetization/private-servers)  não muda se você ajustar as porcentagens de divisão em um momento posterior, significando que se um jogador comprar uma assinatura de servidor privado, as porcentagens de divisão no momento da compra se aplicarão a essa assinatura particular para sempre (até que seja cancelada). Esta política pode ser alterada no futuro.

## [Logs de auditoria do grupo](#logs-de-auditoria-do-grupo)[](#logs-de-auditoria-do-grupo)

Membros do grupo com a permissão View audit logs  podem revisar as alterações do grupo usando estas superfícies de gerenciamento de grupo:

-

No Painel do Criador, selecione Histórico de Atividades  em Colaboração .

-

Nas Comunidades, abra a página de configuração da comunidade e selecione Log de Auditoria .

Os proprietários do grupo podem usar esses logs para monitorar atividades que possam violar as [diretrizes do grupo](/docs/en-us/projects/group-guidelines) .

## [Proteção da propriedade intelectual](#proteção-da-propriedade-intelectual)[](#proteção-da-propriedade-intelectual)

Membros do grupo com permissão para editar todos os jogos do grupo podem ativar a configuração de [Cópia de Lugar](/docs/en-us/projects/configure-games#allow-copying)  para uma criação, permitindo potencialmente que toda a comunidade Roblox a copie e use ativos dentro dela. Para ajudar a proteger a propriedade intelectual em um grupo, o proprietário ou membros com permissões suficientes devem:

-

Confirmar que cada membro está [atribuído ao papel apropriado](#gerenciar-pap%C3%A9is) .

-

Verificar se cada papel do grupo tem as [permissões](#pap%C3%A9is-e-permiss%C3%B5es)  corretas.

-

Confirmar que a configuração de [Cópia de Lugar](/docs/en-us/projects/configure-games#allow-copying)  está desativada antes que ativos privados sejam adicionados.

## [Localizações adicionais para esta página](#localizações-adicionais-para-esta-página)[](#localizações-adicionais-para-esta-página)

Para versões adicionais e localizadas desta página que não estão disponíveis no seletor de idiomas do site, veja os seguintes links:

-

[Búlgaro (български)](https://create.roblox.com/docs/bg-bg/projects/groups)

-

[Croata (hrvatski)](https://create.roblox.com/docs/hr-hr/projects/groups)

-

[Tcheco (čeština)](https://create.roblox.com/docs/cs-cz/projects/groups)

-

[Dinamarquês (dansk)](https://create.roblox.com/docs/da-dk/projects/groups)

-

[Holandês (Nederlands)](https://create.roblox.com/docs/nl-nl/projects/groups)

-

[Estoniano (eesti)](https://create.roblox.com/docs/et-ee/projects/groups)

-

[Finlandês (suomi)](https://create.roblox.com/docs/fi-fi/projects/groups)

-

[Grego (Ελληνικά)](https://create.roblox.com/docs/el-gr/projects/groups)

-

[Húngaro (magyar)](https://create.roblox.com/docs/hu-hu/projects/groups)

-

[Irlandês (Gaeilge)](https://create.roblox.com/docs/ga-ie/projects/groups)

-

[Letão (latviešu)](https://create.roblox.com/docs/lv-lv/projects/groups)

-

[Lituano (lietuvių)](https://create.roblox.com/docs/lt-lt/projects/groups)

-

[Maltês (Malti)](https://create.roblox.com/docs/mt-mt/projects/groups)

-

[Português - Portugal (português)](https://create.roblox.com/docs/pt-pt/projects/groups)

-

[Romeno (română)](https://create.roblox.com/docs/ro-ro/projects/groups)

-

[Eslovaco (slovenčina)](https://create.roblox.com/docs/sk-sk/projects/groups)

-

[Esloveno (slovenščina)](https://create.roblox.com/docs/sl-si/projects/groups)

-

[Sueco (svenska)](https://create.roblox.com/docs/sv-se/projects/groups)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
