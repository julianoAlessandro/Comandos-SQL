# Cria-o-da-tabela-usando-SQL
Estudo dirigido em criação da tabela  atividade Proposta pelo Professor Matheus
<h1>Primeira atividade: Manipulando os comandos SQL</h1><br>
<h2>Materia : Banco de Dados Relacional </h2><br>
<h2>Instituição: Fatec de Itapira </h2>
<h3>Atividade proposta pelo Professor Matheus com o intuito de treinar os principais comandos DDL, criando-se as tabelas: Cliente, Carro,Apolice,Sinistro</h3><br>


<h1>Criação da tabela Cliente </h1><br><br><br><br>

Create table cliente(
    codCliente int PRIMARY KEY,
    Nome VARCHAR(45) NOT NULL,
    CPF VARCHAR(45) NOT NULL UNIQUE,
    Sexo VARCHAR(20) NOT NULL ,
    Estado VARCHAR(45) NOT NULL,
    Cidade VARCHAR(45) DEFAULT 'itapira',
    Bairro VARCHAR(45) NOT NULL,
    Numero VARCHAR(45) NOT NULL,
    Rua VARCHAR(45),
    TelefoneFixo VARCHAR(45) NOT NULL,
    TelefoneCelular VARCHAR(45) UNIQUE

);

<hr>


<h1>Criação da tabela Carro</h1><br><br><br><br>


Create table Carro (
    codCarro INT PRIMARY KEY,
    Placa varchar(45) NOT NULL,
    Marca VARCHAR(45) NOT NULL,
    Modelo VARCHAR(45) NOT NULL,
    Ano  VARCHAR(45) NOT NULL,
    Chass VARCHAR(45)NOT NULL,
    Cor VARCHAR(45) NOT NULL
);

<hr>



<h1>Criação da tabela Apolice </h1><br><br><br><br>

Create table Apolice(
    CodApolice INT PRIMARY KEY,
     valorCobertura DECIMAL NOT NULL,
    valorFranquia DECIMAL NOT NULL,
    DataInicioVigencia Date  CHECK (dataInicioVigencia > GETDATE()),
    DataFimVigencia DATE NOT NULL,
    Cliente_codCliente  INT REFERENCES Cliente(codCliente),
    Carro_codCarro INT REFERENCES Carro (codCarro)

    
);
<hr>

<h1>Criação da tabela Sinistro </h1><br><br><br><br>

Create table Sinistro (
    codSinistro INT,
    HoraSinistro INT NOT NULL,
    localSinsitro VARCHAR(45) NOT NULL,
    Condutor VARCHAR(45),
     Carro_codCarro int,
  CONSTRAINT pk_Sinistro PRIMARY KEY (Carro_codCarro, codSinistro),
  CONSTRAINT fk_Sinistro FOREIGN KEY (Carro_codCarro)REFERENCES Carro(codCarro),


);
