# Analisador de Vendas e Detecção de Discrepâncias

Este projeto consiste em um script Python desenvolvido para realizar a análise estatística básica de entradas de vendas, validando os valores contra limites de segurança e identificando possíveis anomalias nos dados.

## 🚀 Funcionalidades

O script processa três valores de venda e executa as seguintes operações:

1.  **Cálculo de Médias e Medianas**: Determina a média aritmética e a mediana dos valores informados.
2.  **Monitoramento de Limite de Segurança**: Compara a média das vendas com um limite global (`LIMITE_SEGURANCA`).
3.  **Quarentena e Atualização**: Caso a média ultrapasse o limite, o sistema entra em estado de "Quarentena" e permite que o usuário atualize o limite global em tempo de execução.
4.  **Detecção de Discrepâncias (Outliers)**:
    * **Regra de Média**: Identifica se alguma venda individual é 5x maior que a média.
    * **Regra de Mediana**: Identifica se uma venda é 3x maior ou 3x menor (1/3) que a mediana do conjunto.

## 🛠️ Detalhes Técnicos

### Lógica de Detecção
O script utiliza as seguintes fórmulas para sinalizar revisões manuais:

* **Suspeita por Média**: $venda_n \geq 5 \times \text{media}$
* **Suspeita por Mediana**: $venda_n \geq 3 \times \text{mediana}$ ou $venda_n \leq \frac{\text{mediana}}{3}$

### Tipagem de Dados
O sistema garante a integridade dos cálculos convertendo as entradas do usuário para o tipo `float`, permitindo precisão decimal nas operações financeiras.

## 📋 Exemplo de Uso

Ao executar o script, o fluxo de interação segue este padrão:

```text
Venda 1: R$1500.00
Venda 2: R$12000.00
Venda 3: R$1400.00

--- RESULTADO ---
Média: 4966.67 | tipo: float
Limite: 10000 | tipo: int

REVISÃO MANUAL: Venda 2 suspeita
