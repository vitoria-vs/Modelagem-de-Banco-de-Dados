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

![image](https://github.com/vitoria-vs/Modelagem-de-Banco-de-Dados/assets/149893034/efad42fb-2c8c-4f20-b605-e525b94b83d8)
Este diagrama representa o modelo conceitual de um sistema de gerenciamento de uma escola de maneira mais clara e estruturada das entidades e seus relacionamentos.






