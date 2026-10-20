# 🦅 SYNTRIX Manager

Bot para **gerenciamento e organização de facções no FiveM**, integrado ao Discord. O projeto reúne ferramentas para controlar membros, registrar atividades, organizar ações, acompanhar entregas e gerar relatórios em uma estrutura centralizada e configurável.

Desenvolvido em **Node.js** com **Discord.js v14**, o bot utiliza painéis interativos, formulários, botões, menus de seleção e registros em banco de dados JSON.

---

## 📌 Funcionalidades

### 👥 Sistema de registro de membros
Organiza a entrada de membros da facção pelo Discord.

- Formulário de registro com nome, passaporte, telefone e recrutador.
- Envio dos registros para um canal de aprovação.
- Aprovação ou reprovação pela staff.
- Armazenamento do status do membro.
- Aplicação automática de cargo e apelido após aprovação, conforme a configuração.
- Histórico e logs de registro.
- Identificação dos membros pelo passaporte da cidade.

### 🎯 Sistema de ações
Permite criar e acompanhar ações da facção por meio de um painel interativo.

- Criação de ações com seleção de modalidade, tipo e local.
- Categorias de locais para facilitar a seleção.
- Opções de fuga, trocação e informação sobre refém.
- Publicação separada por modalidade, de acordo com os canais configurados.
- Identificador único para cada ação.
- Registro de informações e finalização da ação.
- Registro do valor informado na finalização.
- Tratamento de finalização excepcional com justificativa, conforme as permissões configuradas.
- Histórico e logs para acompanhamento das atividades.

As modalidades disponíveis no projeto incluem **Público, Elite e P1**. Os canais e as opções podem ser alterados nos arquivos de configuração.

### 📦 Sistema de Farm
Registra as entregas realizadas pelos membros e mantém o controle dos totais.

- Registro de entregas por passaporte.
- Categorias configuráveis, incluindo dados e dinheiro sujo na configuração atual.
- Validação da quantidade mínima.
- Atualização do total acumulado por categoria.
- Histórico individual de entregas.
- Envio de logs para o canal configurado.
- Integração com os rankings.

### 💸 Sistema de lavagem
Centraliza o registro das operações de lavagem e calcula automaticamente as taxas definidas na configuração.

- Registro do valor inicial da operação.
- Seleção da modalidade de lavagem.
- Cálculo automático do percentual e do valor da taxa.
- Cálculo do valor final após a taxa.
- Identificador único para cada registro.
- Registro do responsável, data e horário.
- Status da operação: concluída, pendente ou cancelada.
- Proteção contra duplicidade da mesma interação.
- Painel de relatórios com seleção de período.
- Resumo das movimentações por período, categoria e status.
- Visualização detalhada dos registros e navegação entre páginas.
- Consulta por períodos prontos ou intervalo de datas personalizado.

As modalidades e seus percentuais ficam centralizados em `config/lavagem.js`. **Confira e ajuste esses valores antes de utilizar o bot no seu servidor.**

### 📊 Sistema de rankings
Apresenta o desempenho dos membros com base nos registros do bot.

- **Ranking geral:** combina pontuação de farm e ações.
- **Ranking de farm:** compara os totais registrados por membro.
- **Ranking de ações:** compara a quantidade de ações contabilizadas.
- Exibição dos membros aprovados.
- Ordenação automática e limite de posições configurável.
- Pontuação ajustável pela configuração.

Na configuração atual, o ranking geral utiliza os pesos definidos em `config/rankings.js`.

### 🗓️ Sistema de ausências
Facilita o registro de ausências dos membros.

- Formulário com passaporte, período e motivo.
- Envio das informações para o canal de logs.
- Registro do membro responsável pela solicitação.
- Mensagens e aparência configuráveis.

### 🛠️ Painel de administração
Reúne ferramentas administrativas para a staff.

- Busca de membros cadastrados.
- Cadastro manual de membros.
- Importação de membros pelo painel.
- Vinculação de membros.
- Consulta de estatísticas.
- Consulta de data e horário.
- Opções de redefinição dos dados usados nos rankings de farm e ações, com confirmação.

Utilize as ferramentas administrativas somente com as permissões adequadas. Confira os dados e confirme a operação antes de executar ações de redefinição.

### 🧾 Logs e histórico
Os sistemas enviam informações para canais específicos, definidos na configuração.

- Logs de registro.
- Logs de farm.
- Logs de ausência.
- Logs de lavagem.
- Canais de publicação e acompanhamento de ações.
- Histórico de operações e entregas armazenado no banco de dados.

A disponibilidade de cada log depende dos IDs e das permissões configurados no servidor.

### ⚙️ Configuração centralizada
O projeto separa as configurações da lógica dos módulos para facilitar a manutenção.

| Arquivo | Finalidade |
|---|---|
| `config/sistema.js` | Presença do bot, fuso horário e armazenamento |
| `config/canais.js` | IDs dos canais |
| `config/cargos.js` | IDs dos cargos e permissões |
| `config/limites.js` | Limites e quantidades |
| `config/aparencia.js` | Cores, embeds, painéis e emojis |
| `config/modais.js` | Campos e textos dos formulários |
| `config/mensagens.js` | Mensagens de resposta, erros e confirmações |
| `config/registro.js` | Regras do registro de membros |
| `config/farm.js` | Categorias e regras do farm |
| `config/acoes.js` | Modalidades, tipos e locais das ações |
| `config/rankings.js` | Pesos de pontuação do ranking geral |
| `config/lavagem.js` | Modalidades, taxas, status e períodos dos relatórios |
| `config/escalacao.js` | Configurações relacionadas à escalação |

---

## 🧰 Tecnologias utilizadas

- [Node.js](https://nodejs.org/)
- [Discord.js v14](https://discord.js.org/)
- [dotenv](https://www.npmjs.com/package/dotenv)
- JavaScript
- JSON para persistência local de dados
- Slash commands e componentes interativos do Discord

---

## 🚀 Instalação

### 1. Pré-requisitos

Instale uma versão compatível do Node.js. Recomenda-se uma versão LTS ainda suportada.

Você também precisa de uma aplicação e de um bot criados no [Discord Developer Portal](https://discord.com/developers/applications).

### 2. Baixe o projeto

Clone o repositório:

```bash
git clone URL_DO_SEU_REPOSITORIO
cd SYNTRIX-Manager
```

Ou baixe o projeto como ZIP e extraia os arquivos.

### 3. Instale as dependências

Na pasta do projeto, execute:

```bash
npm install
```

### 4. Configure as variáveis de ambiente

Crie um arquivo `.env` na raiz do projeto. Use o seguinte modelo:

```env
TOKEN=TOKEN_DO_SEU_BOT
CLIENT_ID=ID_DA_APLICACAO
GUILD_ID=ID_DO_SERVIDOR
```

Substitua os valores pelos dados corretos da sua aplicação e do servidor Discord.

Os IDs de canais e cargos utilizados pelos módulos também precisam ser preenchidos em `config/canais.js` e `config/cargos.js`, conforme a estrutura do projeto.

**Nunca publique o token do bot.** Não compartilhe seu `.env` e não coloque credenciais diretamente no código.

### 5. Configure canais, cargos e funcionalidades

Antes de iniciar o bot:

1. Revise `config/canais.js` e preencha os IDs dos canais.
2. Revise `config/cargos.js` e configure os cargos exigidos.
3. Confira as taxas em `config/lavagem.js`.
4. Ajuste modalidades, locais e permissões em `config/acoes.js`.
5. Revise os limites, mensagens, aparência e regras de pontuação.
6. Confira se o bot possui as permissões necessárias nos canais configurados.

Os nomes dos cargos e as permissões devem corresponder à configuração utilizada no seu servidor.

### 6. Registre os comandos

Execute:

```bash
npm run deploy
```

Esse comando registra os comandos definidos pelo projeto no servidor configurado. Confirme se as variáveis de ambiente estão preenchidas antes de executá-lo.

### 7. Inicie o bot

```bash
npm start
```

Para executar os testes incluídos no projeto:

```bash
npm test
```

---

## 🎮 Comandos de painéis

Os seguintes slash commands estão implementados para publicar os painéis correspondentes:

| Comando | Função |
|---|---|
| `/painel-registro` | Publica o painel de registro |
| `/painel-acoes` | Publica o painel de criação de ações |
| `/painel-farm` | Publica o painel de farm |
| `/painel-lavagem` | Publica o painel de lavagem e acesso aos relatórios |
| `/painel-ranking` | Publica o painel de rankings |
| `/painel-ausencia` | Publica o painel de ausências |
| `/painel-admin` | Publica o painel de administração |

O uso dos painéis depende da configuração, das permissões e dos canais do servidor.

---

## 💾 Banco de dados e backups

O projeto utiliza `database.json` para armazenar informações como membros, registros de farm, ações e operações de lavagem.

O código prevê gravação atômica do banco e snapshots automáticos na pasta `_backups`, mantendo uma quantidade limitada de cópias recentes.

**Boas práticas:**

- Faça cópias de segurança antes de alterar o projeto.
- Não edite o banco enquanto o bot estiver gravando dados.
- Restrinja o acesso ao banco, pois ele pode conter informações dos membros.
- Teste restaurações de backup antes de depender delas.
- Não publique bancos de produção ou backups com dados privados.

---

## 🔐 Segurança antes de publicar no GitHub

Antes de tornar o repositório público:

- Remova `.env` do controle de versão.
- Não envie tokens, senhas ou credenciais.
- Não publique `database.json` de produção nem backups com dados reais.
- Confira o histórico do Git para garantir que segredos antigos não tenham sido enviados.
- Caso um token já tenha sido publicado, redefina-o no Discord Developer Portal.
- Utilize permissões mínimas necessárias para o bot.

O `.gitignore` deve incluir, no mínimo, entradas como:

```gitignore
node_modules/
.env
database.json
database.json.tmp
_backups/
```

Se algum desses arquivos já estiver sendo rastreado pelo Git, adicioná-lo ao `.gitignore` não o remove automaticamente do histórico. Remova-o do controle de versão e trate qualquer credencial exposta como comprometida.

---

## 📁 Estrutura do projeto

```text
SYNTRIX-Manager/
├── config/
│   ├── acoes.js
│   ├── aparencia.js
│   ├── canais.js
│   ├── cargos.js
│   ├── escalacao.js
│   ├── farm.js
│   ├── index.js
│   ├── lavagem.js
│   ├── limites.js
│   ├── mensagens.js
│   ├── modais.js
│   ├── rankings.js
│   ├── registro.js
│   └── sistema.js
├── modules/
│   ├── acoes.js
│   ├── admin.js
│   ├── ausencia.js
│   ├── farm.js
│   ├── lavagem.js
│   ├── ranking.js
│   └── registro.js
├── testes/
├── utils/
│   └── helpers.js
├── database.js
├── deploy-commands.js
├── index.js
├── package.json
└── README.md
```

A estrutura acima resume os principais arquivos do projeto. Arquivos locais, como `.env`, `database.json` e `_backups`, podem existir durante a execução e devem ser tratados com cuidado.

---

## 🧪 Testes

O projeto inclui verificações para configuração e roteamento de interações. Execute:

```bash
npm test
```

Se houver falhas, confira as mensagens exibidas no terminal, as dependências instaladas e os arquivos de configuração.

---

## 📌 Observações

- Este projeto é voltado à organização de comunidades e facções de roleplay no FiveM por meio do Discord.
- Os recursos dependem das permissões do bot, dos IDs configurados e da estrutura do servidor.
- O armazenamento JSON é local; para ambientes com alta concorrência ou grande volume de dados, avalie futuramente um banco de dados dedicado.
- Revise todas as configurações antes de utilizar o bot em produção.

---

## 👨‍💻 Desenvolvimento

Projeto desenvolvido em JavaScript com foco em organização, automação de tarefas e gerenciamento de atividades de facções no Discord.

**SYNTRIX Manager — organização, controle e acompanhamento em um só lugar.**
