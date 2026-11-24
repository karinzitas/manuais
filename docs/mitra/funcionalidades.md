## Integração
Cadastros Gerais (![botao](../fechamento/imagens/botao_cadastros_gerais.png){width="2%"}) > Integração > Monitor Pipeline

Os pipelines são responsáveis por buscar os arquivos XML nos respectivos diretórios para importar as informações para o sistema Mitra.

* Integração D-2: importa as informações das carteiras diárias e demonstrativos de caixa liberados pelo custodiante para fechamento em D-2, conciliando com os valores do próprio Mitra.
* Exportação Contábil: exporta os dados contábeis gerados nos fechamentos diários ou de mês, disponibilizando para a Gcont.
* IMBARQ: importa as informações do FIA Agrociência Ações do arquivo IMBARQ06.

Cada execução de integração gera um log, que apresenta eventuais erros e avisos. Esses logs podem ser recuperados em Integrações > Logs de integração.

## Operações
### Fundos
Cadastros Gerais (![botao](../fechamento/imagens/botao_cadastros_gerais.png){width="2%"}) > Operações > Fundos > Fundos

Ambiente acessado para editar lançamentos de fundos, como os de recebimento do FII Hermes, que foram provisionados para as 48 parcelas futuras com valor fixo da primeira e datas de recebimento conforme contrato de venda. Os recebimentos têm acontecido alguns dias antes do dia previsto, levantando a necessidade de ajuste não só do valor financeiro (que é atualizado pelo INPC) mas também da data de liquidação.

### Lançamentos
Cadastros Gerais (![botao](../fechamento/imagens/botao_cadastros_gerais.png){width="2%"}) > Operações > Lançamentos

Eventuais necessidades de ajuste de caixa ou de quantidade são importados manualmente por meio dessa funcionalidade.

### Renda fixa
Cadastros Gerais (![botao](../fechamento/imagens/botao_cadastros_gerais.png){width="2%"}) > Operações > Renda Fixa > Operações de Renda Fixa com Filtro

Permite editar e/ou remover operações de renda fixa, como a exclusão de operações compromissadas duplicadas que são eventualmente geradas caso os arquivos XML de uma liberação diária sejam integrados mais de uma vez no Mitra por engano.

### Remover
Cadastros Gerais (![botao](../fechamento/imagens/botao_cadastros_gerais.png){width="2%"}) > Operações > Remover

Com a estrutura (programa) selecionado na barra de navegação à esquerda, no módulo de Cota e Resultado, é possível remover as informações importadas e as informações geradas, em caso de duplicidade ou de reprocessamento: as informações importadas dizem respeito às informações integradas a partir dos arquivos XML, enquanto dentre as informações geradas estão os dados contábeis.

## Recuperar
Cadastros Gerais (![botao](../fechamento/imagens/botao_cadastros_gerais.png){width="2%"}) > Recuperar > Formulários salvos

Toda execução do programa [RECON] FUNDAÇÃO CERES ou [CONTÁBIL] FUNDAÇÃO CERES gera um formulário salvo com os resultados, para serem consultados novamente sem a necessidade de realizar o cálculo inteiro. Os cálculos de conciliação e fechamento dos fundos exclusivos de gestão própria (FIA Agrociência e FIM Eros) não são salvos automaticamente.