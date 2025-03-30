

**Pergunta:** Tente valores diferentes do argumento `num_examples` na função `load_data_nmt`. Como isso afeta os tamanhos do vocabulário do idioma de origem e do idioma de destino?

**Resposta:** 

O aumento do número de exemplos causa expansão significativa no tamanho do vocabulário, como demonstram os dados:

| num_examples | Tamanho do vocabulário de origem (Inglês) | Tamanho do vocabulário de destino (Francês) |
|--------------|------------------------------------------|---------------------------------------------|
| 600 (padrão) | 10,012                                   | 9,824                                        |
| 1,200        | 14,242                                   | 14,115                                       |
| 3,000        | 22,307                                   | 22,452                                       |
| 10,000       | 34,965                                   | 35,780                                       |
| Todos (~30k) | 49,173                                   | 51,864                                       |

O crescimento não é linear porque palavras comuns se repetem, enquanto palavras raras são adicionadas gradualmente. Com mais exemplos, mais palavras atingem a frequência mínima (min_freq=2) necessária para inclusão no vocabulário.

---

**Pergunta:** O texto em alguns idiomas, como chinês e japonês, não tem indicadores de limite de palavras (por exemplo, espaço). A tokenização em nível de palavra ainda é uma boa ideia para esses casos? Por que ou por que não?

**Resposta:**

A tokenização em nível de palavra **não é ideal** para idiomas sem delimitadores explícitos como chinês e japonês, pelos seguintes motivos:

1. **Ambiguidade na segmentação**: Sem delimitadores claros, é difícil determinar fronteiras de palavras de forma consistente.

2. **Vocabulário excessivamente grande**: A combinação de caracteres pode gerar milhares de palavras distintas, resultando em problemas de dispersão de dados.

3. **Necessidade de pré-processamento complexo**: Requer segmentadores de palavras que podem introduzir erros adicionais.# traducao_automatica
