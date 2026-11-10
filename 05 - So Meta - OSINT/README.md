# So Meta — OSINT

> **Categoria:** OSINT  
> **Dificuldade:** Iniciante  
> **Arquivo analisado:** `pico_img.png`

## Objetivo

O desafio fornece uma imagem e pergunta se existe alguma informação escondida nela. As dicas falam sobre “meta” e metadados.

## O que são metadados?

No contexto de arquivos, **meta** significa uma informação sobre o próprio arquivo. Os metadados podem guardar, por exemplo:

- nome do autor;
- data de criação;
- programa utilizado;
- modelo da câmera;
- localização;
- comentários e descrições.

Essas informações não precisam aparecer quando abrimos a imagem normalmente.

## Resolução

Primeiro, abri a imagem. Ela mostra apenas um desenho circular e não possui nenhuma flag visível.

Em seguida, usei o `exiftool` para verificar seus metadados:

```bash
exiftool pico_img.png
```

Entre as informações exibidas, o campo `Artist` chamou a atenção:

```text
Artist : academy{s0_m3ta_45015e26}
```

Também é possível encontrar esse texto com o comando `strings`:

```bash
strings pico_img.png | grep academy
```

## Flag

```text
academy{s0_m3ta_45015e26}
```

## Conclusão

Nesta atividade, aprendi que um arquivo pode guardar informações que não aparecem em seu conteúdo visível. Por isso, verificar metadados é um passo importante durante a análise de imagens.

Os pontos principais foram:

- entender o significado de metadados;
- não procurar somente na parte visível da imagem;
- usar `exiftool` para examinar os campos do arquivo;
- identificar a flag no campo `Artist`.
