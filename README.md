# TP2

# Alunos:

- Edson Pimenta de Almeida
- Luís Augusto Starling Toledo
- Luiz Gabriel Milione Assis
- 
# Descrição do trabalho:

  O TP2 é uma adição ao trabalho do TP1. Seu objetivo é criar as classes ArquivoTarefa e ArquivoCategoria que, alem de fazer o CRUD genérico, também conseguem atualizar um índice indireto, uma vez que uma tarefa possui uma categoria, necessitando de um índice secundário. O índice é criado em uma árvore B+.
  
# Classes:

- Arquivo
- ArquivoCategoria
- ArquivoTarefa
- ArvoreBMais
- ParIdId
- ParNomeId
- HashExtensivel
- ParIdEndereço
- MenuCategorias
- MenuTarefas
- Categoria
- Tarefa
- Main
- 
# Interfaces:

- Registro
- RegistroArvoreBMais
- RegistroHashExtensivel
- 
# Classe Arquivo

Responsável pelo CRUD de objetos do tipo genérico T, que devem estender a interface Registro.

# Atributos

int representando o tamanho do cabeçalho.
RandomAccessFile arquivo: o arquivo a ser manipulado.
String nome_arquivo: nome do arquivo a ser manipulado.
Constructor construtor: construtor da classe T.
HashExtensivel indice_direto: arquivo com índices diretos.

# Métodos

Construtor: Recebe uma String e um Constructor para abrir ou criar o arquivo RandomAccessFile e o construtor da classe T. Inicializa o cabeçalho com o número 0, se necessário.
create: Recebe um objeto T, atribui um novo ID, escreve o registro no arquivo e o índice direto. Retorna o ID.
read: Recebe o ID e retorna o objeto ou null, verificando a validade da lápide.
delete: Recebe o ID e marca o registro como inválido, retornando verdadeiro ou falso.
update: Atualiza o registro no arquivo, comparando o tamanho do novo registro com o original. Se o tamanho for maior, o novo registro é escrito no final.
close: Fecha o arquivo.

# Classe Aquivo Categoria

Extende a classe Arquivo para  fazer o CRUD de objetos do tipo Categoria. Possui os atributos:
Arquivo<Categoria> arq_categoria: Banco de dados dos objetos Categoria
ArvoreBMais<ParNomeId> indice_indireto_nome: Árvore B+ responsavel por armazenar os pares nome_categoria e id_categoria juntamente com o seu endereço no BD. Um índice indireto.

# Construtor: 
Inicializa o arquivo de categorias e o índice indireto
# int create: 
Recebe um objeto Categoria, que é criado no banco de dados e no índice indireto. Retorna o ID criado.
# Categoria read:
Recebe uma String e pesquisa uma categoria no Banco de dados com o nome correspondente. Retorna um objeto Categoria
# boolean delete:
Recebe uma String e deleta no banco de dados a Categoria com o nome correspondente. Retorna verdadeiro para uma operação bem sucedida ou falso para uma operação falha.
# void list:
Imprime todas as categorias presentes no banco de dados.
# boolean update:
Recebe uma categoria já existente no Banco de dados e atualiza seus registros. Retorna verdadeiro para uma operação bem sucedida ou falso para uma operação falha.

# Classe Arquivo Tarefa

Extende a classe Arquivo para  fazer o CRUD de objetos do tipo Tarefa. Possui os atributos:
Arquivo<Tarefa> arq_tarefa: Banco de dados dos objetos Tarefa
ArvoreBMais<ParIdId> indice_indireto_id: Indece indireto, armazenando pares id_categoria e id_tarefa em uma Árvore B+

# Construtor:
Inicializa o arquivo de tarefas e o índice indireto
# int create:
Recebe um objeto Tarefa, que é criado no banco de dados e no índice indireto. Retorna o ID criado.
# ArrayList<Tarefa> readAll:
Lê todas as tarefas com base no id_categoria pela Hash, retorna um ArrayList com todas as tarefas.
# boolean delete:
Deleta uma tarefa e remove do índice indireto. Retorna verdadeiro para uma operação bem sucedida ou falso para uma operação falha.
# boolean update:
Recebe uma tarefa já existente no Banco de dados e atualiza seus registros. Retorna verdadeiro para uma operação bem sucedida ou falso para uma operação falha.

# Classe ArvoreBMais:
Serve como índire indireto de objetos T que implementam a interface RegistroArvoreBMais.

#Métodos:
- Create
- Read
- Delete

# Classe ParIdId:
Esta classe representa um objeto para uma entidade Id, Id que será armazenado em uma árvore B+.

# Métodos:
- Construtor
- Getters
- Setters
- clone
- size
- compareTo
- toString
- toByteArray

# Classe ParNomeId:
Esta classe representa um objeto para uma entidade Nome, Id que será armazenado em uma árvore B+.

# Métodos:
- Construtor
- Getters
- Setters
- clone
- size
- compareTo
- toString
- toByteArray

# Classe HashExtensivel
Serve como índice direto para objetos T que implementem a interface RegistroHashExtensivel.

Métodos
- create
- read
- update
- delete

# Classe ParIDEndereco
Implementa a interface RegistroHashExtensivel, com os atributos:

- int id
- long endereço

# Métodos
- Construtores
- getters
- setters
- toByteArray
- fromByteArray

# Classe MenuCategorias:
Classe responsável por interagir com o usuário e o banco de dados de Categoria

# Atributos:
- ArquivoTarefa arq_tarefa: Banco de dados com as tarefas
- ArquivoCategoria arq_categoria: Banco de dados com as categorias
- Scanner sc: Scanner responsável por ler os inputs do usuário 

# Métodos:
- void menu: Mostra as opções para o usuário escolher. Chama as funções responsáveis por fazer as ações escolhidas pelo usuário.
- void buscarCategoria: Lê do usuário uma categoria e pesquisa no banco de dados. Imprime o resultado na tela.
- void incluirCategoria: Lê do usuário uma categoria e a armazena no Banco de dados.
- void alterarCategoria: Lê do usuário uma categoria, caso exista atualiza com novas informações providas pelo usuário, a armazena no Banco de dados as novas informações.
- void excluirCategoria: Lê do usuário uma categoria, caso exista deleta do banco de dados.

# Classe MenuTarefas:
Classe responsável por interagir com o usuário e o banco de dados de Tarefa

# Atributos:
- ArquivoTarefa arq_tarefa: Banco de dados com as tarefas
- ArquivoCategoria arq_categoria: Banco de dados com as categorias
- Scanner sc: Scanner responsável por ler os inputs do usuário 

# Métodos:
- void menu: Mostra as opções para o usuário escolher. Chama as funções responsáveis por fazer as ações escolhidas pelo usuário.
- void buscarTarefa: Lê do usuário uma tarefa e pesquisa no banco de dados. Imprime o resultado na tela.
- void incluirTarefa: Lê do usuário uma tarefa e a armazena no Banco de dados.
- void alterarTarefa: Lê do usuário uma tarefa, caso exista atualiza com novas informações providas pelo usuário, a armazena no Banco de dados as novas informações.
- void excluirTarefa: Lê do usuário uma tarefa, caso exista deleta do banco de dados.

# Classe Tarefa
Representa uma tarefa com os seguintes atributos:

Nome (String)
Data de criação e conclusão (LocalDate)
Status (String)
Prioridade (byte)

# Métodos
construtores
getters
setters
toByteArray
fromByteArray
toString

# Classe Categoria
Representa uma Categoria com os atributos:
- int id
- String nome

# Métodos:
- Costrutores
- Getters
- Setters
- toByteArray
- fromByteArray

# Interface Registro
Obriga que as classes que implentem a interface possuam:
-  public void setId(int i)
-  public int getId()
-  public byte[] toByteArray() throws IOException
-  public void fromByteArray(byte[] b) throws IOException

# Interface RegistroArvoreBMais
Obriga as classes a implementarem:
- public short size()
- public byte[] toByteArray() throws IOException
- public void fromByteArray(byte[] ba) throws IOException
- public int compareTo(T obj)
- public T clone()

# Interface RegistroHashExtensivel
Obriga as classes a implementarem:
- public int hashCode()
- public short size()
- public byte[] toByteArray() throws IOException
- public void fromByteArray(byte[] ba) throws IOException

# Classe Main
Responsavel por rodar a aplicação, possui a função main que interage com o usuário.

# Relato dos Alunos
- Todos os requisitos foram implementados sem problemas ou dificuldades.
- Os resultados foram alcançados.

# Perguntas:
- O CRUD (com índice direto) de categorias foi implementado? SIM
- Há um índice indireto de nomes para as categorias? SIM
- O atributo de ID de categoria, como chave estrangeira, foi criado na classe Tarefa? SIM
- Há uma árvore B+ que registre o relacionamento 1:N entre tarefas e categorias? SIM
- É possível listar as tarefas de uma categoria? SIM
- A remoção de categorias checa se há alguma tarefa vinculada a ela? SIM
- A inclusão da categoria em uma tarefa se limita às categorias existentes? SIM
- O trabalho está funcionando corretamente? SIM
- O trabalho está completo? SIM
- O trabalho é original e não a cópia de um trabalho de outro grupo? SIM
