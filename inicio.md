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

## apps
- apps em django basicamente servem para você dividir o seu projeto em partes que sejam reutilizáveis para outras partes do código.
- para saber se seu app está feito do jeito certo, pergunte a si mesmo o que ele faz, se na explicação você usar "e", seu app está com muitas responsabilidades, por exemplo, o app de comentario serve para postar comentarios E logar conta E enviar email
- para criar um app, rode:
```python
python manage.py startapp nome_app
```
- logo, tenho o projeto inicial, e temos o app recipes, em recipes/views tenho a função home, para colocar na rota, farei:
```python
# em site/urls:

from recipes.views import home # lembre-se de importar a função da views do app.
urlpatterns = [...
  ...
  path('', home),
  ]
```
- **CLEAN CODE**: agora, temos uma funcionalidade muito boa para deixar o código do app principal/projeto, limpo, é a partir do uso da função include do django.urls, o que faremos é basicamente, criaremos o arquivo urls.py no app recipes, e nele faremos o esquema de rotas:
```python
# em recipes.urls
from django.urls import path
from django.views import home, contato, sobre

urlpatterns = [
  path('', home),
  path('contato/', contato),
  path('sobre/', sobre),
]
```
```python
# em projeto.urls
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
  path('admin/', admin.site.urls),
  path('', include('recipes.urls')) # o '' em branco serve para indicar que todas as urls do include vao ficar DENTRO da home, que seria o ''
  # se eu quisesse, por exemplo, que todas essas urls ficassem em meusite.com/receitas, faria:
  # path('receitas/', include('recipes.urls')),
]
```
- desse modo, vou meio que 'aninhando' as urls.
