# Modelagem de regras e decisão

&emsp;*A linguagem DMN trata da possibilidade de representação de tomadas de decisão em processos. Muitas vezes, as tomadas de decisão devem levar em consideração regras de negócio. Por isso, é comum usar tabelas de decisão como um dos elementos desse modelo.*

&emsp;*A modelagem das regras pode ser visualizada através deste README ou pela planilha do sheets localizada nesta mesma pasta.*


## Regras de Negócio
&emsp;As regras de negócios foram elaboradas com base no módulo de contábil da G2 Tecnologia. As regras foram inicialmente levantadas em sala de aula com auxílio do professor e posteriormente validadas com um consultor.

| Código | Nome                                   | Descrição                                    | Critério de Aplicação                                                                                          | Ação                             |
|--------|----------------------------------------|----------------------------------------------|-----------------------------------------------------------------------------------------------------------------|----------------------------------|
| RN001  | Acesso Restrito aos Relatórios de Faturamento | Checagem de permissão de acesso aos relatórios. | O colaborador que tentar gerar o relatório de faturamentos deve ser gerente ou superior.                        | Gerar relatório                  |
| RN002  | Tributação Obrigatória de Vendas       | Realização de venda.                         | Venda realizada no sistema deve conter dados de tributação.                                                     | Faturar venda                    |
| RN003  | Gerenciamento de Créditos Fiscais      | Utilização dos créditos fiscais da empresa.  | Os créditos fiscais devem ser utilizados antes do vencimento.                                                   | Utilizar crédito fiscal          |
| RN004  | Validação do Orçamento                 | Controle de despesas em relação ao orçamento aprovado. | Se o custo total de um lançamento contábil exceder o orçamento aprovado para o centro de custos, a transação deve ser bloqueada até a revisão e aprovação pelo gerente financeiro. | Bloquear transação e solicitar aprovação |
| RN005  | Classificação de Obrigações Acessórias | Geração de obrigações acessórias em transações financeiras. | Se uma transação financeira envolve impostos, a obrigação acessória correspondente deve ser gerada conforme a legislação vigente. | Gerar obrigação acessória        |

----
## RN001
### Acesso Restrito aos Relatórios de Faturamento

| U  | Um colaborador está tentando acessar os relatórios? (Bool) | O colaborador é gerente ou superior? (Bool) | Autorizar o acesso ao relatório? (Bool) |
|----|------------------------------------------------------------|---------------------------------------------|-----------------------------------------|
| 1  | Não                                                        | Não                                         | Não                                     |
| 2  | Sim                                                        | Não                                         | Não                                     |
| 3  | Sim                                                        | Sim                                         | Sim                                     |

## RN002
### Tributação Obrigatória de Vendas 

| U  | Uma venda foi realizada? (Bool) | A ordem de venda contém dados tributários? (Bool) | Autorizar transação? (Bool) |
|----|---------------------------------|--------------------------------------------------|-----------------------------|
| 1  | Não                             | Não                                              | Não                         |
| 2  | Sim                             | Não                                              | Não                         |
| 3  | Sim                             | Sim                                              | Sim                         |

## RN003
### Gerenciamento de Créditos Fiscais

| U  | A empresa tem créditos fiscais? (Bool) | Os créditos fiscais estão válidos? (Bool) | Utilizar créditos fiscais? (Bool) |
|----|---------------------------------------|------------------------------------------|----------------------------------|
| 1  | Não                                   | Não                                      | Não                              |
| 2  | Sim                                   | Não                                      | Não                              |
| 3  | Sim                                   | Sim                                      | Sim                              |

## RN004
### Validação do Orçamento

| U  | Ocorreu um lançamento contábil? (Bool) | O lançamento excede o orçamento aprovado no centro de custos? (Bool) | Autorizar transação? (Bool) |
|----|---------------------------------------|--------------------------------------------------------------------|-----------------------------|
| 1  | Não                                   | Não                                                                | Não                         |
| 2  | Sim                                   | Não                                                                | Não                         |
| 3  | Sim                                   | Sim                                                                | Sim                         |

## RN005
### Classificação de Obrigações Acessórias

| U  | Ocorreu uma transação? (Bool) | A transação financeira envolve impostos? (Bool) | Gerar obrigação acessória correspondente conforme a legislação vigente? (Bool) |
|----|------------------------------|-------------------------------------------------|--------------------------------------------------------------------------------|
| 1  | Não                           | Não                                             | Não                                                                            |
| 2  | Sim                           | Não                                             | Não                                                                            |
| 3  | Sim                           | Sim                                             | Sim                                                                            |

