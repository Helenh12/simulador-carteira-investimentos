# Simulador de Carteira de Investimentos

Planilha em Excel que simula uma carteira diversificada de acordo com o perfil do investidor.
A pessoa informa quanto consegue investir por mês, escolhe o perfil e o prazo, e a planilha
monta a carteira sugerida e projeta o patrimônio mês a mês.

Projeto desenvolvido como atividade de um curso de Excel.

> **Aviso:** simulação com fins didáticos, usando retornos hipotéticos para renda variável.
> Não é recomendação de investimento.

## Como usar

1. Baixe o arquivo em [`planilha/Simulador_Carteira_Investimentos.xlsx`](planilha/Simulador_Carteira_Investimentos.xlsx).
2. Abra no Excel 2021 ou Microsoft 365 (a planilha usa a função PROCX).
3. Na aba **Simulador**, preencha as células de fundo amarelo:
   - Aporte mensal (R$)
   - Patrimônio inicial (R$), que pode ficar em zero
   - Perfil do investidor (lista: Conservador, Moderado ou Arrojado)
   - Prazo da simulação, em meses (de 1 a 360)
4. A carteira sugerida, o resultado e o detalhe por ativo são calculados automaticamente.

## Estrutura da planilha

| Aba | O que faz |
|---|---|
| **Simulador** | Tela de entrada e resultados: carteira sugerida, total investido, patrimônio bruto e líquido |
| **Perfis** | Percentual de cada ativo por perfil (base da busca com PROCX) |
| **Premissas** | CDI, IPCA, rentabilidade de cada ativo e tabela regressiva de IR |
| **Projeção** | Cálculo mês a mês, até 360 meses |

## Perfis e ativos

| Ativo | Conservador | Moderado | Arrojado |
|---|---|---|---|
| Tesouro Selic | 30% | 15% | 5% |
| CDB (105% do CDI) | 25% | 15% | 5% |
| LCI/LCA (90% do CDI) | 20% | 10% | 5% |
| Tesouro IPCA+ | 15% | 15% | 10% |
| Fundos imobiliários (FIIs) | 5% | 15% | 20% |
| Ações / ETF Ibovespa | 5% | 20% | 35% |
| ETF internacional (S&P 500) | 0% | 10% | 20% |

## Recursos do Excel utilizados

- **Células nomeadas** para facilitar a leitura das fórmulas (`Aporte_Mensal`, `Perfil`, `Prazo_Meses`, `CDI`, `IPCA`, entre outras).
- **PROCX** para buscar o percentual de cada ativo conforme o perfil, a rentabilidade e a alíquota de IR de cada ativo, e o patrimônio no prazo escolhido.
- **PROCX com correspondência aproximada** para achar a alíquota da tabela regressiva de IR.
- **Validação de dados** na lista de perfis e nos campos de aporte e prazo.
- **Formatação condicional** para avisar quando a soma dos percentuais de um perfil não for 100%.

## Premissas e limitações

As premissas e as fontes estão em [`docs/premissas-e-fontes.md`](docs/premissas-e-fontes.md).
Resumo das simplificações:

- O IR da renda fixa usa a alíquota do prazo total sobre o rendimento de cada ativo.
- Os retornos de FIIs, ações e ETF internacional são hipóteses editáveis, não previsões.
- Não considera taxas de corretagem, de administração nem a variação de preços dos ativos.
