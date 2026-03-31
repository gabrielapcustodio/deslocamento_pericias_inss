# Deslocamentos para perícia do INSS

Este repositório conta com as análises realizadas durante a produção de uma série com duas reportagens sobre os deslocamentos de residentes do Ceará para realizar perícia médica para benefícios concedidos pelo Instituto Nacional do Seguro Social (INSS), publicadas no Diário do Nordeste nos dias 30 e 31 de março de 2026.

As reportagens podem ser lidas clicando nas seguintes imagens:

Matéria 1, publicada no dia 30/03/2026.

<a href="https://diariodonordeste.verdesmares.com.br/negocios/gargalo-do-inss-forca-pelo-menos-75-mil-beneficiarios-no-ceara-a-viajar-mais-de-70-km-para-pericia-1.3752155" target="_blank">
  <img src="https://github.com/user-attachments/assets/af5954da-157f-4632-b71b-7c6eb7a41838" alt="Capa da primeira reportagem, com pessoas entrando em uma agência da previdência social e o título da matéria." width="100%" />
</a>


Matéria 2, publicada no dia 31/03/2026.

<a href="https://diariodonordeste.verdesmares.com.br/negocios/moradores-de-cidade-cearense-viajam-mais-de-200-km-para-pericia-do-inss-veja-lista-de-municipios-1.3752972" target="_blank">
  <img src="https://github.com/user-attachments/assets/d844e9bd-a0a8-4929-b47c-ad59cda12c94" alt="Capa da segunda reportagem, com pessoas entrando em uma agência da previdência social e o título da matéria." style="width:100%; max-width:800px;" />
</a>

## Metodologia da análise

Esta reportagem utilizou dados concedidos pelo Ministério da Previdência Social por meio da Lei de Acesso à Informação (LAI) sobre os municípios de residência e de realização da perícia médica por requerentes do Ceará entre 2019 e 2026.

O pedido e a resposta estão disponibilizados na íntegra [neste repositório](https://github.com/gabrielapcustodio/deslocamento_pericias_inss/blob/main/pedido%20de%20LAI/DetalhesNUP_18800048823202611.pdf).

Devido ao tamanho do arquivo enviado pelo Ministério, mesmo com posteriores filtros realizados, não foi possível disponibilizar o arquivo original. Porém, é possível conferir os códigos completos realizados para a análise nos notebooks `pericias_medicas_notebook_1_preparacao.ipynb` e `pericias_medicas_notebook_2_analise.ipynb`.

Com o uso da linguagem de programação Python e auxílio de inteligência artificial para a construção do código de análise, foi feito o cruzamento com a [base de dados da malha municipal](https://www.ibge.gov.br/geociencias/organizacao-do-territorio/malhas-territoriais/15774-malhas.html) disponível no site do Instituto Brasileiro de Geografia e Estatística (IBGE) para se chegar às coordenadas geográficas de cada município.

Em seguida, foi aplicada a fórmula de Haversine, método matemático que calcula a menor distância entre dois pontos na superfície de uma esfera, como a Terra, a partir da latitude e da longitude.

Por não levar em consideração as estradas e os caminhos reais percorridos para se deslocar de uma cidade a outra, as distâncias calculadas são conservadoras e subestimadas, podendo ser ainda maiores na realidade.

Considerando as distâncias encontradas, os deslocamentos feitos estados do Nordeste e o entendimento do TRF5 de que o limite razoável para a realização de perícias médicas deve ser de 70 km do domicílio, foram calculados:

1. Quantos requerentes tiveram perícia médica marcada para cidades diferentes de onde moram e, destes, em quantos casos o local da perícia foi a mais de 70 km do município de residência;
2. Qual a distância média entre cada município e as cidades onde as perícias dos residentes foram marcadas, ponderada pelo número de perícias realizadas fora do local de moradia;
3. Quais os principais fluxos de origem e destino.

Para calcular a quantidade e a proporção de requerentes que tiveram perícia marcada para outras cidades ou não, e os que a distância era superior a 70 km, foi adotado o seguinte critério: quando o mesmo requerente aparecia mais de uma vez em um ano, foi considerada a maior distância entre os municípios de residência e da perícia.

Isso evitou duplicidade de requerentes que aparecessem em duas categorias no mesmo ano.

## Arquivos gerados
**_Dataframe_**
* `df_final_media_ponderada.csv`
* `df_rank_origem_destino.csv`
* `faixa_distancia_pericias.csv`
* `tipo_distancia_pericias.csv`

**_Visualizações_**
* [Tipo de distância: município de residência x município da APS](https://public.flourish.studio/story/3618848/)
* [Faixa de distância - perícia médica marcada para outras cidades](https://public.flourish.studio/story/3618761/)
* [Top 10 fluxos por ano](https://public.flourish.studio/story/3624719/)
* [Ranking das distâncias médias](https://public.flourish.studio/story/3624867/)
