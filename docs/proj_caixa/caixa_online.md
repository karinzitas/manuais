# Projeto Caixa Online

O projeto Caixa Online tem como objetivo oferecer à GEINV a informação do caixa de fechamento do dia anterior (D-1), para auxiliar na sensibilização do recurso disponível para movimentações.

## Passo a passo

1. Obter o arquivo <code>.xls</code> do [site do custodiante](https://bc2.custodia.bradesco/calilogin/login.jsf?lang=1), acessando a aba "Caixa On-line" na barra de navegação > Consulta > Monitoria > Caixa On Line > Pesquisar > Salvar como XLS.
2. Salvar a planilha no diretório <code>G:/Drives compartilhados/GEMOI/Projeto Caixa Online/arquivos Bradesco</code>.
3. Executar o arquivo <code>importacao_dados.bat</code>, que vai gerar uma planilha no modelo <code>caixa_online_DATA.xlsx</code>.
4. Abrir a planilha, copiar as células com informação (não precisa copiar o cabeçalho).
5. Acessar o Mitra Produção e, no módulo Front, clicar em Monitores > Cadastro de Caixa Online.
6. Selecionar Importação > Colar > Salvar.

> Importante: essa rotina deve ser realizada **diariamente**, até 9h.