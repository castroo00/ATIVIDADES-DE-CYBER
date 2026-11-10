# MOD 26 — Crypto

> **Categoria:** Criptografia  
> **Dificuldade:** Iniciante  
> **Arquivo analisado:** [`values.txt`](./values.txt)

## Objetivo

O desafio fornece um texto codificado e pergunta se sabemos o que é ROT13. O objetivo é decodificar o conteúdo do arquivo e encontrar a flag.

## Análise inicial

Ao abrir `values.txt`, encontrei o seguinte texto:

```text
npnqrzl{arkg_gvzr_V'yy_gel_2_ebhaqf_bs_ebg13_5p5s5o36}
```

O ROT13 substitui cada letra pela letra que está 13 posições à frente no alfabeto. Por exemplo:

```text
A vira N
B vira O
N vira A
O vira B
```

O nome **MOD 26** está relacionado às 26 letras do alfabeto. Ao ultrapassar a letra `Z`, a contagem volta para `A`. Como 13 é metade de 26, o mesmo processo serve para codificar e decodificar.

Números, chaves, espaços e símbolos não são alterados pelo ROT13.

## Resolução

No terminal Linux, utilizei o comando `tr` para trocar as letras pelas correspondentes em ROT13:

```bash
tr 'A-Za-z' 'N-ZA-Mn-za-m' < values.txt
```

O comando retornou:

```text
academy{next_time_I'll_try_2_rounds_of_rot13_5c5f5b36}
```

Também seria possível usar um decodificador ROT13, como o CyberChef, colando o conteúdo do arquivo e selecionando a operação `ROT13`.

## Flag

```text
academy{next_time_I'll_try_2_rounds_of_rot13_5c5f5b36}
```

## Conclusão

Nesta atividade, aprendi como funciona o ROT13, uma forma simples de substituir letras. Ele não é considerado seguro para proteger informações importantes, mas é útil para entender os conceitos iniciais de criptografia e cifra de substituição.

Os principais pontos foram:

- reconhecer que o texto estava em ROT13;
- entender o deslocamento de 13 posições;
- perceber que aplicar ROT13 novamente revela o texto original;
- usar o comando `tr` para fazer a decodificação.
