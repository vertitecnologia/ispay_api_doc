##########
Introdução
##########

Descrição do Problema
=====================

Em cidades pequenas no interior do estado, as grandes operadoras de telefonia 
não fornecem o serviço de provedor de acesso à internet. Para que os clientes 
possam acessar a internet, precisam contratar um provedor local, o qual possui 
um link à rede. 

O faturamento do provedor vem principalmente do pagamento de boletos. 
No entanto, o atual modelo de faturamento possui alto custo, é de difícil 
gerenciamento, e possui alta taxa de inadimplência.

Solução Proposta
================

A solução proposta consiste em uma forma de pagamento em que o provedor 
disponibilizará terminais de pagamento em diversos estabelecimentos comerciais 
presentes na cidade, diminuindo a necessidade de boletos de pagamento.

Nestes terminais, o operador poderá consultar, através do CPF do cliente que utiliza 
o serviço disponibilizado pelo Provedor, quais faturas em aberto o cliente possui, 
e efetuar o pagamento no local.

Objetivo da API
===============

Estabelecer a forma e conteúdo que serão disponibilizados para integração com
outros sistemas denominados ERPs.

Áreas envolvidas
================

* Departamento tecnologia

* Departamento comercial / comercial / representantes

* Suporte

Metodologia
===========

As informações disponibilizadas no sistema ISpay, consulta, cadastro, edição e
exclusão serão disponibilizadas por meio de um *web service* de forma que possam
ser capturadas e integradas em outro sistema.

O sistema de ERP faz operações de cadastro, alterações, atualizações e remoção de
informações de faturas no sistema ISpay que atualiza os pagamentos de faturas realizadas 
através pontos de vendas.

Além disso, o ISpay disponibiliza faturas por meio de planilhas eletrônicas, tanto no website
quanto em formato .xls

Elaboração
==========

As informações serão disponibilizadas pelo *web service* padrão *REST*,
dados trocado no formato JSON.

I. Comercial

  a. Sempre que houver uma previsão de integração o departamento Comercial
     deverá informar o cliente sobre o processo e forma de integração.

  b. O comercial deve enviar para a área de TI o nome do software ERP, os
     dados de contato Técnico para que a área de TI possa realizar as tratativas
     Técnicas;

II. T.I.

  a. Com base nas tratativas com a empresa “desenvolvedora” do produto
     a área de T.I determinará o prazo para disponibilização das informações;

  b. Se for necessário, a área de T.I desenvolverá um plano de trabalho antes da integração.

  c. Toda tratativa será documentada de forma a minimizar os erros de comunicação.


Conferência
===========

Após definição do processo de integração, o responsável pela área de T.I deverá
fazer uma conferência minuciosa de todos os dados.

Aprovação
=========

A aprovação é realizada pela Área de T.I e pela fornecedora/desenvolvedora do sistema ERP.


Envio
=====

Toda documentação será enviada por meio eletrônico.
