# Projeto Risco de Liquidez
O projeto de risco de liquidez tem como objetivo projetar os recebimentos futuros já previstos (como de cupom de NTN-B, por exemplo), de forma a reduzir o risco de liquidez nos períodos de pagamento de benefício futuros. No momento, o projeto consiste em calcular os recebimentos previstos e os recebimentos de um dia específico de liquidação, como vencimento ou recebimento de cupom. Ainda em fase de validação.

## Calculando os recebimentos
O cálculo dos recebimentos é feito no Mitra, por meio dos programas <code>[SUCON] Projeção Rendimentos - Eros</code> e <code>[SUCON] Projeção Rendimentos - Planos</code>, sendo necessário escolher a data para cálculo. Após a execução desses programas, os resultados ficam disponíveis no [painel de controle](https://controle.ceres.org.br/).

## Obtendo os relatórios para validação
Acessar a pasta no diretório do Mitra: <code>D:/LUZ Soluções Financeiras/RELATORIOS</code>. Existem duas planilhas, que usam as seguintes consultas e dão os seguintes resultados:

| Planilha                           |         Consulta SQL         |     Resultado     |
|------------------------------------|:----------------------------:|:-----------------:|
| Modelo - Recebimento Cupom.xlsx    | [CERES] Recebimento Cupom v1 | Dia da liquidação |
| Modelo - Recebimento Cupom v2.xlsx | [CERES] Recebimento Cupom v3 | Fluxos futuros    |

Para gerar os relatórios, basta iniciar o Mitra Relatórios Produção, abrir o diretório acima e gerar o relatório com o add-in do Mitra.
