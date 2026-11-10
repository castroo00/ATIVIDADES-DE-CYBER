# Information — Forense

> **Categoria:** Forense  
> **Dificuldade:** Iniciante  
> **Arquivo analisado:** `cat.jpg`

## Objetivo

O desafio entrega uma imagem e pergunta se conseguimos encontrar uma flag escondida nela. A dica informa que arquivos podem ser alterados de maneira secreta.

## Análise inicial

Ao abrir `cat.jpg`, vemos apenas uma fotografia de dois gatos. Não existe nenhuma flag visível na imagem.

Uma imagem pode guardar informações além dos seus pixels. Essas informações são chamadas de **metadados** e podem incluir autor, data, localização, programa utilizado e outros campos.

## Resolução

Para visualizar os metadados da imagem, utilizei o `exiftool`:

```bash
exiftool cat.jpg
```

Entre os resultados, o campo de licença apresentava este valor:

```text
YWNhZGVteXt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9
```

O formato e o conjunto de caracteres são comuns em textos codificados em **Base64**. Para decodificá-lo, usei:

```bash
echo "YWNhZGVteXt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9" | base64 -d
```

O resultado foi:

```text
academy{the_m3tadata_1s_modified}
```

## Flag

```text
academy{the_m3tadata_1s_modified}
```

## Conclusão

Nesta atividade, aprendi que uma imagem pode esconder informações nos metadados, mesmo quando nada diferente aparece visualmente.

Os principais pontos foram:

- verificar os metadados com `exiftool`;
- identificar um texto codificado em Base64;
- usar `base64 -d` para recuperar a informação original;
- não analisar somente o conteúdo visível de um arquivo.
