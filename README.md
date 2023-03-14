#Comandos DDL Linguagem SQL
Estudo dirigido em criação da tabela  atividade Proposta pelo Professor Matheus
<h1>Primeira atividade: Manipulando os comandos SQL</h1><br>
<h2>Matéria : Banco de Dados Relacional </h2><br>
<h2>Instituição: Fatec de Itapira </h2>
<h3>Atividade proposta pelo Professor Matheus com o intuito de treinar os principais comandos DDL, criando-se as tabelas: Cliente, Carro,Apolice,Sinistro</h3><br>


<h1>Criação da tabela Cliente </h1><br><br><br><br>

Create table cliente(<br>
    codCliente int PRIMARY KEY,<br>
    Nome VARCHAR(45) NOT NULL,<br>
    CPF VARCHAR(45) NOT NULL UNIQUE,<br>
    Sexo VARCHAR(20) NOT NULL ,<br>
    Estado VARCHAR(45) NOT NULL,<br>
    Cidade VARCHAR(45) DEFAULT 'itapira',<br>
    Bairro VARCHAR(45) NOT NULL,<br>
    Numero VARCHAR(45) NOT NULL,<br>
    Rua VARCHAR(45),<br>
    TelefoneFixo VARCHAR(45) NOT NULL,<br>
    TelefoneCelular VARCHAR(45) UNIQUE<br>

);

<hr>


<h1>Criação da tabela Carro</h1><br><br><br><br>


Create table Carro (<br>
    codCarro INT PRIMARY KEY,<br>
    Placa varchar(45) NOT NULL,<br>
    Marca VARCHAR(45) NOT NULL,<br>
    Modelo VARCHAR(45) NOT NULL,<br>
    Ano  VARCHAR(45) NOT NULL,<br>
    Chass VARCHAR(45)NOT NULL,<br>
    Cor VARCHAR(45) NOT NULL<br>
);

<hr>



<h1>Criação da tabela Apolice </h1><br><br><br><br>

Create table Apolice(<br>
    CodApolice INT PRIMARY KEY,<br>
     valorCobertura DECIMAL NOT NULL,<br>
    valorFranquia DECIMAL NOT NULL,<br>
    DataInicioVigencia Date  CHECK (dataInicioVigencia > GETDATE()),<br>
    DataFimVigencia DATE NOT NULL,<br>
    Cliente_codCliente  INT REFERENCES Cliente(codCliente),<br>
    Carro_codCarro INT REFERENCES Carro (codCarro)<br>

    
);
<hr>

<h1>Criação da tabela Sinistro </h1><br><br><br><br>

Create table Sinistro (<br>
    codSinistro INT,<br>
    HoraSinistro INT NOT NULL,<br>
    localSinsitro VARCHAR(45) NOT NULL,<br>
    Condutor VARCHAR(45),<br>
     Carro_codCarro int,<br>
  CONSTRAINT pk_Sinistro PRIMARY KEY (Carro_codCarro, codSinistro),<br>
  CONSTRAINT fk_Sinistro FOREIGN KEY (Carro_codCarro)REFERENCES Carro(codCarro),<br>


);
