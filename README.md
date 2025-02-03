# Alerta de SLA de chamados do Jira no Google Chat

### Propósito
Este projeto tem como objetivo a construção de um BOT que verifica os SLA de Primeiro Atendimento e Resolução no Jira e avisa o grupo de operadores no Google Chat se algum SLA esta prestes a vencer.

### Instalação e configuração

- clone o repositório seguindo os comandos abaixo ou baixe o pacote da aplicação dentro de uma pasta com o nome `jira_google_chat_sla_alert`, anote o caminho para depois referenciar dentro do arquivo `bot.sh`
```sh
$ git clone //URL do Repositorio
$ cd jira_google_chat_sla_alert
```
- instale o nodejs e as dependências se ainda não tiver instalado
```sh
$ sudo apt update
$ sudo apt install -Y nodejs npm
```
- Pronto !

### Como configurar no servidor ubuntu para rodar automaticamente
- Não se esqueça que a instalação e configuração de dependências deve ser feita no servidor também. O caminho dentro do arquivo `bot.sh` deve ser alterado.

- Um token para acesso a API deve ser gerado no Jira e informado no campo `jiraAuthorization` em `bot_sla_jira.js` para que a aplicação tenha acesso ao Jira.

- Para que o programa rode a cada x minutos, vamos usar o arquivo `bot.sh`, esse arquivo chama o programa `bot_sla_jira.js` que faz a checagem de SLA. Dessa forma fica mais fácil incluir o arquivo `.sh` no crontab do Ubuntu. Ele também vai gerar um arquivo de log local.

- No crontab do Ubuntu, editamos com o seguinte comando
```sh
crontab -e
```

- Depois editamos o arquivo para que o nosso script seja chamado a cada x minutos, nesse caso a cada 7 minutos.
```sh
# Edit this file to introduce tasks to be run by cron.
#
# m h  dom mon dow   command
*/7 * * * * /home/user_name/jira_google_chat_sla_alert/bot.sh
```

- Pronto !


