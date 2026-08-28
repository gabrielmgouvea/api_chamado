API de Chamados

Primeira versão de uma API REST para cadastro e consulta de chamados, desenvolvida com Python, FastAPI, Pydantic e Uvicorn. Nesta etapa, os dados são armazenados apenas em memória.

Tecnologias
Python
FastAPI
Pydantic
Uvicorn
Como executar

Clone ou abra o projeto e entre na pasta:

cd api_chamados


Crie e ative o ambiente virtual:

python -m venv .venv


No Windows:

.venv\Scripts\activate


No Linux/macOS:

source .venv/bin/activate


Instale as dependências:

pip install -r requirements.txt


Execute a aplicação:

uvicorn main:app --reload


A API estará disponível em:

http://127.0.0.1:8000


A documentação interativa pode ser acessada em:

http://127.0.0.1:8000/docs

Endpoints
Método	Rota	Descrição
GET	/	Verifica se a API está funcionando
GET	/chamados	Lista todos os chamados
POST	/chamados	Cadastra um novo chamado
GET	/chamados/{id}	Consulta um chamado pelo ID
GET	/chamados/status/{status_chamado}	Filtra chamados pelo status
Exemplo de criação

No POST /chamados, envie:

{
  "titulo": "Computador não liga",
  "descricao": "O computador não apresenta sinais de energia.",
  "prioridade": "alta"
}


Em caso de sucesso, a API retorna o status 201 Created e cria automaticamente um ID e o status inicial "aberto".

Validação

Os dados enviados no cadastro são validados pelo Pydantic. Os campos obrigatórios são:

titulo
descricao
prioridade

Caso algum campo seja removido ou enviado com formato inválido, a API retorna um erro de validação automaticamente.

Testes

Os principais testes podem ser realizados pela documentação /docs:

Verificar GET /.
Verificar GET /chamados inicialmente com uma lista vazia.
Criar um chamado com POST /chamados.
Consultar novamente GET /chamados.
Buscar o chamado criado com GET /chamados/1.
Buscar um ID inexistente, como GET /chamados/999, esperando 404.
Realizar um POST sem um campo obrigatório e verificar o erro de validação.
Responsabilidades
Uvicorn: executa o servidor e recebe as requisições HTTP.
FastAPI: define a aplicação, as rotas e o comportamento dos endpoints.
Pydantic: define e valida os dados recebidos.
Funções Python: implementam as operações de cadastro e consulta.
Dependências

As dependências do projeto estão registradas no arquivo requirements.txt, gerado com:

pip freeze > requirements.txt

Observação

Os chamados são armazenados em uma lista na memória. Portanto, os dados serão perdidos quando a aplicação for encerrada ou reiniciada.

Commit sugerido
implementa primeira api de chamados com fastapi
