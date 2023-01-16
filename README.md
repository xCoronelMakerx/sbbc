> :warning: **There are risks when using any kind of unofficial software**: Be very careful! If you lose your account, it is entirely your responsibility.

# Bombcrypto-superbot

Este bot é um produto da engenharia reversa do jogo Bombcrypto. Ele simula o jogo e envia mensagens usando `websocket`. Como não requer um navegador para funcionar, o uso principal é para **várias contas**. Divirta-se!

moderado por Lucas Vieceli

se você não tiver um computador disponível para executar o bot, poderá usar o serviço gratuitamente via telegram. https://t.me/bombcryptoFreeBot

telegram do grupo https://t.me/+tQcb45U9MwAxYWMx

## Funcionalidades

-   Farm Treasure Hunt
-   Lida com o recurso Home se uma casa estiver disponível

# Início do zero

## Contratando servidor dedicado

Caso você não tenha um servidor para colocar seu bot, você pode contratar um servidor em [Linode](https://linode.gvw92c.net/do1vYM), custa 5 dolares mensais e deve aguentar 10 contas

Para aceessar o servidor do Linode, você pode utilizar o programa "Termius" [(Download Windows)](https://termius.com/windows) [(Download Linux)](https://termius.com/linux), ele existe para computador, android e ios

Veja o vídeo de como contratar o serviço e acessar a máquina

[![Video](https://i3.ytimg.com/vi/o4IH5C2YMtk/maxresdefault.jpg)](https://www.youtube.com/watch?v=o4IH5C2YMtk)
video: https://www.youtube.com/watch?v=o4IH5C2YMtk

## Configurando a máquina

[![Video](https://i3.ytimg.com/vi/rHMMF6KJ-Uk/maxresdefault.jpg)](https://youtu.be/rHMMF6KJ-Uk)
video: https://youtu.be/rHMMF6KJ-Uk

Para utilizar o bot, você precisa ter o Nodejs, npm, yarn e pm2 instalado. Execute o seguinte comando que irá instalar tudo automaticamente:

```
cd ~
curl -sL https://raw.githubusercontent.com/lucasvieceli/bombcrypto-superbot/master/vm.sh -o vm.sh
bash vm.sh
```

## Configurações iniciais do bot

Esta no video a cima

Execute o seguinte comando que irá baixar todo o projeto e instalar as dependências para você:

```
cd ~
curl -sL https://raw.githubusercontent.com/lucasvieceli/bombcrypto-superbot/master/init.sh -o init.sh
bash init.sh
cd bombcrypto-superbot
```

Para configura suas contas você precisará editar um arquivo "src/ecosystem.config.js",

```
nano src/ecosystem.config.js
```

Você verá algo como isso aqui:

```
module.exports = {
    apps: [
        {
            name: "client1", //Um nome para identificação
            instances: "1",
            exec_mode: "fork",
            script: "npm run start:bot",
            env: {//aqui você irá colocar as configurações
                DEBUG_LEVEL: "info",
                MIN_HERO_ENERGY_PERCENTAGE: "50",
                LOGIN: "user:CHANGE:CHANGE",
                TELEGRAM_KEY: "CHANGE",
                NETWORK: "POLYGON",
                ALERT_SHIELD: 50,
                NUM_HERO_WORK: 5,
                TELEGRAM_CHAT_ID: "CHANGE",
                SERVER: "sea"
            },
        },
    ],
};

```

Caso você queira colocar mais de uma conta, basta colocar mais um item, ficando assim:

```
module.exports = {
    apps: [
        {
            name: "client1", //Um nome para identificação
            instances: "1",
            exec_mode: "fork",
            script: "npm run start:bot",
            env: {//aqui você irá colocar as configurações
                DEBUG_LEVEL: "info",
                MIN_HERO_ENERGY_PERCENTAGE: "50",
                LOGIN: "user:CHANGE:CHANGE",
                TELEGRAM_KEY: "CHANGE",
                NETWORK: "POLYGON",
                ALERT_SHIELD: 50,
                NUM_HERO_WORK: 5,
                TELEGRAM_CHAT_ID: "CHANGE",
                SERVER: "sea"
            },
        },
        {
            name: "client2", //Um nome para identificação
            instances: "1",
            exec_mode: "fork",
            script: "npm run start:bot",
            env: {//aqui você irá colocar as configurações
                DEBUG_LEVEL: "info",
                MIN_HERO_ENERGY_PERCENTAGE: "50",
                LOGIN: "user:CHANGE:CHANGE",
                TELEGRAM_KEY: "CHANGE",
                NETWORK: "POLYGON",
                ALERT_SHIELD: 50,
                NUM_HERO_WORK: 5,
                TELEGRAM_CHAT_ID: "CHANGE",
                SERVER: "sea"
            },
        },
    ],
};

```

[Aqui você ve as variaveis que existe](https://github.com/lucasvieceli/bombcrypto-superbot/#vari%C3%A1veis)

Salve o arquivo (CTRL + X) ele vai pergunte se você confirma, digite Y e ENTER

## Criando bot no telegram

[![Video](https://i3.ytimg.com/vi/_FKLOTkRizA/maxresdefault.jpg)](https://youtu.be/_FKLOTkRizA)
video: https://youtu.be/_FKLOTkRizA

Para você conseguir ter a TELEGRAM_KEY, vá ate seu telegram e pesquise por "botfather" e inicie uma conversa.

Digite:

```
/newbot
```

Ele vai te perguntar qual nome você gostaria do bot. Depois de informar o nome, ele vai te retornar uma mensagem parecida com essa:

```
Done! Congratulations on your new bot. You will find it at t.me/testeeee. You can now add a description, about section and profile picture for your bot, see /help for a list of commands. By the way, when you've finished creating your cool bot, ping our Bot Support if you want a better username for it. Just make sure the bot is fully operational before you do this.

Use this token to access the HTTP API:
5966491474:AAHy6SQXGYJQqiuQ9zdqW3rI3g-123123
Keep your token secure and store it safely, it can be used by anyone to control your bot.

For a description of the Bot API, see this page: https://core.telegram.org/bots/api
```

a onde está "Use this token to access the HTTP API:" é sua chave TELEGRAM_KEY, exemplo "5966491474:AAHy6SQXGYJQqiuQ9zdqW3rI3g-123123"

Então coloque essa chave no arquivo de configuração do bot "src/ecosystem.config.js". LEMBRANDO QUE CADA CONTA, PRECISA TER UMA CHAVE DIFERENTE

## Recuperando TELEGRAM_CHAT_ID

[![Video](https://i3.ytimg.com/vi/nSXbi9ihScI/maxresdefault.jpg)](https://youtu.be/nSXbi9ihScI)
video: https://youtu.be/nSXbi9ihScI

Para você ter o seu chat id, você precisa entrar nessa conversa: https://t.me/RawDataBot, e clicar em iniciar, ele irá te responder algo do tipo:

```
{
    "update_id": 823632503,
    "message": {
        "message_id": 1752228,
        "from": {
            "id": 123123123,
            "is_bot": false,
            "first_name": "NOME",
            "last_name": "NOME",
            "username": "NOME",
            "language_code": "pt-br"
        },
        "chat": {
            "id": 1291257220,
            "first_name": "NOME",
            "last_name": "NOME",
            "username": "NOME",
            "type": "private"
        },
        "date": 1670437683,
        "text": "/start",
        "entities": [
            {
                "offset": 0,
                "length": 6,
                "type": "bot_command"
            }
        ]
    }
```

Em "chat" está seu id, no meu caso foi "1291257220", então coloque esse id no arquivo "src/ecosystem.config.js", pode ser utilizado o mesmo id para todas as contas

## Executando o bot

[![Video](https://i3.ytimg.com/vi/N9_Z1qIYiKs/maxresdefault.jpg)](https://youtu.be/N9_Z1qIYiKs)
video: https://youtu.be/N9_Z1qIYiKs

Comando para da start em todas as contas ou quando precisa atualizar o código font

```
 yarn start
```

Comando para parar uma conta

```
pm2 stop NOMEDOBOT
```

Comando para start em uma conta

```
pm2 start NOMEBOT
```

Comando para deletar um bot, você precisa tambem remover do arquivo de configuração

```
pm2 delete bot
```

LEMBRANDO QUE VOCÊ PODE ACESSAR A MAQUINA VIRTUAL VIA APP Termius NO SEU CELULAR

## Variáveis

As variáveis são:

| Nome da variável           | Obrigatório | Descrição                                                                                                                                                                                               | Exemplo                                               |
| -------------------------- | ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------- |
| LOGIN                      | Sim         | dados usário para login, se for login com usuário e senha, deve ser utilizado "user:", se for com a wallet "wallet:"                                                                                    | user:NOMEUSUARIO:SENHA ou wallet:WALLETID:PRIVATE_KEY |
| TELEGRAM_KEY               | Não         | Chave do bot telegram, para você conseguir acionar comandos via telegram bot                                                                                                                            |                                                       |
| NETWORK                    | Não         | A rede que será conectada, valores são BSC ou POLYGON, o padrão é BSC                                                                                                                                   | POLYGON                                               |
| MIN_HERO_ENERGY_PERCENTAGE | Não         | A porcentagem que o hero irá começar a trabalhar, você deve informar sem o símbulo %,o padrão é 50%                                                                                                     | 50                                                    |
| HOUSE_HEROES               | Não         | Caso você tenha casa, você pode informar quais heros terão preferencia na casa, o valor deve ser separado com :                                                                                         | 312312312:12323123:2323232                            |
| ALERT_SHIELD               | Não         | Caso você tenha informado TELEGRAM_KEY e TELEGRAM_CHAT_ID, você pode ser notificado quando o shield do hero estiver acabando, aqui você informa quanto de shield vc quer que seja notificado            | 100                                                   |
| NUM_HERO_WORK              | Não         | A quantidade de heroes que irão trabalhar ao mesmo tempo o padrão é 15                                                                                                                                  | 5                                                     |
| SERVER                     | Não         | o servidor que será conectado valores existentes, "na", "sea", "sa", valor padrão se não for informado sea                                                                                              | sea                                                   |
| TELEGRAM_CHAT_ID_CHECK     | Não         | Caso seja informado com o valor 1 e tamém seja informado o telegram chat id, a pessoa que náo é dona do telegram bot, não irá conseguir acionar os comandos do telegram                                 | 1                                                     |
| REPORT_REWARDS             | Não         | caso seja informado, e também seja informado TELEGRAM_CHAT_ID, o bot irá enviar os rewards automaticamente para o chat, o valor é em minutos, exemplo 30 é 30 minutos, 120, é duas horas                | 30                                                    |
| TELEGRAM_CHAT_ID           | Não         | chat id do telegram para funcionar as notificações                                                                                                                                                      |                                                       |
| MAX_GAS_REPAIR_SHIELD      | Não         | Valor máximo que pode ser gasto para reparar o shield                                                                                                                                                   | 0.004                                                 |
| ALERT_MATERIAL             | Não         | Somente quando for logado com wallet, alerta quando chegar o material no valor informado                                                                                                                | 5                                                     |
| RESET_SHIELD_AUTO          | Não         | Somente quando for logado com wallet, irá da reset automaticamente quando chegar a zero                                                                                                                 | 1                                                     |
| IDENTIFY                   | Não         | Identificador da sua conta                                                                                                                                                                              |
| IGNORE_NUM_HERO_WORK       | Não         | Caso seja informado essa config, e ja tem a quantidade de heroes trabalhando conforme a configuração NUM_HERO_WORK, quando algum hero chegar a 100% de vida, ele irá colocar para trabalhar mesmo assim | 1                                                     |

## Comandos telegram

| Nome               | Descrição                                                                                                         |
| ------------------ | ----------------------------------------------------------------------------------------------------------------- |
| /rewards           | Retorna todas as moedas que você já minerou                                                                       |
| /stats             | Retorna o status dos heroes                                                                                       |
| /exit              | Da stop no bot                                                                                                    |
| /start             | Da start no bot                                                                                                   |
| /shield            | Retorna os dados dos shields                                                                                      |
| /rewards_all       | Retorna todos os rewards das contas, o rewards é atualizado sempre q começa um novo mapa ou a conta for conectada |
| /start_calc_farm   | Comando para iniciar o calculo do farm por hora                                                                   |
| /stop_calc_farm    | Comando para da stop no calculo do farm por hora e mostra os resultados                                           |
| /current_calc_farm | Mostra o relatório atual do cáculo de farm, mas não da stop                                                       |
| /gas_polygon       | Retona quanto custaria uma transação na polygon no momento                                                        |
| /withdraw          | Faz o claim caso tenha mais de 40 bombs                                                                           |
| /wallet            | Mostra o saldo da sua carteira                                                                                    |
| /reset_shield      | Restaura shield do hero                                                                                           |
