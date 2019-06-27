# Base de dados de CEPs com código do IBGE

Neste exemplo você terá acesso a um banco de dados completo e atualizado com todos os CEPs do Brasil com código do IBGE no formato SQL. Faça download! 

Confira o passo a passo para a criação desse banco de dados no endereço https://www.devmedia.com.br/exemplo/base-de-dados-de-ceps-com-codigo-do-ibge/39

Diversos sistemas do nosso dia-a-dia precisam de informações do endereço de um cliente, fornecedor, nota fiscal, etc, não é verdade? Imagine no seu sistema ao digitar um CEP e as demais informações (logradouro, bairro, município, uf) serem preenchidas automaticamente. Você terá um software que oferece uma melhor experiência ao usuário e ainda evitará erros na digitação dos endereços.

No link acima você encontra uma base de dados completa e atualizada com todos os CEPs do Brasil, além de todas as cidades com código do IBGE, outro campo que é utilizado com frequência em aplicações que usam Nota Fiscal Eletrônica,por exemplo.

## Coluna Código do IBGE da cidade
O campo que representa o código do IBGE da cidade, presente nas duas tabelas,é muito utilizado em sistemas de automação comercial na hora de emitir uma Nota Fiscal Eletrônica (NF-e), situação em que você precisa informar o código da cidade além de sua descrição.

## Coluna Descrição sem Número
O campo descricao_sem_numero é uma derivação do campo descricao da tabela de logradouro. Como muitos CEPs dos Correios possuem um número em seus logradouros (exemplo: Avenida Tal - 3000), optamos por removê-los e criar uma coluna apenas com o nome do logradouro. Você pode então optar por usar uma ou outra em suas aplicações.

## Notas

A base de CEPs do Brasil pode possuir inconsistências, por exemplo, nos nomes dos logradouros. Além disso, novos CEPs podem ser criados e outros modificados. Caso você encontre algum ajuste que precise ser feito nessa base de dados, fique à vontade para nos enviar e faremos a atualização.

## Consultas comuns

### Exibindo lista de cidades por uma determinada UF

```SELECT DESCRICAO, CODIGO_IBGE, DDD
FROM CIDADE
WHERE UF = 'RJ'
ORDER BY DESCRICAO

### Exibindo lista de CEPs de uma determinada UF e Cidade

```SELECT DESCRICAO_SEM_NUMERO, DESCRICAO_BAIRRO, DESCRICAO_CIDADE, CEP, CODIGO_CIDADE_IBGE
FROM LOGRADOURO
WHERE UF = 'RJ' AND DESCRICAO_CIDADE = 'RIO DE JANEIRO'
ORDER BY DESCRICAO_BAIRRO, DESCRICAO_SEM_NUMERO

### Exibindo dados de um logradouro a partir do seu CEP

```SELECT DESCRICAO_SEM_NUMERO, DESCRICAO_BAIRRO, DESCRICAO_CIDADE, CEP, CODIGO_CIDADE_IBGE
FROM LOGRADOURO
WHERE CEP = '22775003'
