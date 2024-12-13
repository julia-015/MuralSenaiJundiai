# MuralSenaiJundiaí
# MuralSenaiJundiaí
**Descrição Geral do Sistema**

Este sistema foi desenvolvido para aprimorar a comunicação interna e a gestão de informações acadêmicas no SENAI. Ele oferece funcionalidades para o gerenciamento de avisos, turmas, cursos e alunos, com recursos organizacionais em uma interface intuitiva.

---

**Estrutura de Dados**

**Modelos Django**

1. **Login**:
    - **Atributos**:
        - `username`: Nome do usuário (máx. 50 caracteres).
        - `password`: Senha do usuário.
    - **Método**:
        - `__str__()`: Retorna o nome do usuário.
2. **Cadastro**:
    - **Atributos**:
        - `nome`: Nome completo (máx. 100 caracteres).
        - `email`: E-mail do usuário.
        - `profissao`: Profissão do cadastrado dentro da instituição, para definição do que tem acesso.
        - `criarsenha`: Senha do usuário.
    - **Método**:
        - `set_senha(raw_password)`: Configura a senha.
3. **Curso**:
    - **Atributos**:
        - `curso`: Nome do curso (máx. 100 caracteres).
        - `icon`: Ícone representativo (opcional).
    - **Método**:
        - `__str__()`: Retorna o nome do curso.
4. **Turma**:
    - **Atributos**:
        - `turma`: Identificador da turma.
        - `periodo`: Período da turma.
        - `curso`: Curso associado (chave estrangeira).
    - **Método**:
        - `__str__()`: Retorna a turma e seu curso.
5. **Aluno**:
    - **Atributos**:
        - `nome`: Nome do aluno.
        - `telefone`: Contato.
        - `nome_pai` e `nome_mae`: Informações familiares.
        - `turma`: Chave estrangeira para a turma.
        - `observacoes`: Informações adicionadas pelos professores.
    - **Método**:
        - `__str__()`: Retorna o nome do aluno e sua turma.
6. **Aviso**:
    - **Atributos**:
        - `mensagem`: Texto do aviso.
        - `data_criacao: Timestamp de criação.
    - **Método**:
        - `__str__()`: Retorna o aviso com sua data.

---

**Formulários**

Os formulários utilizados no código são:

**Formulário de Login (”FormLogin”)**: Validação de login e autenticação de usuários.

**Formulário de Cadastro (”FormCadastro”)**: Registro de dados de cadastro.

**Formulário de Alunos (”FormAluno”)**: Registro de alunos e edição.

**Formulário de Cursos (”FormCurso”)**: Registro de cursos.

**Formulário de Turma (”FormTurma”)**: Registro e edição de turmas.

---

**Endpoints**

1. `/`:
Tela inicial com login.
2. `/inicio/`:
    - Tela inicial pós-login.
3. `/cadastro/`:
    - Registro de novos usuários.
4. `/muralaviso/`:
    - Exibição de avisos gerais.
5. `/carometro/`:
    - Listagem de cursos cadastrados.
6. `/carometro2/<curso_id>/`:
    - Listagem de turmas relacionadas ao curso.
7. `/carometro3/<turma_id>/`:
    - Listagem de alunos por turma.
8. `/adicionarcurso/`:
    - Adição de novos cursos.
9. `/adicionarturma/`:
    - Adição de novas turmas.
10. `/adicionaraluno/`:
    - Registro de alunos.

---

**InterfacesFrontend HTML & CSS**:
- Estrutura estilizada com **Bootstrap** e componentes interativos.
- Botões de adição e exclusão para gerenciar entidades.
**JavaScript (AJAX)**:
- Carregamento dinâmico de avisos com tratamento de erros.
- Interface renderiza a dinâmica, com botões de edição e exclusão.

---

**Exemplo de Funcionalidade**

**Carômetro**

Fluxo:

- Acessa `/carometro/` para listar cursos.
- Exclusão de cursos e turmas com interatividade.
- Seleciona um curso para visualizar as turmas (`/carometro2/`) e os alunos (`/carometro3/`).

**Mural de Avisos**

Fluxo:

- A interface renderiza avisos do banco.
- Os botões tem a função de editar e excluir avisos.

---

**Estilo de Código**

**DRY**: Reaproveitamento de métodos e classes.
**Segurança**:
- Validação de dados nos formulários.
- Hashing de senhas com `make_password`.
**Boas Práticas Django**:
- Uso de `querysets` para interações otimizadas. é uma coleção de objetos de um modelo que pode ser recuperada do banco de dados. Ele é usado para realizar consultas, filtrar, ordenar e manipular os dados armazenados.
- Modularidade entre views, templates e modelos.
