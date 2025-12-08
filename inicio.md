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
