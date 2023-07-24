# Zabrix24

![enter image description here](https://i.imgur.com/h82S9uk.png)

"Zabrix24" é uma solução de integração que conecta o poderoso sistema de monitoramento **Zabbix** com a plataforma colaborativa **Bitrix24**. Essa integração permite que equipes de operações e suporte acompanhem e ajam rapidamente em eventos críticos de infraestrutura, fornecendo comunicação em tempo real e notificações para os grupos específicos do Bitrix24. Com o Zabrix24, as equipes podem receber alertas e atualizações diretamente no chat do Bitrix24, facilitando a colaboração e a resolução ágil de problemas. Simplifique a gestão de incidentes e melhore a produtividade da equipe com a integração perfeita entre Zabbix e Bitrix24 através do Zabrix24.


# Configuração

```
#!/bin/bash

# Verificar se todos os argumentos foram fornecidos
if [ $# -ne 1 ]; then
    echo "Uso: $0 <message>"
    exit 1
fi

# Obter o valor da macro {ALERT.MESSAGE} como o parâmetro "message"
message="$1"

# Definir as credenciais (substitua pelos valores corretos)
botId="999"
restId="99"
clientId="wfvd2n9zl7hxi7llhr20mmzii0dgnywu"
dialogId="268"

# Montar a URL do webhook
webhookUrl="https://URL-TO-BITRIX.bitrix24.com.br/rest/${restId}/vk6k5y52frwh4nyd/imbot.message.add.json?"

# Montar os parâmetros do POST
data="BOT_ID=${botId}&CLIENT_ID=${clientId}&DIALOG_ID=${dialogId}&MESSAGE=${message}"

# Executar o POST usando o comando curl
response=$(curl -s -X POST -d "${data}" "${webhookUrl}")

# Verificar se ocorreu algum erro no POST
if [ $? -ne 0 ]; then
    echo "Erro ao enviar o POST"
    exit 1
fi

# Imprimir a resposta do Bitrix24 (somente para fins de depuração)
echo "$response"
```

# Em breve mais detalhes...
