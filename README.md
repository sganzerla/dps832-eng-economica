# DPS832-eng-economica

Repositório de estudos de Engenharia Econômica utilizando Jupyter Notebook

## Como Usar

Baixando o repositório completo e executando os arquivos `.ipynb` através do `Jupyter Notebook` instalado e configurado na própria máquina ou importando-os para o [Google Colab](https://colab.research.google.com/)) e executando-os na nuvem sem realizar nenhuma configuração adicional.

## Pré-Requisitos

Somente siga esses passos se for executar locamente, desconsiderar se estiver usando o [Google Colab](https://colab.research.google.com/)).

Para instalar o pacote numpy-financial, que é utilizado nos métodos de Análise de Investimentos, basta executar o comando:

    pip install numpy-financial  (ou pip3)

ou, se você estiver usando o Anaconda, basta executar:

    conda install -c conda-forge numpy-financial

(Código testado e rodando com o Python 3.9.7, via Anaconda)

## Ferramentas Disponíveis

Abaixo link para 4 recursos disponíveis para uso em duas categorias diferentes.

### 1 - Fluxo de Caixa

Métodos de conversão de valores ao longo do tempo para formatos diferentes de fluxo de caixa.

* [1-1 Conversões e Equivalências](fluxo.ipynb)

Exemplo de uso:

    valor_presente: float = 1000
    taxa: float = 0.08
    periodo: int = 12

    v_futuro: float = obter_f_com_p(valor_presente, taxa, periodo)
    print("Valor Futuro:", round(v_futuro, 2))

Saída:

    Valor Futuro: 2518.17

### 2 - Ánalise de Investimentos

Métodos para realizar análise de investimentos de três formas diferentes.

* [2-1 TIR - Taxa Interna de Retorno](tir.ipynb)
* [2-2 VPL - Valor Presente Líquido](vpl.ipynb)
* [2-3 VAUE/CAUE - Valor (ou Custo) Anual Uniforme Equivalente](vaue.ipynb)
  
Exemplo de uso usando TIR:

    investimento1: Investimento = Investimento(
        taxa=0.0, fluxo_caixa=[-150, 73, 73, 73])

    investimento2: Investimento = Investimento(
        taxa=0.0, fluxo_caixa=[-130, 52, 52, 52])

    comparar_invest_via_tir(investimento1, investimento2)

Saída:

    Comparação de investimentos considerando TIR.
    Investimento 1:  21.6
    Investimento 2:  9.7
    Melhor investimento, considerando maior valor TIR é:  21.6%
