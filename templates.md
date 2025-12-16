# Templates
```python
from django.shortcuts import render
# render vai renderizar os documentos html, css etc.
# em views vai ser:
def home(request):
  return render(request, 'home.html')
  # vai renderizar o documento html
```
- entretanto, isso vai dar erro usando no nosso exemplo, que temos o projeto principal e o app receitas, pq o django nao sabe que existe a pasta templates dentro de recipes, na verdade ele nem sabe da existencia de recipes, entao
- precisamos ir em settings na pasta raiz e adicionar recipes em INTALLED_APPS, apenas fazendo o 'recipes', na ultima linha
## A função render
- ela recebe a request, o nome do template, e etc, usa uma funcao loader que vai renderizar para string o conteudo e retorna como http response.
- o context: é basicamente onde passaremos variáveis para serem usadas dentro dos templates, no html e etc.
