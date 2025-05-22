# Desafio-Esquema-conceitual-de-uma-oficina-mecanica-
Neste repositório está disponível um desafio do curso "Suzano - Análise de Dados com Power BI", com o objetivo de modelar um esquema conceitual de um banco de dados de uma oficina.


Descrição do desafio:
Oficina - Narrativa
· Sistema de controle e gerenciamento de execução de ordens de servico em uma oficina mecânica.
· Clientes levam veículos à oficina mêcanica para serem consertados ou para passarem por revisões periódicas.
· Cada veículo é designado a uma equipe de mecânicos que identifica os serviços a serem executados e preenche uma OS com data de entrega.
· A partir da OS, calcula-se o valor de cada serviço, consultando-se uma tabela de referência de mão-de-obra.
· O valor de cada peça também irá compor a OS.
· O cliente autoriza a execução dos serviços.
· A mesma equipe avalia e executa os serviços.
· Os mecânicos possuem código, nome, endereço e especialidade.
· Cada OS possui: n°, data de emissão, um valor, status e uma data para conclusão dos trabalhos.
· Uma OS pode ser composta por vários serviços e um mesmo serviço pode estar contido em mais de uma OS.
· Uma OS pode ter vários tipos de peça e uma peça pode estar presente em mais de uma OS.


# 🔧 Sistema de Gestão de Ordens de Serviço - Oficina Mecânica

Este repositório contém o **esquema conceitual e relacional** de um banco de dados para gerenciamento de **ordens de serviço (OS)** em uma **oficina mecânica**. O objetivo é organizar o fluxo de trabalho entre clientes, veículos, equipes de mecânicos, serviços, peças e mão de obra.

---

## 🗃️ Estrutura do Banco de Dados

### 📌 Cliente
- `idCliente`: Identificador do cliente
- `Nome`, `CPF/CNPJ`, `Telefone`, `Endereço completo` (CEP, cidade, estado, logradouro, número, bairro)

### 📌 Veículo
- `idVeiculo`: Identificador do veículo
- `Marca`, `Modelo`, `Placa`, `Ano`, `Conserto/Revisao` (tipo)
- `Cliente_idCliente`: Chave estrangeira para o cliente
- `Equipe_idEquipe`: Equipe designada para o serviço

### 📌 Equipe
- `idEquipe`: Identificador da equipe
- `Descricao`: Nome ou descrição da equipe
- `Quantidade`: Número de membros da equipe

### 📌 Mecânico
- `idMecanico`: Identificador do mecânico
- `Nome`, `Especialidade`, `CPF/CNPJ`, `Telefone`, `Endereço`
- `Inicio/Expediente`, `Fim/Expediente`, `Trabalhando`
- `Equipe_idEquipe`: Chave estrangeira para a equipe

### 📌 Ordem de Serviço (OrdemServico)
- `idOrdemServico`: Identificador da OS
- `Numero`, `DataEmissao`, `DataConclusao`, `ValorTotal`, `Status`, `AutorizacaoCliente`
- `Veiculo_idVeiculo`, `Veiculo_Cliente_idCliente`: Relacionamento com veículo e cliente

### 📌 Serviço
- `idServico`: Identificador do serviço
- `Descricao`
- `Equipe_idEquipe`: Equipe responsável

### 📌 Mão de Obra
- `idMaoDeObra`: Identificador
- `Descricao`, `Valor`

### 📌 Serviço_has_MaoDeObra
Tabela associativa:
- Relaciona um serviço com sua mão de obra e equipe

### 📌 Peça
- `idPeca`: Identificador
- `Descricao`, `Fabricante`, `Valor`, `MarcaCarro`, `ModeloCarro`, `Ano`

### 📌 RelacaoOS/Servicos
Tabela associativa:
- Relaciona uma OS com um ou mais serviços

### 📌 RelacaoOS/Pecas
Tabela associativa:
- Relaciona uma OS com uma ou mais peças

---

## ✅ Regras e Relacionamentos

- Um **cliente** pode possuir vários **veículos**.
- Um **veículo** pode estar vinculado a uma **ordem de serviço** e a uma **equipe**.
- Uma **ordem de serviço** pode conter vários **serviços** e várias **peças**.
- Um **serviço** pode ser realizado em várias OS e estar associado a diferentes **mãos de obra**.
- As **equipes** são compostas por vários **mecânicos**.
- Cada **mão de obra** tem um valor base e está associada a um tipo de **serviço**.

---

## 📁 Estrutura do Repositório

- `Oficina.png`: Diagrama ER do banco de dados
- `README.md`: Documentação do projeto

---

## 📌 Objetivo

Oferecer uma estrutura sólida e escalável para o gerenciamento das operações de uma oficina mecânica, melhorando a organização, o controle de serviços e a eficiência do atendimento ao cliente.

---

## 🧠 Autor

Este projeto foi elaborado para fins acadêmicos e didáticos, com foco em **modelagem conceitual e relacional de banco de dados**.

- Cadastro de clientes
- Histórico de serviços por veículo
- Emissão de relatórios

---

📦 Este sistema é ideal para oficinas que desejam aumentar sua organização, reduzir erros e melhorar a comunicação com os clientes.
