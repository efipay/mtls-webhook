# mTLS Nginx Docker

Este projeto consiste em uma configuração de Nginx utilizando Docker que visa simplificar o processo de criação de um servidor com mTLS para o recebimento de webhooks das APIs Efí.

Basta que as variáveis de ambiente sejam configuradas no arquivo .env e seja inserido os certificados (fullchain.pem e privkey.pem) no diretório /certs.

Feito isso esse servidor irá intermediar a comunicação entre a API Efí e a sua aplicação, garantindo a segurança da comunicação através do uso de certificados. Para utilizar o servidor basta executar o comando `docker-compose up -d` e o servidor estará disponível na porta que você configurou no arquivo `.env` do servidor configurado na propriedade `DOMAIN` em seu `.env`. Sua aplicação final pode ser feita em qualquer stack, esse servidor irá apenas intermediar a comunicação.

Caso seja necessário receber/redirecionar os webhooks para um caminho diferente de /webhook e/ou /webhook/pix basta que seja alterado a linha 12 do arquivo templates/services.conf.template substituindo o "/webhook" para o caminho desejado, por exemplo "^/webhook(/pix)?$". 
Lembrando que o "/pix" é adicionado automaticamente quando o webhook for de fato acionado no caso de se tratar da API Pix, podendo ser contornado cadastrando sua URL de webhook contendo "?ignorar=" no final.

Por se tratar de um servidor nginx, é possível adicionar novas configurações de acordo com a necessidade do usuário, para isso basta adicionar as configurações no arquivo config/nginx.conf.

Se tiverem alguma dúvida, entre em contato conosco. Estamos à disposição para ajudá-los da forma mais assertiva possível.