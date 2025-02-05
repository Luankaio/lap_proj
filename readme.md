# Projeto Livraria

Este projeto é uma API em Django para gerenciar livros e autores, apresentando:

- **CRUD de Livros e Autores**  
- **Paginação e Filtros** (por título e autor)  
- **Relacionamento muitos-para-muitos** (vários autores para um livro)  
- **Banco de Dados** (PostgreSQL)
- **Dockerização** (Dockerfile + docker-compose)

## Estrutura e Arquivos Principais

- `lapisco_api/models.py`:
  - Modelos `Author` e `Book` (com ManyToManyField).
- `lapisco_api/serializers.py`:
  - Serializadores para `Author` e `Book`.
- `lapisco_api/views.py`:
  - ViewSets para operações CRUD (incluindo filtros).
- `app/urls.py`:
  - Rotas para livros, autores e documentação.
- `requirements.txt`:
  - Dependências do projeto.
- `docker-compose.yml` e `Dockerfile`:
  - Configuração de contêineres (Django + PostgreSQL).

## Pré-requisitos

- Python 3.9+  
- PostgreSQL  
- Instalar as dependências via `requirements.txt`.

## Como Executar (Local)

1. Criar virtualenv e instalar dependências:
   ```bash
   python -m venv venv
   source venv/bin/activate
   pip install -r requirements.txt
2. Criar e aplicar migraçoes
    ```bash
    docker compose run --rm app sh -c "python manage.py makemigrations lapisco_api && python manage.py migrate"
3. Build e up pra rodar
    ```bash
    docker compose build
    docker compose up
4. Acessar essa url
    http://localhost:8000.
## Filtros e Paginação
    
1. Para listar livros, paginar e filtrar:
    ```bash
    GET /api/books/?page=2&title=Exemplo
