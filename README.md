# Pipeline_python
Projeto DIO -> Pipeline com Python

Projeto que envolve o processo ETL: extração, transformação e carregamento dos dados.

# Este projeto teve insumo um banco de dados que sinaliza a média de consumo dos clientes de determinada empresa.
1. Os dados foram extraídos do arquivo 'consumo_medio_energia' disponível abaixo.
2. Os dados foram transformados com a inserção de duas novas colunas, 'status_energia' e 'desconto' que indicam respectivamente o nível de consumo de energia e se determinado desconto é aplicável.
3. O dataframe foi convertido e carregado em .json para arquivo 'consumo_energia_json'. 


## Arquivos para download
[consumo_medio_energia (1).csv]
(https://github.com/codepyrock/pipeline_python/files/12551926/consumo_medio_energia.1.csv)

[Uploading Projeto_{"nbformat":4,"nbformat_minor":0,"metadata":{"colab":{"provenance":[],"authorship_tag":"ABX9TyMHYaYs0z9De4mlWIPNEuWe"},"kernelspec":{"name":"python3","display_name":"Python 3"},"language_info":{"name":"python"}},"cells":[{"cell_type":"markdown","source":["App que emite mensagens quando clientes aumentam muito o consumo de energia"],"metadata":{"id":"CA6KmnhXlUXm"}},{"cell_type":"markdown","source":["Extract"],"metadata":{"id":"WJzYPMmX0s-Y"}},{"cell_type":"code","execution_count":null,"metadata":{"id":"H4o_dJeWlG6b"},"outputs":[],"source":["import pandas as pd\n","\n","df = pd.read_csv('consumo_medio_energia.csv', sep=',')\n","df.head()\n","\n"]},{"cell_type":"markdown","source":["Transform"],"metadata":{"id":"AQGkgV3qjR_E"}},{"cell_type":"markdown","source":["Hipoteticamnte será concedido um desconto para cada cliente que obtiver cumprir alguns requisitos. Por isso, foi criada uma coluna com status da energia"],"metadata":{"id":"a8NiL0KAzMPx"}},{"cell_type":"code","source":["df['status_energia'] = ['alto' if i > 200 else 'baixo' for i in df.media_consumo_kwh]\n","df"],"metadata":{"id":"hvO8_KpSeZNz"},"execution_count":null,"outputs":[]},{"cell_type":"markdown","source":["Criação de outra coluna que determinará a concessão ou não do desconto baseada na coluna status_energia"],"metadata":{"id":"noHLQMYWooIG"}},{"cell_type":"code","source":["df['desconto'] = ['sim' if i == 'baixo' else 'nao' for i in df.status_energia]\n","df"],"metadata":{"id":"732Rwh1xomnp"},"execution_count":null,"outputs":[]},{"cell_type":"markdown","source":["Load -> carregando em arquivo json"],"metadata":{"id":"LytX2AKpBiR-"}},{"cell_type":"code","source":["import json\n","consumo_energia_json = df.to_json()\n","print(consumo_energia_json)\n"],"metadata":{"id":"woXxEAmGbGrX"},"execution_count":null,"outputs":[]}]}ETL.ipynb…]()

