# VSCode-Django
Minhas configurações padrão para usar o Django no VSCode:

Use CTRL + SHIFT + P para abrir a busca por funções do programa e pesquise por ˋPreferências: Abrir as Configurações do Usuário (JSON)ˋ. Então seu arquivo json deve se parecer com o seguintte:
```json
{
  // salva automaticamente após cada alteração
  "files.autoSave": "afterDelay",

  // inclui uma coloração em respectivos caracteres de abertura e fechamento, como {}, [], ()
  "editor.bracketPairColorization.enabled": true,

  // inclui o django template na lista de linguagens que suportam abreviação
  "emmet.includeLanguages": {
    "django-html": "html",
    "**/templates/*.html": "django-html",
    "**/templates/*": "django-txt",
    "**/requirements{/**,*}.{txt,in}": "pip-requirements",
  },
  "[django-html]": {},

  // configura os templates django como linguagem html para associar atalhos, extensões e abreviações
  "files.associations": {
    "**/templates/*.html": "django-html",
    "**/templates/*": "django-txt",
    "**/requirements{/**,*}.{txt,in}": "pip-requirements",
    "**/*.html": "html",
    "*.html": "html",
    "*.js": "javascriptreact"
  },

  // configuras linhas verticais para marcar o estouro de 72 e 80 colunas
  "editor.rulers": [
    72,
    80
  ],

  // desabilita o minimapa do código ao lado direito de cada editor
  // "editor.minimap.enabled": false,

  // Autoriza a autoimportação de bibliotecas python nas sugestões do editor ao
  // digitat nomes de classes e funções ainda não carregadas no script
  "python.analysis.autoImportCompletions": true,
  "python.analysis.diagnosticMode": "workspace",
  "python.analysis.indexing": true,
  // deficne a profundidade da busca nos scripts internos das bibliotecas disponíveis
  "python.analysis.packageIndexDepths": [
   {
      "depth": 100,
      "includeAllSymbols": true,
      "name": ""
    },
  ],
}
```

## Extensões específicas para o django:

https://marketplace.visualstudio.com/items?itemName=thebarkman.vscode-djaneiro
https://marketplace.visualstudio.com/items?itemName=batisteo.vscode-django
https://marketplace.visualstudio.com/items?itemName=bigonesystems.django
https://marketplace.visualstudio.com/items?itemName=MaxChamps.django-commands
https://marketplace.visualstudio.com/items?itemName=Pachwenko.django-test-runner
https://marketplace.visualstudio.com/items?itemName=shamanu4.django-intellisense


## Extensões que eu uso para aumentar a produtividade (não segue ordem de relevância):

1: ![Auto Rename Tag](https://marketplace.visualstudio.com/items?itemName=formulahendry.auto-rename-tag) 	->	 Quando se tem um par de tags html (ou xml e similares) como `<tag></tag>` e ocorre mudança no nome de uma, a outra é automaticamente renomeada com o texto correspondente.

2: ![Better Comments](https://marketplace.visualstudio.com/items?itemName=aaron-bond.better-comments)	->	Permite realçar, em cores, diferentes tipos de comentários para facilitar o desenvolvimento em equipe e a fácil identificação de referências

3: ![Error Lens](https://marketplace.visualstudio.com/items?itemName=usernamehw.errorlens)	->	destaca erros e avisos e torna mais fácil sua detecção e tratamento

4: ![Local History](https://marketplace.visualstudio.com/items?itemName=xyz.local-history)	->	Salva constantemente backups das edições no código em arquivos na pasta raiz_do_projeto/.history

5: ![Git Lens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens)	->	Exibe informações relevantes sobre edições no arquivo, autores, commits que trouxeram determinadas modificações

6: ![Jinja](https://marketplace.visualstudio.com/items?itemName=wholroyd.jinja)	->	Auxilia na detecção e realce de código específico do django template

7: ![Thunder Client](https://marketplace.visualstudio.com/items?itemName=rangav.vscode-thunder-client)	->	Permite fazer requisições get, post etc diretamente dentro o editor, muito semelhante ao app Insomnia

8: ![Live Share](https://marketplace.visualstudio.com/items?itemName=MS-vsliveshare.vsliveshare)	->	permite compartilhamente de código em tempo real com possibilidade de edição simultânea entre membros da live

9: ![Reload](https://marketplace.visualstudio.com/items?itemName=natqe.reload)	->	permite reiniciar o vscode para aplicar mudanças ou retomar o controle após falhas

10: ![Python Ident](https://marketplace.visualstudio.com/items?itemName=KevinRose.vsc-python-indent)		->	Identa automaticamente linhas de código após quebras de linha

11: [Markdown Preview](https://marketplace.visualstudio.com/items?itemName=shd101wyy.markdown-preview-enhanced)	->	Permite pré-visualizar arquivos readme diretamente no editor

12: [autoflake python]()	->	remove importações e variáveis desnecessárias e não utilizadas 

13: [Bootstrap 5 Snippet Extension](https://marketplace.visualstudio.com/items?itemName=swumplurd.bootstrap-5-snippets-extension)	->	oferece atalhos para criação de itens do bootstrap 5


## Tema que eu uso e recomendo

![Hyper Dark Material](https://marketplace.visualstudio.com/items?itemName=kuscamara.hyper-dark-material)


## Configurações de depuração para o django
Abra a seção de depuração `CTRL + SHIFT + D` e clique no ícone da engrenagem ou `CTRL + SHIFT + P` e pesquise pelo comando `Abrir 'launch.json'`. Seu arquivo deve se parecer com o seguinte:
```json
{
    // Use o IntelliSense para saber mais sobre os atributos possíveis.
    // Focalizar para exibir as descrições dos atributos existentes.
    // Para obter mais informações, acesse: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Django",
            "type": "python",
            "request": "launch",
            "console": "integratedTerminal",
            "program": "${workspaceFolder}/project/manage.py",
            "args": [
                "runserver",
                // "8000"
                // caso queira incluir outros argumentos ou uma determinada porta para o servidor cada nova linha significa um novo argumento
            ],
            "django": true,
            "justMyCode": true // depurar apenas meu código ou incluir código interno do django + bibliotecas
        },
    ]
}
```
