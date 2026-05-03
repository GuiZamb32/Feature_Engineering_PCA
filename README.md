# Análise WDI - World Development Indicators

## Sobre o Projeto

Este projeto realiza uma análise completa dos Indicadores de Desenvolvimento Global (WDI) do Banco Mundial, focando no período da pandemia COVID-19 (2019-2023).

## Estrutura do Projeto

```
├── analise_wdi_2019_2023.ipynb   # Notebook principal com toda a análise
├── WDICSV.csv                     # Dataset principal (VOCÊ PRECISA FORNECER)
├── WDISeries.csv                  # Dicionário de séries (VOCÊ PRECISA FORNECER)
├── WDICountry.csv                 # Informações dos países (VOCÊ PRECISA FORNECER)
└── README.md                      # Este arquivo
```

## Arquivos Necessários

Você precisa fazer download dos seguintes arquivos do Banco Mundial:

1. **WDICSV.csv** - Dataset principal com todos os indicadores
2. **WDISeries.csv** - Dicionário de dados com descrição das séries
3. **WDICountry.csv** - Informações sobre os países

### Onde Baixar:
- Site oficial: https://databank.worldbank.org/source/world-development-indicators
- Ou busque por "World Development Indicators download" no Google

## Requisitos

### Bibliotecas Python:
```bash
pip install pandas numpy matplotlib seaborn
```

**IMPORTANTE:** Este projeto NÃO utiliza bibliotecas de IA/ML como scikit-learn, seguindo as especificações da atividade.

## Como Usar

1. **Baixe os datasets** do Banco Mundial e coloque na mesma pasta do notebook

2. **Abra o notebook**:
   ```bash
   jupyter notebook analise_wdi_2019_2023.ipynb
   ```

3. **Execute as células** sequencialmente (Cell > Run All ou Shift+Enter)

## Conteúdo do Notebook

### 1. Carregamento e Exploração
- Importação das bibliotecas
- Carregamento dos datasets
- Exploração inicial dos dados

### 2. Seleção de Features
Features distribuídas em 4 pilares:
- **Econômico**: PIB per capita, Inflação, Exportações, Desemprego
- **Saúde**: Expectativa de vida, Mortalidade infantil, Gastos em saúde
- **Educação/Social**: Alfabetização, Internet, População urbana, Eletricidade
- **Ambiental**: Emissões CO2, Consumo de energia, Energia renovável

### 3. Limpeza de Dados
- Remoção de países com muitos dados faltantes
- Remoção de features com >40% de valores nulos
- Imputação de valores faltantes usando mediana

### 4. Feature Engineering

#### Questão 02: Índice de Eficiência de Saúde
- Calcula: Expectativa_Vida / Gasto_Saude_Per_Capita
- Identifica países eficientes com orçamentos limitados

#### Questão 03: Categorização Industrial
- Cria variável categórica: Nivel_Industrial (Alta/Média/Baixa)
- Baseada em Exportações + Consumo de Energia
- Usada para colorir o gráfico PCA

#### Questão 04: Normalização Per Capita
- Divide métricas absolutas pela população
- Compara PCA antes e depois
- Analisa impacto na variância explicada

#### Questão 05: Tratamento de Skewness
- Aplica transformação logarítmica no PIB
- Gera histogramas comparativos
- Analisa impacto em outliers

### 5. PCA (Implementação Manual)
- Implementação própria do PCA usando NumPy
- Sem uso de scikit-learn
- Cálculo de:
  - Matriz de covariância
  - Autovalores e autovetores
  - Componentes principais
  - Variância explicada
  - Loadings

### 6. Visualizações

#### Questão 01: Interpretação dos Componentes
- Gráficos de loadings (pesos)
- Análise do significado de PC1 e PC2
- Síntese interpretativa

#### Gráfico de Dispersão Principal
- 2 primeiros componentes principais como eixos
- Colorido por Nível Industrial
- Labels para países de interesse
- Linhas de referência

#### Análises Complementares
- Scree plot (variância por componente)
- Análise de quadrantes
- Identificação de clusters

## Resultados Esperados

### Outputs:
1. **Gráfico de dispersão** com países no espaço PC1 x PC2
2. **Gráficos de loadings** mostrando importância das features
3. **Histogramas** do PIB (original e log-transformado)
4. **Análises** respondendo às 5 questões propostas
5. **Arquivos CSV**:
   - `dados_processados_pca_2019_2023.csv`
   - `pca_loadings_2019_2023.csv`

### Interpretações:
- PC1 = Índice de Desenvolvimento Socioeconômico
- PC2 = Sustentabilidade vs Industrialização
- Identificação de clusters de países similares
- Análise do impacto da pandemia COVID-19

## Questões Respondidas

✅ **Q1**: Interpretação dos componentes principais (loadings e síntese)<br>
✅ **Q2**: Criação e análise do Índice de Eficiência de Saúde<br>
✅ **Q3**: Categorização do Nível Industrial e uso no gráfico<br>
✅ **Q4**: Comparação do PCA antes/depois da normalização per capita<br>
✅ **Q5**: Tratamento de skewness com transformação logarítmica<br>

## Observações Importantes

### ⚠️ Antes de Executar:
1. Certifique-se de ter os 3 arquivos CSV do WDI
2. Ajuste os nomes dos arquivos se necessário
3. Verifique se as features selecionadas existem no seu dataset
4. O dataset WDI é atualizado periodicamente - códigos de indicadores podem mudar

### 💡 Dicas:
- Execute célula por célula para acompanhar o processo
- Leia os comentários e análises em cada seção
- Os gráficos são interativos no Jupyter
- Você pode modificar a lista de países a rotular no gráfico
- Ajuste as cores e estilos de visualização conforme preferir

### 🔧 Personalizações Possíveis:
- Adicionar/remover features da análise
- Ajustar threshold de dados faltantes
- Modificar número de componentes principais
- Alterar método de imputação
- Customizar visualizações

## Autor

Guilherme Zamboni Menegacio

## Licença

Este projeto é para fins educacionais.
Os dados são propriedade do Banco Mundial.

## Contato

Para dúvidas ou sugestões, entre em contato pelo email guilhermezamboni867@gmail.com

---

**Última atualização**: Maio 2026
**Versão**: 1.0
