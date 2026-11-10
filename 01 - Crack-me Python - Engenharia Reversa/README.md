# Crack-me Python — Engenharia Reversa

> **Categoria:** Engenharia Reversa  
> **Dificuldade:** Iniciante  
> **Arquivo analisado:** [`crackme_gen.py`](./crackme_gen.py)

## Objetivo

O objetivo desta atividade é analisar um programa em Python e descobrir a informação secreta escondida no código.

## Análise inicial

Ao abrir o arquivo, encontrei uma variável chamada `bezos_cc_secret`:

```python
bezos_cc_secret = "24256>JL`>0c0Abc?FE02a_53e7fe7af5gN"
```

O valor não está legível, então provavelmente foi codificado.

Mais abaixo existe uma função chamada `decode_secret()`:

```python
def decode_secret(secret):
    """ROT47 decode"""

    rotate_const = 47
    decoded = ""

    for c in secret:
        index = alphabet.find(c)
        original_index = (index + rotate_const) % len(alphabet)
        decoded = decoded + alphabet[original_index]

    print(decoded)
```

O comentário informa que ela decodifica textos usando **ROT47**. Porém, no final do programa, apenas a função `choose_greatest()` é executada:

```python
choose_greatest()
```

Isso significa que a função necessária para revelar o segredo já está pronta, mas não foi chamada. A função `choose_greatest()` serve como distração para o desafio.

## Resolução

Para revelar o segredo, comentei a última linha e chamei `decode_secret()` passando a variável secreta:

```python
# choose_greatest()
decode_secret(bezos_cc_secret)
```

Depois, executei o arquivo no terminal:

```bash
python3 crackme_gen.py
```

O programa aplicou ROT47 ao texto escondido e mostrou a flag:

```text
academy{1m_4_p34nut_a20db6f76f27d8}
```

## Flag

```text
academy{1m_4_p34nut_a20db6f76f27d8}
```

## Conclusão

Nesta atividade, aprendi que engenharia reversa também pode começar com uma leitura cuidadosa do código. A informação secreta estava codificada com ROT47, mas o próprio programa já possuía a função necessária para decodificá-la.

Os pontos mais importantes foram:

- identificar a variável que guardava o segredo;
- ler os nomes, comentários e funções do programa;
- perceber que `decode_secret()` não estava sendo executada;
- chamar a função com o valor correto;
- executar o arquivo e verificar o resultado.
