# Referência de problemas da rotina de fechamento
Os eventuais problemas com a rotina de fechamento envolvem diferenças de quantidade, PU, financeiro ativo ou financeiro passivo entre os dados do custodiante e do Mitra. Essas divergências podem ocorrer por erros operacionais, como a integração duplicada dos arquivos XML de um dia, ou por erros estruturais, como a não captura de informações necessárias do arquivo XML pelos programas do Mitra.

## Remover informações duplicadas ou reprocessamento da estrutura de carteiras
Durante a rotina, um dos erros operacionais que podem acontecer é a integração duplicada (ou mais) das informações que são importadas para o Mitra, sendo necessário excluir os dados excedentes. Esse processo também deve ser executado caso o custodiante comunique o reprocessamento da estrutura de carteiras devido à necessidade de reprocessamento de algum fundo específico.

### Remover as informações importadas
Com o programa **[RECON] FUNDAÇÃO CERES** selecionado, clicar em Cadastros Gerais (![botao](imagens/botao_cadastros_gerais.png){width="2%"}) > Remover > definir a data inicial e a data final dos dias cujos dados serão removidos > selecionar Informações Importadas > Selecionar Tudo > Remover. Será necessário digitar EXCLUIR na janela que aparecer para que a remoção dos dados se complete.

### Remover as operações compromissadas
Na integração dos dados, são geradas informações sobre operações compromissadas, que também precisam ser removidas: Cadastros Gerais (![botao](imagens/botao_cadastros_gerais.png){width="2%"}) > Operações > Renda Fixa > Operações de renda fixa com filtro > definir as mesmas datas do passo anterior > filtrar apenas as OP_COMP_PRE e remover todas (em caso de nova integração) ou as duplicadas (em caso de erro de integração realizada de forma duplicada).

### Remover informações duplicadas dos fundos
Com os **Fundos Exclusivos** (![botao](imagens/botao_fundos.png){width="2%"}) selecionados, seguir os mesmos passos apresentados para a remoção de informações importadas.

### Remover os dados contábeis
Se a rotina de fechamento já tiver sido concluída, também será necessário remover os dados contábeis gerados. Cadastros Gerais (![botao](imagens/botao_cadastros_gerais.png){width="2%"}) > Operações > Remover > definir a data inicial e a data final dos dias cujos dados contábeis serão gerados novamente > selecionar Informações Geradas > selecionar **apenas** Dados Contábeis > Remover.

## Diferenças no Caixa
As diferenças no fechamento do Caixa, tanto dos planos de benefícios quanto dos fundos exclusivos de gestão própria, podem ocorrer por provisões do XML que não foram integradas corretamente para o Mitra ou por despesas que não são capturadas pela integração.

Na ocasião de divergência de caixa, no programa selecionado à esquerda ([RECON] FUNDAÇÃO CERES), expandir os níveis até os planos e escolher um dos planos que apresentaram diferença. Clicar com a direita no plano e escolher Gerenciamento de Caixa, que vai abrir as informações de caixa que foram integradas e que podem ser consultadas no **demonstrativo de caixa** do plano.

Conferir os lançamentos presentes no Mitra com os do XML para verificar onde está a diferença.

### Remover lançamentos
Caso os dados estejam duplicados, excluir em Cadastros Gerais (![botao](imagens/botao_cadastros_gerais.png){width="2%"}) > Operações > Lançamentos.

### Ajuste de caixa
Nos dias 7 e 15, há as rotinas de despesas financeiras, cujas informações não são integradas no Mitra, uma vez que o Bradesco não segue um padrão e, por isso, esses dados acabam não sendo capturados pelo pipeline de integração. Nesse caso, essas despesas precisam ser incluídas manualmente.

No diretório <code>D:/LUZ Soluções Financeiras/ARQUIVOS INTEGRAÇÃO/MODELOS DE AJUSTE</code>, abrir a planilha <code>Modelos de ajuste - Caixa.xlsx</code> e copiar o modelo utilizado anteriormente. Colar embaixo para manter um histórico, ajustando a data de entrada e de lançamento para a data em questão, o valor das despesas conforme o demonstrativo de caixa e a descrição.

No Mitra: Cadastros Gerais (![botao](imagens/botao_cadastros_gerais.png){width="2%"}) > Operações > Lançamentos > escolher Importação > Colar > Validar > Salvar.

> Importante verificar os valores que estão faltando no sistema que sejam referentes somente às despesas financeiras. Simplesmente pegar o valor da diferença resultante do cálculo pode resultar em ajustes que não estão relacionados às despesas financeiras daquele dia.

### Ajuste de rendimentos
O ajuste de caixa gera um ajuste gerencial, que não tem um impacto contábil, enquanto o ajuste de rendimentos possui uma consequência contábil. No fechamento do mês, quando há necessidade de ajustar o caixa dos planos para ficarem zerados, geramos um **ajuste de rendimentos**, seguindo os mesmos passos acima, com a diferença da planilha utilizada para os ajustes <code>Ajuste de rendimentos.xlsx</code>. A inserção desse ajuste no Mitra se dá da mesma forma.

### Incluir os recebimentos do Ed. José Guerra
Assim como as despesas financeiras, os recebimentos da venda do Ed. José Guerra também não são capturados na integração dos XML para o Mitra, sendo necessário incluí-los manualmente. A solução é a mesma da inclusão dos lançamentos de despesas.

### Ajustar os recebimentos do FII Hermes
De forma similar, também se faz necessário ajustar os recebimentos do FII Hermes. Por mais que os valores das 48 parcelas estejam já lançados e provisionados no Mitra, o valor da parcela que cada plano vai receber não é atualizado pelo INPC. Além disso, a Phorbis costuma adiantar o pagamento em relação à data provisionada no Mitra.

Cadastros Gerais (![botao](imagens/botao_cadastros_gerais.png){width="2%"}) > Operações > Fundos > Fundos > na janela que abrir, digitar "FII Hermes" em Nome para filtrar apenas os lançamentos desse "fundo". Depois, filtrar pela data do mês em exercício e editar cada lançamento, atualizando a **Data de liquidação** e o **Financeiro**, com o valor apresentado no demonstrativo de caixa.

## Anotações
### Sobre títulos públicos comprados a termo
Quando há boletagem de títulos públicos, a NTN-B não vai com o código certo, referente à operação, para o Bradesco, pois a Geinv ainda não tem essa informação na hora de fazer a boleta. Por causa disso, o código do Mitra fica "genérico", no padrão "MTRXXXXX".

Caso haja diferença entre Mitra e sistema externo muito mais alta do que as diferenças normais de precificação, é porque o Bradesco já identificou o código correto, mas o Mitra ainda usa o código placeholder. Dessa forma, é necessário atualizar essa informação no Mitra:

Cadastros Gerais (![botao](imagens/botao_cadastros_gerais.png){width="2%"}) > Operações > Renda Fixa > Operações de renda fixa com filtro > encontrar as NTN-B que deram problema e editar uma a uma, atualizando o código de acompanhamento com o código do Bradesco.

Além disso, se a operação for **a termo**, então é D+1 e ela só regulariza no Mitra na conciliação do dia posterior. Nesse caso, é possível que o código de agrupamento mude novamente. Nesse caso, é preciso igualar o código do Mitra com o código mais recente, mesmo que isso em teoria possa impactar a conciliação do dia anterior (já que o código ficará divergente de novo). Não tem problema pois não vamos calcular o dia anterior de novo.