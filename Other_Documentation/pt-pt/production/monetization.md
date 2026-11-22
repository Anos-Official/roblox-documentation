<!-- Source: https://create.roblox.com/docs/pt-pt/production/monetization -->

Monetização | Documentation - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)

# Monetização

English

* This content is translated using AI (Beta) and may contain errors. To view this page in English, click [here] .

A monetização é uma parte da estrutura geral do Roblox para fornecer valor aos criadores. Existem várias abordagens diferentes para monetizar seu conteúdo, incluindo a utilização de [assinaturas](#assinaturas) , cobrança de uma taxa de acesso em [Robux](#acesso-pago-em-robux)  ou [moeda local](#acesso-pago-em-moeda-local) , fornecimento de [itens ou habilidades que os usuários podem comprar](#produtos-do-desenvolvedor) , oferta de [servidores privados](#servidores-privados)  para os usuários jogarem apenas com amigos, e [venda de modelos e plugins](/docs/en-us/production/creator-store#distribute-and-sell-assets)  para outros criadores na Loja do Criador.

Se você optar por oferecer conteúdo comprável, o Roblox não registra automaticamente informações sobre produtos ou compras. Para evitar a perda de dados, você deve armazenar cuidadosamente esses dados usando [DataStoreService](/docs/en-us/reference/engine/classes/DataStoreService)  ou outro serviço de armazenamento de dados hospedado fora do Roblox.

Para uma análise aprofundada sobre como projetar estratégias de monetização ideais para sua experiência, veja [Fundamentos da monetização](/docs/en-us/production/game-design/monetization-foundations) .

## [Estratégias de monetização](#estratégias-de-monetização)[](#estratégias-de-monetização)

Tenha em mente os métodos de monetização que você introduz em seu jogo, pois nossos usuários provavelmente votarão negativamente  em seu jogo se não aprovarem suas estratégias. Além disso, todos os desenvolvedores precisam ser transparentes com qualquer [monetização baseada em chance](/docs/en-us/production/monetization/paid-random-items)  e usar essas mecânicas de forma responsável.

Algumas estratégias de monetização populares para jogos free-to-play em outras plataformas não são recomendadas para o Roblox. Por exemplo, mecânicas de agendamento e temporizadores que podem ser removidos ou adiantados podem funcionar bem em outras plataformas, mas essas mecânicas são impopulares entre os usuários do Roblox, que se incomodam com a diversão chegando ao fim prematuramente.

As seguintes sugestões de melhores práticas são populares entre os principais desenvolvedores para adaptar estratégias de monetização à plataforma e ao público do Roblox.

Por favor, note que ao aplicar essas técnicas e considerações, você não tem garantia de que conseguirá monetizar efetivamente seu jogo. Lembre-se de que você não precisa ter objetivos financeiros para se divertir criando um jogo no Roblox.

### [Turistas e locais](#turistas-e-locais)[](#turistas-e-locais)

Pode ser útil pensar nos usuários do Roblox em duas categorias:

-

Turistas  normalmente pulam de um jogo para outro, priorizando variedade em vez de profundidade. Eles preferem itens com efeitos imediatos, seja tornando a jogabilidade mais divertida ou fazendo com que se destaquem, convidando outros usuários a questionar como e onde conseguiram o item.

-

Locais  são mais propensos a se concentrar em um jogo específico ou em um conjunto menor de jogos. Eles se envolvem mais profundamente e, tipicamente, formam quase toda a base de usuários engajados de um jogo. Eles estão mais interessados em itens com benefícios a longo prazo, como um [passe de batalha](/docs/en-us/production/game-design/season-pass-design) .

Para saber mais sobre como projetar seu jogo com os usuários do Roblox em mente, veja [Design para Roblox](/docs/en-us/production/game-design/design-for-roblox) .

### [Recursos sociais](#recursos-sociais)[](#recursos-sociais)

Os usuários do Roblox tendem a gostar de jogos que enfatizam a interação social. Por exemplo, ter itens ou eventos que estão disponíveis apenas por um tempo limitado  pode criar empolgação em torno desse conteúdo. Um sistema de trocas  incentiva os usuários a interagir. Embora ambos os sistemas possam ser bem-sucedidos por conta própria, eles são particularmente eficazes quando combinados.

### [Operações ao vivo](#operações-ao-vivo)[](#operações-ao-vivo)

O suporte pós-lançamento é, em muitos aspectos, mais fácil no Roblox do que em outras plataformas, pois você pode rapidamente enviar atualizações para melhorar seu jogo.

Atualizações de conteúdo frequentes  podem ser úteis se você quiser manter o engajamento com seu jogo ao longo do tempo. Os usuários do Roblox estão acostumados a serem engajados por atualizações regulares, e pode ser muito mais difícil recuperar o interesse de um usuário do que manter os ativos. Uma cadência semanal  para atualizações é ideal. No mínimo, busque atualizações mensais. Para uma discussão sobre cadência de conteúdo, veja o workshop de [cadência de conteúdo](/docs/en-us/production/game-design/content-updates) .

Ao projetar atualizações, mantenha-as focadas em um tema  específico. Isso facilita para os usuários entenderem a nova atualização e perceberem qual conteúdo é novo quando entram. Também ajuda você a coordenar seu conteúdo e ativos promocionais. Por exemplo, se você está adicionando um novo Zoológico ao seu jogo de interpretação de papéis, certifique-se de que todo o novo conteúdo tenha alguma conexão com o tema do Zoológico.

Não tenha medo de fazer os usuários ganharem seu acesso  a novos conteúdos. Novos usuários vão se aglomerar para jogar novas atualizações, mas se não sentirem que conquistaram  algo no jogo, podem sair logo depois. Você pode criar uma sensação de conquista de uma atualização, seja monetizando o conteúdo da atualização ou criando condições pré-requisito para jogar o novo conteúdo.

Para saber mais sobre como projetar um suporte pós-lançamento eficaz para seu jogo, veja [Essenciais de operações ao vivo](/docs/en-us/production/game-design/liveops-essentials) .

## [Produtos](#produtos)[](#produtos)

### [Anúncios imersivos](#anúncios-imersivos)[](#anúncios-imersivos)

O sistema de [anúncios imersivos](/docs/en-us/production/monetization/immersive-ads)  permite que você insira unidades de anúncios em seu jogo que permitem ao Roblox servir programaticamente conteúdo publicitário de anunciantes para seus usuários ativos.

![](https://prod.docsiteassets.roblox.com/assets/monetization/immersive-ads/Overview-ImageAd.jpg) Formato de anúncio de imagem

Formato de anúncio de portal

### [Roblox Plus](#roblox-plus)[](#roblox-plus)

[Roblox Plus](/docs/en-us/production/monetization/roblox-plus)  permite que você ganhe através de compras dentro do jogo aumentadas por descontos subsidiados pelo Roblox, bônus de inscrição para cada novo assinante que você trouxer e engajamento em servidores privados pagos.

### [Assinaturas](#assinaturas)[](#assinaturas)

[Assinaturas](/docs/en-us/production/monetization/subscriptions)  dentro dos jogos permitem que você ofereça aos usuários benefícios recorrentes por uma taxa mensal.

![](https://prod.docsiteassets.roblox.com/assets/monetization/subscriptions/Example-Subscriptions.png) Exemplos de assinaturas de jogos

### [Passes](#passes)[](#passes)

Um [passe](/docs/en-us/production/monetization/passes)  permite que você cobre uma taxa única em Robux  para que os usuários acessem privilégios especiais dentro de um jogo, como entrada em uma área restrita, um item de avatar no jogo ou um power-up permanente.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/passes/passes-sample.png)

### [Produtos do desenvolvedor](#produtos-do-desenvolvedor)[](#produtos-do-desenvolvedor)

Um [produto do desenvolvedor](/docs/en-us/production/monetization/developer-products)  é um item ou habilidade que um usuário pode comprar mais de uma vez, como moeda do jogo, munição ou poções. Você pode solicitar compras, registrá-las e obter informações sobre o produto através de scripts.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/developer-products/Buy-Product-Example.jpg)

### [Preços gerenciados](#preços-gerenciados)[](#preços-gerenciados)

[Preços gerenciados](/docs/en-us/production/monetization/managed-pricing)  é um sistema unificado que reúne [preços regionais](/docs/en-us/production/monetization/regional-pricing)  e [otimização de preços](/docs/en-us/production/monetization/price-optimization)  em um só lugar. Você opta por participar uma vez, escolhe quais itens incluir, e os preços gerenciados mantêm seus preços otimizados ao longo do tempo em produtos e regiões.

### [Otimização de preços](#otimização-de-preços)[](#otimização-de-preços)

[A otimização de preços](/docs/en-us/production/monetization/price-optimization)  permite que você encontre os melhores pontos de preço para seus passes e produtos do desenvolvedor, o que pode ajudá-lo a ganhar mais dinheiro ao longo do tempo, mantendo seus preços competitivos.

### [Acesso pago em Robux](#acesso-pago-em-robux)[](#acesso-pago-em-robux)

[O acesso pago em Robux](/docs/en-us/production/monetization/paid-access-robux)  permite que você cobre dos usuários uma taxa única em Robux  para acessar seu jogo. Alguns desenvolvedores usam temporariamente esse recurso para criar um beta fechado onde seus usuários mais engajados podem ter acesso antecipado a um jogo e ajudar com testes e feedback.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/paid-access/Buy-Access-Example.png)

### [Acesso pago em moeda local](#acesso-pago-em-moeda-local)[](#acesso-pago-em-moeda-local)

[O acesso pago em moeda local](/docs/en-us/production/monetization/paid-access-local-currency)  permite que você cobre dos usuários uma taxa única em sua moeda local  para acessar seu jogo. Se a moeda local deles não estiver disponível, eles serão cobrados em USD. Alguns desenvolvedores usam temporariamente esse recurso para criar um beta fechado onde seus usuários mais engajados podem ter acesso antecipado a um jogo e ajudar com testes e feedback.

### [Servidores privados](#servidores-privados)[](#servidores-privados)

Um [servidor privado](/docs/en-us/production/monetization/private-servers)  é um recurso baseado em assinatura que permite a um usuário decidir quem pode jogar um jogo com eles. Embora os servidores privados possam ser gratuitos, você também pode usar servidores privados como um método de monetização cobrando dos usuários que desejam acessar servidores privados uma taxa mensal em Robux .

### [Taxas de catálogo e comissões](#taxas-de-catálogo-e-comissões)[](#taxas-de-catálogo-e-comissões)

Você pode criar e vender acessórios e roupas no Marketplace. Depois de pagar a taxa de upload e enviar um novo ativo para aprovação, a equipe de moderação revisa seu ativo e, se aprovado, adiciona seu ativo ao catálogo.

Você receberá uma [comissão](/docs/en-us/marketplace/marketplace-fees-and-commissions)  toda vez que os usuários comprarem seu item do catálogo. Se os usuários comprarem seu item do catálogo dentro de um jogo usando o [menu de inspeção de avatar](/docs/en-us/players/avatar-inspect-menu)  ou o [serviço de editor de avatar](/docs/en-us/players/avatar-editor) , o proprietário do jogo também recebe uma comissão.

### [Plugins e Modelos](#plugins-e-modelos)[](#plugins-e-modelos)

Um [plugin](/docs/en-us/studio/plugins)  é uma extensão que adiciona funcionalidade adicional ao Studio, e um [modelo](/docs/en-us/parts/models)  é um tipo de ativo reutilizável. Você pode oferecer ambos a outros criadores na [Loja do Criador](/docs/en-us/production/creator-store)  gratuitamente, ou pode vendê-los por Dólares Americanos  (o preço mínimo é $4.99 para plugins e $2.99 para modelos). O Roblox oferece uma participação na receita líder de mercado para essas vendas, pois apenas impostos e taxas de processamento de pagamento são deduzidos. Para mais informações sobre a venda de plugins e modelos, veja [Loja do Criador - Distribuir e vender ativos](/docs/en-us/production/creator-store#distribute-and-sell-assets) .

Há uma retenção de 30 dias para cada compra. O Roblox retém sua parte da venda por 30 dias, a partir da data da venda.

## [Diretrizes](#diretrizes)[](#diretrizes)

Ao projetar e implementar produtos de monetização em seus jogos, considere as seguintes diretrizes para garantir que seus métodos de monetização sejam adequados para todos os públicos na plataforma.

### [Apresentando produtos](#apresentando-produtos)[](#apresentando-produtos)

Para manter a segurança e a justiça, você deve apresentar produtos de monetização de uma maneira que seja transparente, honesta e amigável para o usuário. Por exemplo, se você oferecer descontos, eles devem ser genuínos  e justos :

-

Um desconto não é genuíno se um item está sempre "em promoção" pelo mesmo valor de Robux.

-

Um desconto não é justo se é oferecido apenas por um tempo muito curto, pressionando os usuários a fazer uma compra o mais rápido possível.

Os usuários nunca devem ser enganados, confundidos ou pressionados a fazer compras de maneiras que não pretendiam, e eles devem sempre ter a liberdade de fazer uma escolha clara e deliberada para obter uma assinatura ou gastar Robux em um item específico. Como orientação geral, existem algumas práticas a evitar em todos os momentos ao apresentar produtos de monetização ao seu público:

-

Não afirme que uma assinatura ou item está quase esgotado ou disponível apenas por um curto período se isso não for verdade.

-

Não use um temporizador de contagem regressiva que não seja preciso ou que reinicie automaticamente para o mesmo item.

Por exemplo, se seu jogo inclui uma "oferta do dia" que diz que está disponível apenas por 24 horas, mas depois você mostra a mesma mensagem aos usuários toda vez que eles fazem login e nunca para de estar disponível, você criou uma falsa sensação de urgência que não é amigável para o usuário.

### [Promovendo para públicos globais](#promovendo-para-públicos-globais)[](#promovendo-para-públicos-globais)

O Roblox é uma comunidade global para usuários de todas as idades, portanto, as promoções dentro de seus jogos devem ser adequadas para todos os públicos por padrão. Se certos produtos de monetização forem restritos em certas localidades, como itens aleatórios pagos, o Roblox fornece a API [PolicyService](/docs/en-us/reference/engine/classes/PolicyService)  para ajudá-lo a garantir que esses produtos sejam visíveis apenas para usuários elegíveis.

[PolicyService](/docs/en-us/reference/engine/classes/PolicyService)  retorna se um usuário é elegível para itens ou recursos específicos de acordo com sua localização, idade e plataforma. Você deve integrar essa API em seu jogo para atender às suas obrigações de conformidade, incluindo determinar se cada usuário é:

-

Elegível para comprar assinaturas ou produtos comerciais.

-

Permitido a itens aleatórios pagos, troca de itens pagos ou ver anúncios imersivos.

Se um usuário pode usar Robux ou algo mais que foi adquirido com Robux para obter uma recompensa aleatória, você é obrigado a usar [PolicyService](/docs/en-us/reference/engine/classes/PolicyService)  para bloquear esse recurso para usuários que não têm permissão para usar itens aleatórios em troca de Robux.

Como orientação geral, evite usar mensagens insistentes ou urgentes ao interagir com menores, pois uma linguagem de alta pressão pode ser esmagadora:

| ** Linguagem a evitar** | | ** Alternativas recomendadas** |
| --- | --- |
| "OBTENHA AGORA" | | "Ver Item" |
| "ÚLTIMA CHANCE, AJA AGORA" | | "Ver Preço" |
| "COMPRE ANTES QUE ACABE!" | | "Abrir Loja" |

## [Localizações adicionais para esta página](#localizações-adicionais-para-esta-página)[](#localizações-adicionais-para-esta-página)

Para versões localizadas adicionais desta página que não estão disponíveis no seletor de idiomas do site, veja os seguintes links:

-

[Búlgaro (български)](https://create.roblox.com/docs/bg-bg/production/monetization)

-

[Croata (hrvatski)](https://create.roblox.com/docs/hr-hr/production/monetization)

-

[Tcheco (čeština)](https://create.roblox.com/docs/cs-cz/production/monetization)

-

[Dinamarquês (dansk)](https://create.roblox.com/docs/da-dk/production/monetization)

-

[Holandês (Nederlands)](https://create.roblox.com/docs/nl-nl/production/monetization)

-

[Estoniano (eesti)](https://create.roblox.com/docs/et-ee/production/monetization)

-

[Finlandês (suomi)](https://create.roblox.com/docs/fi-fi/production/monetization)

-

[Grego (Ελληνικά)](https://create.roblox.com/docs/el-gr/production/monetization)

-

[Húngaro (magyar)](https://create.roblox.com/docs/hu-hu/production/monetization)

-

[Irlandês (Gaeilge)](https://create.roblox.com/docs/ga-ie/production/monetization)

-

[Letão (latviešu)](https://create.roblox.com/docs/lv-lv/production/monetization)

-

[Lituano (lietuvių)](https://create.roblox.com/docs/lt-lt/production/monetization)

-

[Maltês (Malti)](https://create.roblox.com/docs/mt-mt/production/monetization)

-

[Português - Portugal (português)](https://create.roblox.com/docs/pt-pt/production/monetization)

-

[Romeno (română)](https://create.roblox.com/docs/ro-ro/production/monetization)

-

[Eslovaco (slovenčina)](https://create.roblox.com/docs/sk-sk/production/monetization)

-

[Esloveno (slovenščina)](https://create.roblox.com/docs/sl-si/production/monetization)

-

[Sueco (svenska)](https://create.roblox.com/docs/sv-se/production/monetization)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
