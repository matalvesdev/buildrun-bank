# JBank - Sistema de Banking com Spring Boot

Bem-vindo ao **JBank**, meu projeto de sistema bancário desenvolvido com Spring Boot! Aqui, construo e gerencio carteiras bancárias, permitindo depósitos, transferências, consultas de extratos e mantendo uma auditoria completa de todas as transações.

## Funcionalidades

- **Criar Carteira:** Posso criar uma nova carteira bancária informando CPF, e-mail e nome do titular.
- **Encerrar Carteira:** Consigo encerrar uma carteira existente, desde que o saldo esteja zerado.
- **Depositar Dinheiro:** Realizo depósitos em carteiras existentes, atualizando o saldo e registrando a operação no histórico.
- **Realizar Transferências:** Transfiro fundos entre carteiras, sempre com verificação de saldo suficiente.
- **Consultar Extrato:** Tenho acesso a um extrato detalhado de todas as transações de uma carteira, incluindo depósitos, transferências recebidas e enviadas, com data e hora.

## Entidades Principais

- **Carteira**
  - Código da Conta (UUID)
  - CPF (único)
  - E-mail (único)
  - Nome do Titular
  - Saldo Atual

- **Transferência**
  - Código da Transferência (UUID)
  - Carteira de Origem (Many-to-One)
  - Carteira de Destino (Many-to-One)
  - Valor da Transferência
  - Data e Hora

- **Depósito**
  - Código do Depósito (UUID)
  - Carteira de Destino (Many-to-One)
  - Valor Depositado
  - Data e Hora
  - Endereço IP do Usuário

## Regras de Negócio e Auditoria

- **Logging e Auditoria**
  - Implementei um filtro para capturar e logar o endereço IP de cada usuário em todas as requisições, incluindo esse IP no header de resposta.
  - Utilizo um interceptor para logar requisições e respostas, salvando detalhes como método HTTP, URL, código de status da resposta e endereço IP.

- **Validações**
  - Antes de realizar transferências, sempre verifico se a carteira de origem possui saldo suficiente.
  - Só permito o encerramento de carteiras com saldo zerado.
  - Garanto a consistência das operações utilizando transações do tipo ACID.

## Tecnologias Utilizadas

- **Spring Boot:** Estrutura principal do projeto.
- **Spring Data JPA:** Manipulação de dados e entidades.
- **Hibernate Validator:** Validação de dados.
- **APIs RESTful:** Para todas as operações de CRUD e transações.
- **Boas práticas de logging e auditoria:** Para garantir segurança e rastreabilidade.

## O que aprendo neste projeto

Ao desenvolver o JBank, pratico:

- Configuração de projetos Spring Boot;
- Manipulação de transações bancárias e regras de negócio;
- Implementação de filtros e interceptores para auditoria e logging;
- Validação de dados de entrada;
- Criação de APIs RESTful robustas e seguras.

Com este projeto, me capacito a construir e gerenciar sistemas backend robustos, seguros e auditáveis, seguindo as melhores práticas do mercado.
