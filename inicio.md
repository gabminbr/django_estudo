# Configurações iniciais
- criar o ambiente virtual com 'python3 -m venv venv', e ativar ele com source /venv/bin/activate, desativa com 'deactivate'.
- lembre-se também de usar o cntrll + shift + p e selecionar o interpretador certo (o que tiver o venv)

# Django
## instalando django
- certifique-se que está dentro do seu ambiente virtual
- rode pip install django
## gitignore
- o arquivo *.gitignore* deve ter em todo projeto, basta pesquisar na internet modelos de gitignore para django em especifico.

## iniciando o projeto
- primeiro, caso queira ver comandos, use o *django-admin --help* no terminal.
- comando para iniciar o projeto:
```bash
django-admin startproject nome-do-projeto .
```
- desvendando o que rodamos: o startproject é autointuitivo, o ponto basicamente vai fazer com que seja criado o projeto no diretorio atual, se nao usarmos o '.', o projeto vai ser criado dentro de uma pasta no diretorio atual.
- para iniciar o servidor:
```bash
python manage.py runserver
```
- lembre-se sempre: use o ambiente virtual.

## urls
- o arquivo urls é como uma recepção, a função dele é: ler o endereço que o usuário digitou e decidir qual função Python deve ser executada
- a função path recebe 3 argumentos principais
```python
path('artigos/<int:id>/', views.detalhe_artigo, name='detalhe')
```
- route (primeiro argumento): é o padrão da URL (o endereço), exemplo 'sobre/'
- a view: é a função que é chamada se a URL bater com o padrão acima, o django vai chamar automaticamente essa função e passar a request.
- o name: é o apelido interno da URL, ajuda tipo em vez de escrever /artigos/5/ hardcoded (fixo) no seu código HTML, você usa uma tag do Django tipo {% url 'detalhe' 5 %}
