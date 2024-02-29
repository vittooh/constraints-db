# constraints-db
Script para expliacação de constraints em bancos de dados, vídeo no canal.

CREATE TABLE atletas (
    id INT PRIMARY KEY,
    nome VARCHAR(100) not null,
    cpf VARCHAR(14) not null,
    telefone VARCHAR(20),
    idade INT,
    tipoEsporte VARCHAR(50)
);

CREATE TABLE inscricao (
    idEvento INT,
    idAtleta INT,
    PRIMARY KEY (idEvento, idAtleta),
    FOREIGN KEY (idAtleta) REFERENCES atletas(id)
);

alter table atletas alter column
nome set not null;

alter table atletas alter column
cpf set not null;

ALTER TABLE atletas
ADD CONSTRAINT CHK_Idade_Range CHECK (idade >= 18 AND idade <= 150);

alter table atletas 
add constraint check_range_esportes check (tipoEsporte in ('musculacao',
'corrida','natacao','bike'));

ALTER TABLE atletas
ADD CONSTRAINT UQ_Nome_CPF UNIQUE (nome, cpf);


insert into atletas values (2,'vhcs','0000000','34',18,'bike');

