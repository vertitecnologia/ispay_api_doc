###########
Visão geral
###########

Endpoints
=========

Os endpoints são mapeados como segue::

    http://ispay.vertitecnologia.com.br/api/v1/caminho/para/resource

Autenticação
============

Cada operador receberá a sua api key, que deverá ser passada na URL em TODAS as
requisições feitas à API.

Exemplo::

    http://ispay.vertitecnologia.com.br/api/v1/caminho/para/api?access_token=837e068fbb4c1e1f


Gerenciamento de tokens
=======================

* O usuário administrador do provedor pode gerar, revogar e listar quando um token foi utilizado
pela última vez para realizar uma operação.
* Esse gerenciamento é feito através da página de gerenciamento no website da ISpay na qual 
que somente o administradores do provedor terão acesso.
* É possível ver o valor do token somente quando ele é gerado por 10 minutos, após isso o usuário
administrador deve copiar seu valor para utilizá-lo em futuras operações.


Exemplo de requisição válida
============================

Essa requisição lista toda as categorias de um determinado operador::

    GET http://ispay.vertitecnologia.com.br/api/v1/bills?access_token=213qweasdzxc

Códigos de retorno e seus significados
======================================

* 200: Requisição processada com sucesso / entidade salva com sucesso
* 201: Entidade criada com sucesso
* 204: Entidade excluída com sucesso
* 400: Algum parâmetro obrigatório faltando ou com formato errado
* 401: Tentativa de acesso a entidade não permitida
* 422: Entidade não salva por conta de erros de validação

Código de exemplo
=================

Um exemplo de código em linguagem Python para acessar a API do ISpay está
disponível no `repositório da Verti no github`_.

.. _repositório da Verti no github: https://github.com/vertitecnologia/vmpay_api_client
