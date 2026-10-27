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

## Limites do plano gratuito do Firebase

- 50 mil leituras e 20 mil gravações por dia, 1 GB de dados.
- Com cerca de 1000 clientes, cada vez que o sistema é aberto num aparelho novo ele lê todos os clientes. O sistema guarda os dados no aparelho para economizar leituras, então o uso diário normal cabe no plano gratuito.
- Se um dia passar do limite, o sistema para de salvar até o dia seguinte. Nada é cobrado sem você cadastrar um cartão.

## Arquivos

- `index.html`: o sistema inteiro.
- `pedido.html`: página onde o cliente faz o pedido.
- `firestore.rules`: regras de segurança do banco (quem pode ler e gravar).
- `manifest.json`, `icon-192.png`, `icon-512.png`: ícone e nome para a tela inicial do celular.
