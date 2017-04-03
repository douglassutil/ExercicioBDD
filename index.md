## Exercício de TDD/BDD

### Exercício Imposto de renda
https://github.com/mbbotelho/ImpostoRendaBdd

Esse foi o primeiro exercício na vida que aplique BDD/TDD (sei que era para ter feito quando fiz a matéria de poo1 :/) .Por nunca ter  entendido como funciona essa técnicas de verdade, mais depois que li o livro ... tudo ficou mais claro na cabeça. Pelo menos agora eu consigo ter um ponto de partida.

Nesse exercício comecei a fazer as Features de acordo com as característica

Scenario: calculando o imposto de renda 
    Given Eu tenho um salario
    When Eu quero calcular o imposto de renda do salario "1600.0"
    Then Eu tenho o valor do imposto "0.0"

    Scenario: calculando o imposto de renda
    Given Eu tenho um salario
    When Eu quero calcular o imposto de renda do salario "1800.0"
    Then Eu tenho o valor do imposto "135"
    
    Scenario: calculando o imposto de renda
    Given Eu tenho um salario
    When Eu quero calcular o imposto de renda do salario "2600"
    Then Eu tenho o valor do imposto "390"

e nos steps fui aplicando a tecnica de tdd(fazer o teste falar,fazer o teste passar e refatora) o resultado:


Como o arquivo de Features ficou muito repetitivo, resovi atualiar para uma tabela. Com isso montei caso de teste para todas faixas do imposto de renda

Feature: Calcular a taxa do imposto de renda dos salarios informados.

    Scenario Outline: Calcular o imposto de renda de acordo com um salário
    Given Eu tenho o salario "<salario_pessoa>"
    When  Eu quero calcular o imposto de renda do salario
    Then  Eu quero o valor "<resultado_calculado>" como resultado
    
    Examples:
   |salario_pessoa|resultado_calculado|
   
   |1600.0|0.0|
  
   |1800.0|135.0|
   
   |2600.0|390.0|
   
   |3500.0|787.5|
   
   |4500.0|1237.5|
   
   Mas ainda precisava refatorar o código e aplicar padrões de projeto. Comecei a refator e apliquei o padrão de projeto estratégia para representar as faixas do imposto de renda e 	cadeia	de	responsabilidade de responsabilidade para passar de uma faixa para outra. Depois de refatorar rodei o teste, para minha tristeza vário teste falharam, mesmo eu tendo certeza que refatorei certo. Ai os teste que crie me ajudaram a identificar ainda estava errado e foi mais  fácil de concertar o erro. Depois que acertei o erro. Rodei o teste e todos funcionaram (  QUE FELICIDADEEEEE o/ o/ o/)
   
   ### Conclusão
   De fato o TDD/TDD ajuda a você ter certeza que no final esta desenvolvendo um programa correto. Mas para mim ainda não é uma coisa  natural demorei muito tempo para desenvolver esse exercício. Acredito que isso seja uma questão de prática
