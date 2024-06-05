# Sistema de Banco de Dados para uma Escola

# 1 - Cenário:

Descrição do Cenário:

A Escola "Educação Avançada" é uma instituição de ensino que oferece cursos para alunos do ensino fundamental e médio. A escola precisa de um sistema de banco de dados para gerenciar informações sobre alunos, professores, cursos, turmas e avaliações. O sistema deve ser capaz de armazenar e organizar dados de maneira eficiente, permitindo consultas rápidas e precisas.

Entidades, Atributos e Relacionamentos<br>
1. Aluno<br>

Atributos:<br>
ID_Aluno (chave primária, simples): Número único de identificação do aluno. <br>
Nome (simples): Nome completo do aluno.<br>
Endereço (composto): Rua, Número, Bairro, Cidade, Estado.<br>
Data_Nascimento (simples): Data de nascimento do aluno.<br>
E-mail (simples): Endereço de e-mail do aluno.<br>
Telefones (multivalorado): Lista de números de telefone do aluno.<br>
Idade (derivado): Calculado a partir da Data_Nascimento.<br>
Relacionamentos:<br>
Um aluno pode estar matriculado em muitas turmas (1:N com Matrícula).<br>
Um aluno pode receber muitas avaliações (1:N com Avaliação).<br>

2. Professor<br>

Atributos:<br>
ID_Professor (chave primária, simples): Número único de identificação do professor.<br>
Nome (simples): Nome completo do professor.<br>
Endereço (composto): Rua, Número, Bairro, Cidade, Estado.<br>
Data_Nascimento (simples): Data de nascimento do professor.<br>
E-mail (simples): Endereço de e-mail do professor.<br>
Telefones (multivalorado): Lista de números de telefone do professor.<br>
Especialidade (simples): Área de especialização do professor.<br>
Idade (derivado): Calculado a partir da Data_Nascimento.<br>
Relacionamentos:<br>
Um professor pode lecionar em muitas turmas (1:N com Turma).<br>

3. Disciplina<br>

Atributos:<br>
ID_Disciplina (chave primária, simples): Número único de identificação da disciplina.<br>
Nome (simples): Nome da disciplina.<br>
Carga_Horária (simples): Carga horária total da disciplina.<br>
Relacionamentos:<br>
Uma disciplina pode ter muitas turmas (1:N com Turma).<br>

4. Turma<br>

Atributos:<br>
ID_Turma (chave primária, simples): Número único de identificação da turma.<br>
Ano (simples): Ano letivo da turma.<br>
Semestre (simples): Semestre letivo da turma.<br>
Horário (simples): Horário das aulas da turma.<br>
Relacionamentos:<br>
Uma turma é ministrada por um professor (N:1 com Professor).<br>
Uma turma pertence a uma disciplina (N:1 com Disciplina).<br>
Uma turma pode ter muitos alunos matriculados (1:N com Matrícula).<br>
Uma turma pode ter muitas avaliações (1:N com Avaliação).<br>

5. Avaliação<br>

Atributos:<br>
ID_Avaliação (chave primária, simples): Número único de identificação da avaliação.<br>
Nota (simples): Nota recebida pelo aluno.<br>
Data_Avaliação (simples): Data em que a avaliação foi realizada.<br>
Relacionamentos:<br>
Uma avaliação é dada a um aluno (N:1 com Aluno).<br>
Uma avaliação é realizada em uma turma específica (N:1 com Turma).<br>

Resumo dos Relacionamentos<br>
Aluno - Matrícula: Um aluno pode estar matriculado em muitas disciplinas (1:N).<br>
Professor - Turma: Um professor pode lecionar em muitas turmas (1:N).<br>
Disciplina - Turma: Uma disciplina pode ter muitas turmas (1:N).<br>
Turma - Matrícula: Uma turma pode ter muitos alunos matriculados (1:N).<br>
Turma - Avaliação: Uma turma pode ter muitas avaliações (1:N).<br>
Aluno - Avaliação: Um aluno pode receber muitas avaliações (1:N).<br>

# 2 - Modelagem Conceitual: <br>

![image](https://github.com/vitoria-vs/Modelagem-de-Banco-de-Dados/assets/149893034/efad42fb-2c8c-4f20-b605-e525b94b83d8)<br>
Este diagrama representa o modelo conceitual de um sistema de gerenciamento de uma escola de maneira mais clara e estruturada das entidades e seus relacionamentos.<br>

# 3 - Modelagem Lógica:<br>

![image](https://github.com/vitoria-vs/Modelagem-de-Banco-de-Dados/assets/149893034/0033e7e4-6698-4452-9ab8-d2431e78205c)<br>
Este modelo lógico detalha a estrutura do banco de dados, especificando as chaves primárias e estrangeiras para garantir a integridade referencial e o correto relacionamento entre as entidades do sistema.<br>

# 4 - Modelagem Física:<br>

Este projeto implementa a modelagem física de um banco de dados para uma escola utilizando SQL Server. Abaixo mostra como as tabelas foram criadas e as relações entre elas.<br><br>
Tabela aluno: 
```sql
CREATE TABLE Aluno (
    ID_Aluno INT PRIMARY KEY,
    Nome VARCHAR(100),
    Rua VARCHAR(100),
    Numero INT,
    Bairro VARCHAR(50),
    Cidade VARCHAR(50),
    Estado VARCHAR(50),
    Data_Nascimento DATE,
    Email VARCHAR(100),
    Idade INT
);
```
Tabela Telefones Aluno:
```sql
CREATE TABLE Telefones_Aluno (
    ID_Aluno INT,
    Telefone VARCHAR(15),
    FOREIGN KEY (ID_Aluno) REFERENCES Aluno(ID_Aluno)
);
```
Tabela Professor:
```sql
CREATE TABLE Professor (
    ID_Professor INT PRIMARY KEY,
    Nome VARCHAR(100),
    Rua VARCHAR(100),
    Numero INT,
    Bairro VARCHAR(50),
    Cidade VARCHAR(50),
    Estado VARCHAR(50),
    Data_Nascimento DATE,
    Email VARCHAR(100),
    Especialidade VARCHAR(100),
    Idade INT
);
```
Tabela Telefones Professor:
```sql
CREATE TABLE Telefones_Professor (
    ID_Professor INT,
    Telefone VARCHAR(15),
    FOREIGN KEY (ID_Professor) REFERENCES Professor(ID_Professor)
);
```
Tabela Disciplina:
```sql
CREATE TABLE Disciplina (
    ID_Disciplina INT PRIMARY KEY,
    Nome VARCHAR(100),
    Carga_Horaria INT
);
```
Tabela Turma:
```sql
CREATE TABLE Turma (
    ID_Turma INT PRIMARY KEY,
    Ano INT,
    Semestre INT,
    Horario VARCHAR(50),
    ID_Professor INT,
    ID_Disciplina INT,
    FOREIGN KEY (ID_Professor) REFERENCES Professor(ID_Professor),
    FOREIGN KEY (ID_Disciplina) REFERENCES Disciplina(ID_Disciplina)
);
```
Tabela Aluno Turma:
```sql
CREATE TABLE Aluno_Turma (
    ID_Aluno INT,
    ID_Turma INT,
    PRIMARY KEY (ID_Aluno, ID_Turma),
    FOREIGN KEY (ID_Aluno) REFERENCES Aluno(ID_Aluno),
    FOREIGN KEY (ID_Turma) REFERENCES Turma(ID_Turma)
);
```
Tabela Avaliação:
```sql
CREATE TABLE Avaliacao (
    ID_Avaliacao INT PRIMARY KEY,
    Nota FLOAT,
    Data_Avaliacao DATE,
    ID_Aluno INT,
    ID_Turma INT,
    FOREIGN KEY (ID_Aluno) REFERENCES Aluno(ID_Aluno),
    FOREIGN KEY (ID_Turma) REFERENCES Turma(ID_Turma)
);
```
# 5 - Inserção de Dados:<br>
A seguir é demonstrada a inserção de dados na Tabela Aluno.<br>
```sql
INSERT INTO Aluno (ID_Aluno, Nome, Rua, Numero, Bairro, Cidade, Estado, Data_Nascimento, Email, Idade) VALUES
(1,'João Silva', 'Rua das Flores', 123, 'Centro', 'São Paulo', 'SP',  '1990-05-10', 'joao@gmail.com',22),
(2,'Maria Santos', 'Avenida Principal', 456, 'Jardim', 'Rio de Janeiro', 'RJ','1993-05-10' ,'maria@hotmail.com',22),
(3, 'Pedro Oliveira', 'Rua dos Coqueiros', 789, 'Praia', 'Florianópolis', 'SC', '1995-08-15', 'pedro@example.com', 29),
(4, 'Ana Silva', 'Rua das Palmeiras', 102, 'Centro', 'Salvador', 'BA', '1993-03-25', 'ana@example.com', 31),
(5, 'Lucas Fernandes', 'Avenida das Flores', 567, 'Jardins', 'Brasília', 'DF', '1992-11-12', 'lucas@example.com', 32),
(6, 'Juliana Costa', 'Rua da Esperança', 321, 'Vila Nova', 'Recife', 'PE', '1994-07-18', 'juliana@example.com', 30),
(7, 'Felipe Santos', 'Rua dos Girassóis', 888, 'Campestre', 'Porto Alegre', 'RS', '1991-09-30', 'felipe@example.com', 33),
(8, 'Aline Lima', 'Avenida das Acácias', 444, 'Floresta', 'Manaus', 'AM', '1996-02-08', 'aline@example.com', 28),
(9, 'Rafaela Oliveira', 'Rua dos Pinheiros', 555, 'Jardim', 'Campinas', 'SP', '1993-12-20', 'rafaela@example.com', 31),
(10, 'Gabriel Pereira', 'Rua das Oliveiras', 777, 'Centro', 'Goiânia', 'GO', '1990-06-05', 'gabriel@example.com', 32),
(11, 'Mariana Costa', 'Avenida dos Lírios', 333, 'Alameda', 'Fortaleza', 'CE', '1992-04-17', 'mariana@example.com', 30),
(12, 'Thiago Souza', 'Rua das Amendoeiras', 222, 'Praia', 'Natal', 'RN', '1995-11-28', 'thiago@example.com', 27),
(13, 'Carla Santos', 'Rua das Violetas', 696, 'Bela Vista', 'São Luís', 'MA', '1994-08-10', 'carla@example.com', 29),
(14, 'Daniel Almeida', 'Avenida das Margaridas', 111, 'Centro', 'Belém', 'PA', '1991-10-15', 'daniel@example.com', 32),
(15, 'Isabela Ferreira', 'Rua dos Ipês', 999, 'Jardim', 'Cuiabá', 'MT', '1990-03-20', 'isabela@example.com', 34),
(16, 'Diego Rocha', 'Avenida das Orquídeas', 777, 'Alameda', 'João Pessoa', 'PB', '1993-07-08', 'diego@example.com', 31),
(17, 'Camila Oliveira', 'Rua dos Lírios', 444, 'Vila Nova', 'Curitiba', 'PR', '1996-01-25', 'camila@example.com', 28),
(18, 'Luciana Silva', 'Rua das Tulipas', 555, 'Centro', 'Teresina', 'PI', '1992-05-30', 'luciana@example.com', 29),
(19, 'Anderson Santos', 'Avenida dos Cravos', 888, 'Bela Vista', 'Florianópolis', 'SC', '1990-09-12', 'anderson@example.com', 31),
(20, 'Fernanda Costa', 'Rua das Rosas', 222, 'Praia', 'São Luís', 'MA', '1995-04-18', 'fernanda@example.com', 27);
```
















