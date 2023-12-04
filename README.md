# Analise Farmacêutica
![image](https://github.com/danielreinaux/DataAnalytics/assets/91274263/efd37374-d100-4aab-949e-97b577842a89)

## 🔍 Sobre o projeto
#### Análise de Consumo de Medicamentos Industrializados
O propósito principal desta análise é explorar e entender os padrões e tendências no consumo de medicamentos industrializados. Nosso foco será desvendar insights acerca da utilização destes produtos, observando variáveis como categorias de medicamentos, volume de consumo, e regiões de distribuição predominantes.

#### Alvo da Análise
1. **Padrões de Consumo**: Identificar os medicamentos mais consumidos para entender as preferências da população.
2. **Categorias e Variedades**: Analisar as categorias de medicamentos no dataset para determinar quais são mais prevalentes.
3. **Regiões de Maior Consumo e Promoção da Saúde Pública**: Descobrir regiões com maior demanda e fornecer recomendações para melhorar o acesso e a distribuição de medicamentos essenciais.



#### Sobre o Dataset 
Nossa análise se baseia em uma amostra cuidadosamente selecionada de dados obtidos do Portal de Dados Abertos do Governo Brasileiro (Gov.br), específicos ao mês de Novembro de 2021. Esta amostra representa uma fonte oficial e pública de dados, garantindo a veracidade e a relevância das informações coletadas.
![image](https://github.com/danielreinaux/DataAnalytics/assets/91274263/394553cb-e84a-42a0-9ff5-92d4eec7bb92)

## 💾 Tratamento de Dados
Foi-se criada uma função de Metadados para entender melhor o funcionamento das categorias do Dataset, e dessa forma, executar de forma efetiva o seu tratamento. A função gerou essa tabela:
![image](https://github.com/danielreinaux/DataAnalytics/assets/91274263/495dba99-423c-4a5c-a2ec-165b1ab4b64c)
Pela tabela dos metadados, pôde-se ter certas ações:
* Importante notar que existem algumas colunas com uma quantidade elevada de valores nulos. No caso de `CID10` em que o número é de 99.90% de números nulos, a retirada dessa coluna é o melhor a se fazer
*  Para os casos de `SEXO` e `UNIDADE_IDADE` em que a cardinalidade é igual a 2, vamos preencher esses valores nulos com a moda dessas variáveis.
* Para o caso de `IDADE`, o preenchimento será pela média dessa variável. Talvez o ideal fosse colocar a mediana, já que temos muitos outliers
* O `PRINCIPIO_ATIVO` é uma variável object, logo, o melhor a se fazer para preencher os nulos é colocar uma string "SEM CONHECIMENTO". **Poderíamos também colocar o valor da Moda**, **que é o ideal para variáveis categóricas**
* As colunas `ANO_VENDA` e `MES_VENDA` continuaram como inteiras, pois a cardinalidade de ambas é apenas 1, considerando que é um dataset de um mês específico
* Além disso, mudaremos o nome da coluna `unnamed` para `id`, para ficar mais intuitivo.

## 🗺️ Analise exploratória dos dados

#### Medicamentos mais vendidos
Para essa análise, foi necessária a utilização da categoria `PRINCIPIO_ATIVO`
![image](https://github.com/danielreinaux/DataAnalytics/assets/91274263/6d440fd8-919d-40ca-8a3f-725ef90764cf)
É possível, com esse gráfico, entender alguns pontos importantes:


Identificar o Líder do mercado:
  * É possível perceber que o medicamento mais vendido é o **clonazepam**. Indicando que o medicamento é bem visto no mercado em seus diversos âmbitos, como eficácia, popularidade ou disponibilidade
  * Importantes para o próprio produto, e até para seus competidores, entederem do porque esse medicamento vende tanto, podendo intensificar essas vendas, ou no caso dos concorrentes, encontrarem formas de concorrer


Diversificação de Produto
  * Nota-se que, apesar do **Clonazepam** está com uma boa margem frente aos outros, existe uma grande variabilidade dos produtos, e o mercado é relativamente equilibrado
  * Fundamental essa análise para os empreendedores atuais e novos nesse mercado. Entender como ele se comporta, e como pode agir em meio a esse cenário

Potencial de Mercado
  * Identificação de oportunidades de crescimentos são possíveis na visualização desses gráficos, entendendo onde o mercado está saturado, e onde existem brechas para o crescimento
 
#### Medicamentos vendidos por estado
![image](https://github.com/danielreinaux/DataAnalytics/assets/91274263/ff88c0f5-bbd1-4df3-b124-a00d4a7556f6)
1. **Dominância do Mercado no RJ**: O volume de vendas de medicamentos no estado do Rio de Janeiro destaca-se significativamente, sugerindo uma demanda substancialmente maior, o que pode indicar uma concentração de serviços de saúde ou uma maior prevalência de farmácias e distribuidoras. No entanto, essa dominância também pode apontar para um mercado potencialmente saturado, onde novos entrantes podem enfrentar forte concorrência.
2. **Potencial de Crescimento em SP e MG**: São Paulo e Minas Gerais, apesar de sua população numerosa e desenvolvimento econômico, mostram vendas relativamente baixas de medicamentos. Isso pode indicar uma oportunidade significativa de mercado para expansão ou melhoria na distribuição e acessibilidade de medicamentos.
3. **Distribuição Desigual**: A disparidade nas vendas entre os estados sugere uma distribuição desigual de recursos de saúde ou diferenças na estrutura de atendimento à saúde. Esta informação é crucial para políticas públicas focadas em melhorar o acesso à saúde e a medicamentos em estados com menor volume de vendas.

#### Venda por gênero e idade
Análises separadas por determinadas categorias são fundamentas para cada produtor/vendedor entender seu público alvo. Fundamental para uma venda mais direcionada, e consequentemente, eficiente

##### Distribuição de idade dos compradores
![image](https://github.com/danielreinaux/DataAnalytics/assets/91274263/e58a4950-c080-4bb2-b30f-545ab5d5b3da)
Alguns insights tirados desse gráfico:
1. **Alto Consumo aos 40 anos**: Existe um pico no consumo de medicamentos na faixa dos 40 anos, indicando a necessidade de focar em tratamentos para condições comuns nessa idade.

2. **Baixa Frequência entre Jovens e Idosos**: Há uma compra reduzida de medicamentos por jovens e idosos, o que pode apontar para uma menor incidência de doenças ou dificuldades de acesso a medicamentos nessas idades.

3. **Demanda Contínua na Terceira Idade**: A distribuição mostra uma demanda constante por medicamentos entre os mais velhos, destacando a importância do acesso a tratamentos para doenças crônicas na velhice.

##### Distribuição por gênero:
Nessa análise, o número 1 é o gênero feminino, e o 2 é o gênero masculino 
![image](https://github.com/danielreinaux/DataAnalytics/assets/91274263/941a12cd-626e-40f6-af7c-06bf08aff184)
 
Além disso, analisamos os 3 medicamentos mais vendidos, separados novamente por gênero:
![image](https://github.com/danielreinaux/DataAnalytics/assets/91274263/5ca9b3ff-f4db-49bf-b3de-3a49e5448f85)
![image](https://github.com/danielreinaux/DataAnalytics/assets/91274263/3573eb60-cb97-4d0f-a677-460c7b90ec0f)
![image](https://github.com/danielreinaux/DataAnalytics/assets/91274263/073216c1-8a0e-420e-918d-5ba150da5dbe)

A análise dos dados de consumo de medicamentos revela padrões significativos relacionados ao gênero e à idade dos compradores, oferecendo insights valiosos para estratégias de mercado:
1. Dominância Masculina no Mercado: Homens são os principais compradores no mercado de medicamentos, representando a maioria dos consumidores. Com base nessa tendência, as empresas têm duas abordagens estratégicas principais:
- Marketing Focado: Desenvolver campanhas de marketing e benefícios que atendam às necessidades e preferências masculinas, maximizando o engajamento com esse segmento predominante.
- Atração do Público Feminino: Implementar iniciativas para equilibrar a discrepância de gênero, como a introdução de produtos especializados para mulheres, incluindo itens de higiene pessoal feminina e suplementos nutricionais destinados à saúde feminina.
2. Concentração de Compradores de 30-45 Anos: A faixa etária de 30 a 45 anos constitui uma parcela significativa dos consumidores. As farmácias e fabricantes devem, portanto, direcionar estratégias para atender eficazmente às necessidades deste grupo demográfico. Isso pode incluir a criação de programas de fidelidade, ofertas especiais e serviços de saúde preventiva que ressoem com esse público-alvo.

3. Participação Inferior de Idosos: Apesar da maior necessidade potencial de medicamentos, os idosos não representam a maior parcela de compradores. Isso aponta para oportunidades de melhoria no acesso e na comodidade, tais como:

- Entrega Conveniente: Aperfeiçoar os serviços de entrega para superar barreiras de mobilidade enfrentadas por idosos, como serviços de entrega rápida e métodos de compra simplificados.
- Acesso Facilitado: Introduzir soluções inovadoras, como farmácias drive-thru, permitindo que os idosos adquiram medicamentos sem sair do carro, ou programas de assistência que facilitam o reabastecimento automático de prescrições regulares.

Além disso, podem ser explorados outros pontos para melhorar a acessibilidade e a experiência de compra para todos os consumidores:
- Programas Educacionais: Campanhas de conscientização sobre saúde e bem-estar adaptadas para diferentes grupos etários e gêneros, promovendo o uso responsável de medicamentos.
- Parcerias com Profissionais de Saúde: Colaborar com médicos e profissionais de saúde para entender melhor as necessidades específicas de medicamentos e garantir que as farmácias estejam bem abastecidas com os produtos necessários.
- Análise de Dados Contínua: Utilizar dados de vendas e feedback dos consumidores para ajustar continuamente a oferta de produtos e as estratégias de marketing, garantindo que as necessidades dos clientes sejam atendidas de maneira eficaz.
