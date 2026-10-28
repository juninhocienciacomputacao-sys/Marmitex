# Marmitex Gestão

Sistema de gestão do restaurante de marmitas: clientes, planos, cardápio do dia, calendário, confirmações, entregas e rotas, relatórios, financeiro e marketing.

Funciona no celular e no computador. Os dados ficam no Firebase (Google), no plano gratuito.

## 1. Criar o Firebase (uma vez, uns 10 minutos)

1. Entre em <https://console.firebase.google.com> com sua conta Google e toque em **Criar um projeto**. Dê o nome `marmitex`. Pode desativar o Google Analytics.
2. **Login:** no menu, abra **Criação > Authentication > Vamos começar**. Em **Método de login**, escolha **E-mail/senha**, ative a primeira opção e salve.
3. **Banco de dados:** abra **Criação > Firestore Database > Criar banco de dados**. Local: `southamerica-east1 (São Paulo)`. Escolha **Iniciar no modo de produção**.
4. **Regras:** ainda no Firestore, abra a aba **Regras**, apague tudo e cole o conteúdo do arquivo [`firestore.rules`](firestore.rules). Troque `SEU-EMAIL-AQUI` pelo seu e-mail (para mais pessoas: `['voce@gmail.com', 'funcionario@gmail.com']`). Toque em **Publicar**.
5. **Configuração:** toque na engrenagem ao lado de **Visão geral do projeto > Configurações do projeto**. Em **Seus apps**, toque no ícone **`</>`** (Web), dê o apelido `marmitex` e toque em **Registrar app**. Copie o bloco `firebaseConfig` que aparece.

## 2. Abrir o sistema

1. Abra o endereço do sistema: <https://juninhocienciacomputacao-sys.github.io/Marmitex/>
2. A configuração do Firebase já está gravada no `index.html`, então não precisa colar nada.
3. Digite seu e-mail e uma senha (6 caracteres ou mais) e toque em **Criar acesso**. Das próximas vezes, use **Entrar**.
4. **Celular:** no menu do navegador, toque em **Adicionar à tela inicial**. O sistema vira um ícone como um aplicativo.

## 3. Ativar o endereço no GitHub (uma vez)

No repositório, abra **Settings > Pages**. Em **Branch**, escolha `main` e a pasta `/ (root)` e toque em **Save**. Em 1 ou 2 minutos o endereço acima fica no ar.

## Usuários do sistema

O administrador é o e-mail escrito no arquivo de regras (`SEU-EMAIL-AQUI`). Os outros usuários são cadastrados dentro do sistema, em **Ajustes > Usuários do sistema**: nome, e-mail e uma senha inicial. Para tirar o acesso de alguém, toque em **Remover**.

## Pedidos pelo link

A mensagem do cardápio (botão **Copiar mensagem** na aba Dia) já leva o link `pedido.html`. O cliente toca, digita o WhatsApp, escolhe a quantidade e confirma. O pedido entra sozinho na aba Dia.

- Clientes de plano entram sozinhos nos dias abertos em que recebem. Quem ainda não confirmou aparece no alerta **Plano sem confirmação**, com botão para lembrar no WhatsApp.
- Pedido de telefone não cadastrado aparece num aviso com o botão **Cadastrar**.
- Para desligar a confirmação automática de plano: **Ajustes**.

## Cardápio pronto

Na aba **Cardápio**, escolha um dos cardápios fit prontos ou toque em **Sugerir sem repetir** (o sistema evita repetir a proteína da semana). Ao digitar um prato aparecem sugestões da biblioteca fit e dos pratos que você já usou. **Planejar a semana** cria de uma vez os cardápios dos dias abertos dos próximos 7 dias; depois é só ajustar conforme os ingredientes.

## Preços e promoções

Na aba **Preços** você cadastra os tamanhos de marmita, adicionais, bebidas e a taxa de entrega (há uma tabela fit de exemplo para carregar e ajustar). As promoções têm período e dias da semana; as que valem no dia entram sozinhas na mensagem do cardápio. **Copiar tabela para o WhatsApp** junta preços, planos, congeladas e promoções numa mensagem.

## Endereço automático no pedido

Quando o cliente digita o WhatsApp na página de pedido e já tem endereço cadastrado, aparece marcado **Entregar no meu endereço cadastrado** e ele não precisa digitar nada. Se desmarcar, informa outro endereço só para aquele pedido, que vai na rota do dia. Cliente sem endereço precisa informar, e o sistema já guarda no cadastro dele. A página não mostra dados do cliente: o sistema publica só um código do telefone.

## Atendimento automático (WhatsApp Business)

A página `atendimento.html` é o "balcão" do restaurante: o cliente escolhe **Pedir marmita** (vai para o próximo cardápio aberto), **Assinar um plano** (o sistema cadastra o cliente, ativa o plano e mostra o Pix), **Congeladas**, **Preços** ou **Falar com a gente**.

Em **Marketing > Atendimento automático** estão o link e os textos prontos para a **Mensagem de saudação**, a **Mensagem de ausência** e as **Respostas rápidas** do WhatsApp Business, com o passo a passo para ligar. As novas assinaturas aparecem no Dia com o botão de boas-vindas.

## Pedido pelo link, do jeito profissional

- **Prazo:** em Ajustes escolha se os pedidos fecham no próprio dia ou no dia anterior (ex.: até 14:00 do dia anterior). Os pedidos de um dia só abrem quando o cardápio dele é salvo.
- **Entrega:** o cliente escolhe Casa, Apartamento (pode deixar na portaria) ou Apartamento (só em mãos). Aparece na lista, nas rotas e no cadastro.
- **Pix:** com a chave Pix em Ajustes, o cliente avulso vê o valor, o Pix copia e cola e o QR Code assim que confirma, e pode tocar em "Já paguei". Cliente de plano não vê cobrança.
- **Cliente novo:** quem pede pelo link e não está na base é cadastrado sozinho (dá para desligar em Ajustes).
- **Fechar os pedidos:** no Dia, passo 4, **Fechar pedidos do dia** trava o link e abre a lista para avisar cada cliente pelo WhatsApp com a confirmação, o total e o Pix.

## Logo e imagem do cardápio

Em **Ajustes > Logo e cor da marca**, carregue a logo (PNG ou JPG) e escolha a cor. A logo aparece no menu, na tela de entrada, na página de pedido dos clientes e no ícone da aba. No **Cardápio**, o botão **Imagem com a logo** gera uma imagem pronta (1080 × 1350) com pratos, preços e promoções: no celular abre direto o compartilhamento para o WhatsApp; no computador baixa o arquivo.

## Congeladas

Na aba **Congeladas** você cadastra os pacotes (ex.: Kit 10 congeladas fit), lança as encomendas de cada cliente com o dia da entrega e controla o estoque.

- A encomenda entra sozinha na rota do entregador no dia da entrega, junto com a marmita do cliente quando ele também pediu.
- **Receber** lança o valor no Financeiro. **Entregar** tira as unidades do estoque.
- **Copiar oferta** monta a mensagem com os pacotes e preços para o WhatsApp.

## Conservação das congeladas e etiquetas

Em **Congeladas > Recomendações ao cliente** fica um texto pronto (freezer a -18 °C, validade, descongelar na geladeira, consumir em até 24 h depois de descongelada, nunca recongelar, como aquecer). Dá para editar e mudar a validade. O texto aparece na página de atendimento (`atendimento.html#cuidados`), no link de pedido e na mensagem de confirmação de quem recebe congeladas. O botão **Imprimir etiquetas** gera folha A4 com 24 etiquetas: prato, data de produção, validade e modo de preparo.

## Pagamento

Preencha em **Ajustes** a chave Pix (o sistema já arruma o formato: telefone vira +55, CPF/CNPJ só números) e marque as formas de pagamento aceitas. Com a chave, o cliente avulso recebe o Pix copia e cola e o QR Code na hora do pedido. Sem a chave, a página mostra o valor, as formas aceitas e um botão para combinar no WhatsApp. Enquanto faltar nome, Pix ou WhatsApp do restaurante, a tela **Dia** avisa.

## Segurança e desempenho (auditoria de 28/10/2026)

- Regras testadas no emulador do Firebase (30 testes): quem não está logado só lê cardápio e dados públicos, só envia o próprio pedido ou assinatura, e não lê nem lista clientes, pedidos, financeiro ou respostas. E-mail logado que não está cadastrado não acessa nada.
- Pedido pelo link só é aceito para dia com cardápio publicado e não fechado (o Firebase barra, não só a página).
- Muitos pedidos de uma vez (ex.: 1000 pela manhã) e clientes de plano entram em uma gravação só por dia, sem travar. Testado com 2000 clientes.
- Se uma tela der erro, aparece um aviso com botão de recarregar, sem perder dados.

## Feriados

Os feriados nacionais aparecem no Calendário e ficam fechados (os atalhos "Abrir seg a sex/sáb" pulam os feriados). Para abrir num feriado, toque no dia. Os feriados da sua cidade você cadastra em **Ajustes**.

## Backup (faça toda semana)

Em **Ajustes > Backup**, toque em **Baixar backup agora**. O sistema baixa um arquivo `backup-marmitex-DATA.json` com tudo: clientes, planos, cardápios, pedidos, financeiro e configurações. Guarde no computador e no Google Drive.

- A tela **Dia** avisa quando o último backup tem mais de 7 dias.
- Para voltar um backup, abra **Restaurar de um arquivo de backup**, escolha o arquivo e toque duas vezes em **Restaurar**. O que está no arquivo volta como era; o resto não é apagado.

## Limites do plano gratuito do Firebase

- 50 mil leituras e 20 mil gravações por dia, 1 GB de dados.
- Com cerca de 1000 clientes, cada vez que o sistema é aberto num aparelho novo ele lê todos os clientes. O sistema guarda os dados no aparelho para economizar leituras, então o uso diário normal cabe no plano gratuito.
- Os pedidos feitos pelo link são apagados do banco assim que entram na lista do dia, e as telas só carregam os últimos 75 dias de pedidos e 100 dias de financeiro. Isso economiza leituras.
- Se um dia passar do limite, o sistema para de salvar até o dia seguinte. Nada é cobrado sem você cadastrar um cartão.

## Arquivos

- `index.html`: o sistema inteiro.
- `pedido.html`: página onde o cliente faz o pedido.
- `firestore.rules`: regras de segurança do banco (quem pode ler e gravar).
- `manifest.json`, `icon-192.png`, `icon-512.png`: ícone e nome para a tela inicial do celular.
