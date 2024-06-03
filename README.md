# Sistema de Banco de Dados para uma Escola

# 1 - Cenário:

Descrição do Cenário:

A Escola "Educação Avançada" é uma instituição de ensino que oferece cursos para alunos do ensino fundamental e médio. A escola precisa de um sistema de banco de dados para gerenciar informações sobre alunos, professores, cursos, turmas e avaliações. O sistema deve ser capaz de armazenar e organizar dados de maneira eficiente, permitindo consultas rápidas e precisas.

Entidades, Atributos e Relacionamentos
1. Aluno

Atributos:
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

2. Professor<br><br>

Atributos:
ID_Professor (chave primária, simples): Número único de identificação do professor.
Nome (simples): Nome completo do professor.
Endereço (composto): Rua, Número, Bairro, Cidade, Estado.
Data_Nascimento (simples): Data de nascimento do professor.
E-mail (simples): Endereço de e-mail do professor.
Telefones (multivalorado): Lista de números de telefone do professor.
Especialidade (simples): Área de especialização do professor.
Idade (derivado): Calculado a partir da Data_Nascimento.
Relacionamentos:
Um professor pode lecionar em muitas turmas (1:N com Turma).

3. Disciplina

Atributos:
ID_Disciplina (chave primária, simples): Número único de identificação da disciplina.
Nome (simples): Nome da disciplina.
Carga_Horária (simples): Carga horária total da disciplina.
Relacionamentos:
Uma disciplina pode ter muitas turmas (1:N com Turma).

4. Turma

Atributos:
ID_Turma (chave primária, simples): Número único de identificação da turma.
Ano (simples): Ano letivo da turma.
Semestre (simples): Semestre letivo da turma.
Horário (simples): Horário das aulas da turma.
Relacionamentos:
Uma turma é ministrada por um professor (N:1 com Professor).
Uma turma pertence a uma disciplina (N:1 com Disciplina).
Uma turma pode ter muitos alunos matriculados (1:N com Matrícula).
Uma turma pode ter muitas avaliações (1:N com Avaliação).

5. Avaliação

Atributos:
ID_Avaliação (chave primária, simples): Número único de identificação da avaliação.
Nota (simples): Nota recebida pelo aluno.
Data_Avaliação (simples): Data em que a avaliação foi realizada.
Relacionamentos:
Uma avaliação é dada a um aluno (N:1 com Aluno).
Uma avaliação é realizada em uma turma específica (N:1 com Turma).

Resumo dos Relacionamentos
Aluno - Matrícula: Um aluno pode estar matriculado em muitas disciplinas (1:N).
Professor - Turma: Um professor pode lecionar em muitas turmas (1:N).
Disciplina - Turma: Uma disciplina pode ter muitas turmas (1:N).
Turma - Matrícula: Uma turma pode ter muitos alunos matriculados (1:N).
Turma - Avaliação: Uma turma pode ter muitas avaliações (1:N).
Aluno - Avaliação: Um aluno pode receber muitas avaliações (1:N).

# 2 - Modelagem Conceitual: 

![image](https://github.com/vitoria-vs/Modelagem-de-Banco-de-Dados/assets/149893034/efad42fb-2c8c-4f20-b605-e525b94b83d8)
Este diagrama representa o modelo conceitual de um sistema de gerenciamento de uma escola de maneira mais clara e estruturada das entidades e seus relacionamentos.






