# DPS832-eng-economica

Repositório de estudos de Engenharia Econômica utilizando Jupyter Notebook

## Ferramentas

* Fluxo de Caixa:
  * [Fluxo de Conversões e Equivalências](fluxo.ipynb)
* Análise de Investimento:
  * [TIR - Taxa Interna de Retorno](tir.ipynb)
  * [VPL - Valor Presente Líquido](vpl.ipynb)
  * [VAUE - Valor Anual Uniforme Equivalente](vaue.ipynb)

## Como Usar

Baixando o repositório completo e executando os arquivos `.ipynb` através do `Jupyter Notebook` instalado e configurado na própria máquina ou importando-os para o [Google Colab](https://colab.research.google.com/) e executando-os na nuvem sem realizar nenhuma configuração adicional.

## Pré-Requisitos

Somente siga esses passos se for executar localmente, desconsiderar se estiver usando o [Google Colab](https://colab.research.google.com/)).

Para instalar o pacote numpy-financial, que é utilizado nos métodos de Análise de Investimentos, basta executar o comando:

    pip install numpy-financial

ou, se você estiver usando o Anaconda, basta executar:

    conda install -c conda-forge numpy-financial

(Código testado e rodando com o Python 3.9.7, via Anaconda)

## Exemplo de Uso

### Fluxo de Caixa

Métodos de conversão de valores ao longo do tempo para formatos diferentes de fluxo de caixa.

Exemplo de uso:

    valor_presente: float = 1000
    taxa: float = 0.08
    periodo: int = 12

    v_futuro: float = obter_f_com_p(valor_presente, taxa, periodo)
    print("Valor Futuro:", round(v_futuro, 2))

Saída:

    Valor Futuro: 2518.17

### Análise de Investimentos

Métodos para realizar análise de investimentos de três formas diferentes.
  
#### Exemplo de uso com TIR

    # investimento A
    inv_a = Investimento(
        fluxo_caixa=[
            -100,
            55, 55, 55, 55, 55 - 200,
            70, 70, 95, 95, 95
        ])

    # investimento 2
    inv_b = Investimento(
        fluxo_caixa=[
            -175,
            58, 58, 65, 65, 65,
            95, 95, 95, 95, 95
        ])

    comparar_invest_via_tir(inv_a, inv_b)

Saída:

    Comparação de investimentos considerando TIR.
    Investimento 1:  42.42%
    Investimento 2:  36.49%
    Melhor investimento, considerando maior valor TIR é:  42.42%

#### Exemplo de uso com VPL

    # investimento a
    inv_a = Investimento(
        taxa=0.15,
        fluxo_caixa=[
            -103,
            30, 35, 32, 28, 37
        ])

    # investimento b
    inv_b = Investimento(
        taxa=0.18,
        fluxo_caixa=[
            -103,
            30, 35, 32, 28, 37
        ])

    comparar_invest_via_vpl(inv_a, inv_b)

Saída:

    Comparação de investimentos com mesmo período de tempo (5) considerando VPL.
    Investimento 1:  5.0
    Investimento 2:  -2.35
    Melhor investimento, considerando maior valor de VPL é:  5.0

#### Exemplo de uso com VAUE

    # investimento 1
    inv_1 = Investimento(
        taxa=0.3,
        fluxo_caixa=[
            -14_000,
            5_000, 5_000, 5_000, 5_000, 5_000, 5_000, 5_000
        ])

    # investimento 2
    inv_2 = Investimento(
        taxa=0.3,
        fluxo_caixa=[
            -18_000,
            6_500, 6_500, 6_500, 6_500, 6_500, 6_500, 6_500
        ])

    comparar_invest_via_vaue(inv_1, inv_2)

Saída:

    Comparação de investimentos considerando VAUE.
    Investimento 1:  3.77%
    Investimento 2:  76.27%
    Melhor investimento, considerando maior valor VAUE é:  76.27%
