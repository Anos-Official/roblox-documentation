<!-- Source: https://create.roblox.com/docs/pt-pt/cloud-services/extended-services -->

Serviços Estendidos | Documentation - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Cloud services](/docs/en-us/cloud-services/data-stores-vs-memory-stores)

# Serviços Estendidos

English

* This content is translated using AI (Beta) and may contain errors. To view this page in English, click [here] .

Os Serviços Estendidos são uma solução que permite gerenciar o uso e o pagamento de serviços além dos limites padrão do Roblox. Inclui armazenamento de dados, armazenamento em memória, conversão de texto em fala, conversão de fala em texto e computação.

## [Requisitos de elegibilidade](#requisitos-de-elegibilidade)[](#requisitos-de-elegibilidade)

Para usar os Serviços Estendidos, sua conta Roblox deve:

-

Ser [verificada por ID](/docs/en-us/production/publishing/account-verification#verify-through-government-id)  e ter 18 anos ou mais.

-

Estar localizada em um [país suportado](#pa%C3%ADses-suportados) .

-

Ter um endereço de e-mail válido associado a ela.

-

Não estar atualmente banida ou moderada.

-

Aceitar e cumprir os [termos de serviço](https://en.help.roblox.com/hc/articles/37967848292500) .

Para contas de grupo, apenas o proprietário do grupo precisa atender aos requisitos de elegibilidade.

## [Desbloquear Serviços Estendidos](#desbloquear-serviços-estendidos)[](#desbloquear-serviços-estendidos)

Se você atender a todos os [requisitos de elegibilidade](#requisitos-de-elegibilidade) , pode finalizar a configuração dos Serviços Estendidos inserindo os detalhes da sua conta e informações de pagamento. Para jogos de propriedade de grupos, apenas o proprietário do grupo pode desbloquear os Serviços Estendidos e integrar o jogo a eles.

Para desbloquear e usar os Serviços Estendidos:

1.

No [Painel do Criador](https://create.roblox.com/dashboard/creations) , vá para Criações  e selecione um jogo.

2.

Vá para Serviços Estendidos .

3.

Se você ainda não inseriu os detalhes da sua conta e informações de pagamento, clique em Adicionar informações faltantes  na barra superior.

1.

Insira suas informações da conta. Os campos Tipo de conta , Tipo de ID fiscal  e ID fiscal  são opcionais.

-

Você também pode ir para Finanças  ⟩ Informações da Conta  na seção Serviços Estendidos  para gerenciar suas informações da conta. Você não precisa atualizar mais nada nesta página.

2.

Clique em Próximo .

3.

Insira um método de pagamento. Você pode inserir um novo método de pagamento ou selecionar entre as opções de pagamento disponíveis já associadas à sua conta Roblox.

-

Você também pode ir para Finanças  ⟩ Pagamentos  para adicionar novos métodos de pagamento, ou ir para Finanças  ⟩ Cobrança  para definir um novo método de pagamento padrão.

4.

Clique em Salvar .

##### Status da conta

Sua conta de Serviços Estendidos pode estar em um dos seguintes status:

| Status | | Descrição | | Ação necessária |
| Normal | | Você pode usar todos os recursos dos Serviços Estendidos. | | Nenhuma ação é necessária. |
| --- | --- |
| Vencido | | Sua conta está vencida porque seu método de pagamento automático falhou. O Roblox oferece um período de carência de sete dias  antes de suspender sua conta de Serviços Estendidos. | | Altere seu método de pagamento e tente um pagamento manual, ou aguarde até que o Roblox tente cobrar seu método de pagamento novamente após o término do período de carência. |
| Suspensa | | Você não pode usar nenhum serviço pago dos Serviços Estendidos. No entanto, você ainda pode usar serviços com limites padrão. | | Corrija seus requisitos de elegibilidade, adicione um método de pagamento válido ou pague manualmente o saldo vencido em sua conta. |

## [Habilitar um serviço](#habilitar-um-serviço)[](#habilitar-um-serviço)

Para habilitar um serviço:

1.

Vá para Serviços Estendidos .

2.

Ative o serviço que você deseja habilitar.

3.

Insira um orçamento mensal para cada recurso aplicável sob o serviço. O orçamento mensal mínimo que você pode definir é de $0,50 USD.

Seu método de pagamento é cobrado no final do mês, quando uma fatura é gerada, ou quando seu uso atinge $10 USD, o que ocorrer primeiro.

Você pode aumentar ou diminuir o orçamento mensal de um serviço a qualquer momento. Seu serviço é automaticamente limitado se você diminuir seu orçamento para um valor abaixo do seu uso atual até a data, ou se você exceder o orçamento que definiu.

O Roblox notifica você por e-mail quando seu uso atinge 80% do seu orçamento e novamente quando atinge 100%.

### [Serviços Estendidos para Computação](#serviços-estendidos-para-computação)[](#serviços-estendidos-para-computação)

Cada servidor de jogo recebe uma quantidade padrão de CPU, que aumenta com cada jogador que se junta. Serviços Estendidos para Computação  mais do que dobra a CPU por jogador que os servidores do seu jogo recebem.

A grande maioria dos jogos no Roblox não vê benefícios deste serviço, mas jogos com física pesada do lado do servidor ou que fazem uso extensivo da [autoridade do servidor](/docs/en-us/projects/server-authority)  atingem limites existentes. Para ver se seu jogo pode se beneficiar dos Serviços Estendidos para Computação :

-

Verifique o [batimento cardíaco do servidor](/docs/en-us/performance-optimization/identify#server-compute)  para quedas persistentes abaixo de 60 FPS.

-

Examine a utilização do núcleo da CPU no [Painel de Desempenho](/docs/en-us/production/analytics/performance#server-charts) .

Antes de pagar por mais CPU, tente [reduzir o trabalho que seus servidores fazem](/docs/en-us/performance-optimization/improve) .

## [Gerenciar cobrança](#gerenciar-cobrança)[](#gerenciar-cobrança)

Para acessar o painel de cobrança dos Serviços Estendidos:

1.

Vá para Finanças  ⟩ Cobrança .

2.

Selecione a aba Serviços em Nuvem  para exibir o seguinte:

-

Seu saldo pendente, incluindo o custo até a data do mês

-

Seu histórico de cobrança, incluindo toda a atividade de cobrança dos Serviços Estendidos em seus jogos

Para uma análise detalhada dos custos do seu saldo pendente atual, clique em Ver Detalhes  ao lado do seu método de pagamento. Para uma fatura detalhada de uma fatura anterior, clique em Ver Fatura  em Histórico de Cobrança .

## [Preços dos serviços](#preços-dos-serviços)[](#preços-dos-serviços)

Veja a tabela a seguir para os preços dos Serviços Estendidos:

| Serviço | |  | | Padrão | | Estendido |
| [Armazenamentos em memória](https://create.roblox.com/docs/cloud-services/memory-stores) | | Solicitações | | 1000 + (CCU × 120) solicitações por minuto | | $0.003 / 1M solicitações |
|  | | Armazenamento | | 64 KB + (CCU × 1.2 KB) | | $0.10 / GB por hora¹ |
| [Texto para fala](https://create.roblox.com/docs/audio/objects#text-to-speech) | | Solicitações | | 1 + (CCU × 6) solicitações por minuto | | $5.00 / 1M solicitações |
| [Fala para texto](https://create.roblox.com/docs/audio/objects#speech-to-text) | | Solicitações | | 1 + (CCU × 5) solicitações por minuto | | $1 / 1M solicitações |
| [Armazenamentos de dados padrão](https://create.roblox.com/docs/cloud-services/data-stores) | | Obter | | 250 + (CCU * 40) solicitações por minuto | | $0.08 / 1M solicitações |
|  | | Definir | | 250 + (CCU * 20) solicitações por minuto | | $0.80 / 1M solicitações |
|  | | Listar | | 10 + (CCU * 2) solicitações por minuto | | $0.60 / 1M solicitações |
|  | | Remover | | 100 + (CCU * 40) solicitações por minuto | | $0.80 / 1M solicitações |
| [Armazenamentos de dados ordenados](https://create.roblox.com/docs/cloud-services/data-stores) | | Obter | | 250 + (CCU * 40) solicitações por minuto | | $0.08 / 1M solicitações |
|  | | Definir | | 250 + (CCU * 20) solicitações por minuto | | $0.25 / 1M solicitações |
|  | | ObterOrdenado | | 100 + (CCU * 2) solicitações por minuto | | $0.32 / 1M solicitações |
|  | | Remover | | 100 + (CCU * 40) solicitações por minuto | | $0.25 / 1M solicitações |
| [Armazenamento de dados ](https://create.roblox.com/docs/cloud-services/data-stores) | | Armazenamento | | 100 MB + (1 MB * Jogadores ao longo da vida) GB por mês | | $0.12 / GB por mês |
| [Computação ](https://create.roblox.com/docs/production/analytics/performance) | | Núcleos de CPU | | Primeiras 100K horas de jogo por mês sem custo (quando inscrito nos Serviços Estendidos para Computação) | | $0.001 / hora de jogo² |

 ¹ GB por hora = o consumo de armazenamento multiplicado pelo tempo. Por exemplo, 100 GB horas podem equivaler a "100 GB × 1 hora" ou "200 GB × 0.5 horas".  ² Os Serviços Estendidos para Computação são cobrados com base em quanto tempo o recurso permanece habilitado, medido em minutos de jogo. Como habilitar o recurso reserva capacidade de computação adicional para seu jogo, as cobranças se aplicam sempre que o recurso está ativo, mesmo que a computação adicional não seja totalmente consumida. As horas de jogo são calculadas como a soma de todas as durações das sessões dos jogadores. Por exemplo, se 10.000 usuários jogam por 1 hora cada, isso equivale a 10.000 horas de jogo, resultando em $10 em cobranças além da cota mensal incluída de 100.000 horas de jogo. Esses limites e preços se aplicam apenas a jogos inscritos nos Serviços Estendidos para Computação. Jogos que não se inscrevem continuam a receber horas de jogo ilimitadas sob os limites padrão atuais sem custo adicional.

## [Países suportados](#países-suportados)[](#países-suportados)

Os Serviços Estendidos estão disponíveis nos seguintes países:

| País |
| Austrália | | Alemanha | | Polônia |
| Áustria | | Hong Kong | | Portugal |
| Bélgica | | Hungria | | Romênia |
| Brasil | | Irlanda | | Cingapura |
| Bulgária | | Itália | | Eslováquia |
| Canadá | | Cazaquistão | | Eslovênia |
| Chile | | Letônia | | África do Sul |
| Croácia | | Lituânia | | Coreia do Sul |
| Chipre | | Malásia | | Espanha |
| República Checa | | Malta | | Suécia |
| Dinamarca | | México | | Suíça |
| Estônia | | Países Baixos | | Tailândia |
| Finlândia | | Nova Zelândia | | Reino Unido |
| França | | Noruega | | Estados Unidos |
| Geórgia | | Peru | |  |

## [Localizações adicionais para esta página](#localizações-adicionais-para-esta-página)[](#localizações-adicionais-para-esta-página)

Para versões localizadas adicionais desta página que não estão disponíveis no seletor de idiomas do site, veja os seguintes links:

-

[Búlgaro (български)](https://create.roblox.com/docs/bg-bg/cloud-services/extended-services)

-

[Croata (hrvatski)](https://create.roblox.com/docs/hr-hr/cloud-services/extended-services)

-

[Checo (čeština)](https://create.roblox.com/docs/cs-cz/cloud-services/extended-services)

-

[Dinamarquês (dansk)](https://create.roblox.com/docs/da-dk/cloud-services/extended-services)

-

[Holandês (Nederlands)](https://create.roblox.com/docs/nl-nl/cloud-services/extended-services)

-

[Estoniano (eesti)](https://create.roblox.com/docs/et-ee/cloud-services/extended-services)

-

[Finlandês (suomi)](https://create.roblox.com/docs/fi-fi/cloud-services/extended-services)

-

[Grego (Ελληνικά)](https://create.roblox.com/docs/el-gr/cloud-services/extended-services)

-

[Húngaro (magyar)](https://create.roblox.com/docs/hu-hu/cloud-services/extended-services)

-

[Irlandês (Gaeilge)](https://create.roblox.com/docs/ga-ie/cloud-services/extended-services)

-

[Letão (latviešu)](https://create.roblox.com/docs/lv-lv/cloud-services/extended-services)

-

[Lituano (lietuvių)](https://create.roblox.com/docs/lt-lt/cloud-services/extended-services)

-

[Maltês (Malti)](https://create.roblox.com/docs/mt-mt/cloud-services/extended-services)

-

[Português - Portugal (português)](https://create.roblox.com/docs/pt-pt/cloud-services/extended-services)

-

[Romeno (română)](https://create.roblox.com/docs/ro-ro/cloud-services/extended-services)

-

[Eslovaco (slovenčina)](https://create.roblox.com/docs/sk-sk/cloud-services/extended-services)

-

[Esloveno (slovenščina)](https://create.roblox.com/docs/sl-si/cloud-services/extended-services)

-

[Sueco (svenska)](https://create.roblox.com/docs/sv-se/cloud-services/extended-services)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
