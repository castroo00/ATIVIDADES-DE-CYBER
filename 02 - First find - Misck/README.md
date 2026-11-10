# First find — Misck

> **Categoria:** Misc  
> **Dificuldade:** Iniciante  
> **Arquivo recebido:** `files.zip`

## Objetivo

O objetivo desta atividade é descompactar o arquivo `files.zip`, procurar pelo arquivo chamado `uber-secret.txt` e ler seu conteúdo.

## Resolução

Primeiro, descompactei o arquivo ZIP em uma nova pasta:

```bash
unzip files.zip -d files_extraidos
```

- `unzip` descompacta o arquivo;
- `files.zip` é o arquivo que recebemos;
- `-d files_extraidos` coloca o conteúdo na pasta `files_extraidos`.

Depois, usei o comando `find` para procurar pelo nome exato do arquivo:

```bash
find files_extraidos -type f -name "uber-secret.txt"
```

O arquivo foi encontrado neste caminho:

```text
files_extraidos/files/adequate_books/more_books/.secret/deeper_secrets/deepest_secrets/uber-secret.txt
```

A pasta `.secret` começa com um ponto. No Linux, isso significa que ela fica oculta nas listagens comuns, mas o comando `find` ainda consegue pesquisá-la.

Por último, utilizei `cat` para mostrar o conteúdo do arquivo:

```bash
cat files_extraidos/files/adequate_books/more_books/.secret/deeper_secrets/deepest_secrets/uber-secret.txt
```

O resultado foi:

```text
academy{f1nd_15_f457_ab443fd1}
```

## Flag

```text
academy{f1nd_15_f457_ab443fd1}
```

## Conclusão

Nesta atividade, aprendi a descompactar arquivos e pesquisar arquivos pelo nome no terminal Linux. O comando `find` foi importante porque permitiu localizar rapidamente o arquivo dentro de várias pastas, incluindo uma pasta oculta.

Os principais comandos utilizados foram:

- `unzip` para descompactar o ZIP;
- `find` para localizar o arquivo;
- `cat` para ler seu conteúdo.
