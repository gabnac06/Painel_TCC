# Fogo em Lavras-MG — estudo interativo do TCC

Portal de exploração do mapeamento do fogo em Lavras-MG, entre 2011 e 2025, com identidade visual baseada na logo da Universidade Federal de Lavras fornecida para o projeto.

Portal: https://lavras-fogo-2011-2025.dapperdog2.chatgpt.site

## Funcionalidades

- Mapas de recorrência, área atingida ao menos uma vez e queima anual.
- Camadas vetoriais de 2011 a 2025 com mês, cobertura da terra e área por feição.
- Integração descritiva com uso e cobertura do mesmo ano da queima.
- Controle de opacidade, ampliação do mapa, navegação e reprodução dos anos.
- Gráficos anuais e mensais, calendário de sazonalidade e comparação de quinquênios.
- Consulta de atributos ao clicar nas feições e download dos vetores GeoJSON.
- Tabelas filtradas para consulta e download CSV.

## Dados e interpretação

MapBiomas Fogo, Coleção 5, e MapBiomas Brasil, Coleção 11, na resolução original de 30 m. A área municipal do domínio analisado é 56.429,2952 ha. A soma das áreas anuais é 8.107,8288 ha; a área atingida ao menos uma vez é 5.687,8354 ha; a área atingida em dois ou mais anos é 1.727,2613 ha.

As áreas dos indicadores usam os valores validados de interseção dos pixels com o limite municipal, calculados em EPSG:31983. Os mapas web e vetores usam EPSG:4326. As feições vetoriais são cópias de apresentação derivadas da grade nativa; seus atributos geométricos não substituem as tabelas de referência. Recorrência é o número de anos com presença mapeada, não a contagem de incêndios. Zero não comprova ausência física de fogo. Não são feitas inferências causais ou predições neste portal.

Os vetores de recorrência e área acumulada estão disponíveis para o período completo e os três quinquênios. Em outros recortes de anos, mês ou classe, esses mapas usam a visualização filtrada dos pixels nativos. As camadas anuais e de integração usam as feições vetoriais do respectivo ano. A grade de 500 m não é oferecida como opção de visualização.

## Executar localmente

O portal é estático e não exige instalação de dependências para uma compilação.

```sh
python -m http.server 8765 --directory dist
```

Abra http://localhost:8765 em um navegador atualizado. Os dados binários comprimidos são lidos com a API `DecompressionStream`. O fundo cartográfico utiliza OpenStreetMap, com atribuição na interface. Não há integração com Google Maps e não é necessária chave de API.

## Organização

- `dist/index.html`: interface e seções do estudo.
- `dist/styles.css`: identidade visual e responsividade.
- `dist/app.js`: filtros, estatísticas, gráficos, tabelas e mapa de pixels.
- `dist/vector-maps.js`: camadas vetoriais, atributos e navegação anual.
- `dist/data`: tabelas, dados de apresentação, limite municipal e vetores.
- `dist/lib`: Leaflet e Apache ECharts, incorporados localmente.
- `docs`: registros de fontes e conferências numéricas.

Os rasters originais, a biblioteca de pacotes R, credenciais, arquivos internos de hospedagem e o texto do TCC não fazem parte deste repositório.

## Fontes e bibliotecas

- MapBiomas: https://brasil.mapbiomas.org/
- OpenStreetMap: https://www.openstreetmap.org/copyright
- Leaflet 1.9.4: https://leafletjs.com/
- Apache ECharts 5.6.0: https://echarts.apache.org/

As bibliotecas mantêm suas licenças e avisos próprios. A identificação visual da UFLA foi fornecida pelo responsável pelo projeto.
