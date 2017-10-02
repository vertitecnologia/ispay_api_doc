########
Faturas
########

Criar
=====

Cria uma fatura

::

    POST /api/v1/bills

Request::

  {
    "access_token": "213qweasdzxc",
    "bill": {
      "name": "João da Silva",
      "cpf": "35793476164",
      "due_date":"05/01/2018",
      "ref": "12/2017",
      "price_cents": 5000,
      "description": "",
      "item": "Serviço 1"
    }
  }

Campos
------

Obrigatórios
^^^^^^^^^^^^

* *bill*

  * *name*: Nome do cliente.
  * *cpf*: CPF (obrigatório apenas quando for pessoa física).
  * *due_date*: Data de vencimento da fatura no formato dd/mm/aaaa
  * *ref*: Data de referência da fatura no formato mm/aaaa
  * *price_cents*: Preço em centavos. No exemplo acima o valor da fatura seria de R$50,00

Opcionais
^^^^^^^^^
  * *description*: Descrição da fatura
  * *item*: Item da fatura

Retorno
-------

======  ==================
status  descrição
======  ==================
201     Criado com sucesso
======  ==================

Exemplo:

::

	26

* Valor retornado é o id da fatura

Erros
-----

==========  ====================================  ====================================================
status      descrição                             response body
==========  ====================================  ====================================================
422         erro ao criar                         ver exemplo abaixo
==========  ====================================  ====================================================

422 - erro ao criar

Para valor de CPF passado como "123" (formato inválido):

::

  {
    "error":
      {
        "cpf":["is invalid"]
      }
  }

caso o valor de CPF que é obrigatório não for passado na requisição:

::

  {
    "error":
      {
        "cpf":["can't be blank", "is invalid"]
      }
  }

Ver
===

::

    GET /api/v1/bills/[id]

Obtem informações de uma fatura através do ID dela obtido quando ela é criada.

Parâmetros de URL:
------------------

=========  ===============  ===========
parâmetro  descrição        obrigatório
=========  ===============  ===========
id         id da fatura     sim
=========  ===============  ===========

Request::

  {
    "access_token": "213qweasdzxc"
  }


Retorno
-------

======  =========
status  descrição
======  =========
200     OK
======  =========

Exemplo:

::

  {
    "id": 32, 
    "name": "Cliente fictício", 
    "cpf": "49448828071", 
    "price_cents": 8800, 
    "due_date": "2017-11-05"
    "paid_at": "2017-10-03T00:00:00.000Z", 
    "ref": "2017-10-01T00:00:00.000Z", 
    "item": "Serviço de internet 1", 
    "description": "Sem descrição", 
  }

Erros
-----

==========  ========================  =========================================
status      descrição                 response body
==========  ========================  =========================================
404         fatura não encontrado     { "status": "404", "error": "Not Found" }
==========  ========================  =========================================

Listar
======

::

    GET /api/v1/bills

Obtenção de faturas pagas a partir de uma data especificada. Por exemplo caso seja enviado
“01/10/2017”, todos os ids de faturas pagas a partir dessa data serão enviados.

Request::

  {
    "access_token": "213qweasdzxc"
    "start_date_paid": "01/10/2017"
  }

Campos
------

* start_date_paid indica a partir de qual

Retorno
-------

======  =========
status  descrição
======  =========
200     OK
======  =========

Exemplo:

::

  [21,33,45]

Atualizar
=========

Faz update de campos de fatura especificada pelo ID.

::

    PATCH /api/v1/bills/[id]

Parâmetros de URL:
------------------

=========  ===============  ===========
parâmetro  descrição        obrigatório
=========  ===============  ===========
id         id da fatura     sim
=========  ===============  ===========

Request::

   {
     "access_token": "213qweasdzxc",
     "bill": {
       "name": "Silva João",
     }
   }

Campos
------

Ao menos um campo interno a *client* deve ser passado.

Retorno
-------

======  ======================
status  descrição
======  ======================
200     Atualizado com sucesso
======  ======================

Erros
-----

==========  ====================================  ====================================================
status      descrição                             response body
==========  ====================================  ====================================================
404         fatura não encontrada                 { "status": "404", "error": "Not Found" }
422         erro ao atualizar                     ver exemplo abaixo
==========  ====================================  ====================================================

422 - erro ao atualizar

::

  {
    "error":
      {
        "cpf":["is invalid"]
      }
  }

Excluir
=======

Exclui fatura através do seu ID

::

    DELETE /api/v1/bills/[id]

Parâmetros de URL:
------------------

=========  ===============  ===========
parâmetro  descrição        obrigatório
=========  ===============  ===========
id         id da fatura     sim
=========  ===============  ===========

Request::

  {
    "access_token": "213qweasdzxc"
  }

Retorno
-------

======  ====================  =============
status  descrição             response body
======  ====================  =============
204     Excluído com sucesso  (vazio)
======  ====================  =============

Erros
-----

==========  ====================================  ====================================================
status      descrição                             response body
==========  ====================================  ====================================================
404         fatura não encontrada                 { "status": "404", "error": "Not Found" }
==========  ====================================  ====================================================
