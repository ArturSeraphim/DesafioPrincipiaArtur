# Desafio Principia Artur Seraphim

*Etapas*

- Importação de dados:
  - Primeiramente importei as bibliotecas necessárias e instalei outras também
  - Depois retirei do banco de dados as linhas repetidas
 
- Validações:
  - CPF:
    - Primeiramente eu retirei os espaços dos cpfs para que nenhum fosse dado como incorreto por algum erro de padronização
    - Depois utilizei da biblioteca validate_docbr para fazer os cálculos necessários que verificam se um CPF é válido ou não, e como resposta obtive quais não são válidos.
  
  - Email:
    - Para a validação de e-mail, tentei usar APIs que fazem esse tipo de trabalho, porém não encontrei nenhuma gratuita, então utilizei uma biblioteca do python que faz a verificação, acredito que essa verificação não está completamente correta, alguns emails incorretos devem ter passado em branco, o ideal seria utilizar uma API, porém todas que encontrei são pagas, e procurei bastante.
    - Tendo duas saídas possiveis, se o algorítimo da biblioteca identificou algum email incorreto, ele mostra os nomes das pessoas com emails incorretos, se não houver "todos emails estão corretos"
 
  - Data de nascimento:
    - Primeiramente converti todas os valores para data pelo pandas usando datetime, padronizando-os
    - Depois converti as datas em idades e subtraí pela data atual, tendo assim a idade real da pessoa, e coloquei como invalidos aqueles mais novos do que 18 anos ou mais velhos do que 100 anos (botei um número máximo pra alguém não preencher incorretamente como "01/01/1888" e passar batido)
    - Assim recebendo como resposta quais são inválidos e se não houverem inválidos "Todas as datas são válidas"
  
  - Nomes completos:
    - Este código foi bem simples, apenas apliquei uma contagem no número de nomes escrito pela pessoa, se houvesse pelo menos dois nomes era contabilizado como nome completo, se houver apenas um nome é contabilizado como nome incompleto
    - Tendo também duas possiveis saídas, se houver nomes incompletos, mostrar quais são, se não houver "Todos os nomes estão corretos"
   
  - Telefones:
    - Para verificar se os telefones estão no padrão correto, utilizei uma verificação por meio de um padrão que seria (xx) xxxx-xxxx sendo 2 números entre parenteses, 4 ou 5 números (depende do estado), um "-" e mais 4 números.
    - Tendo as duas saídas possíveis, se houver telefones fora do padrão, mostrar quais são, se não houver "Todos os telefones estão corretos"
   
  - CEP:
    - Esta validação foi bem complexa, primeiramente usei a API indicada, e tendo o retorno dela como JSON, depois fiz a contabilização se todos os CEPs tinham 8 dígitos ou não, após isso comparei os dados recebidos da API com os da Base de dados, e identificando as incongruências existentes, depois, como report recebemos os nomes das pessoas que estão com os endereços inválidos e o que deveria estar no lugar do que foi colocado.

  - Excluindo nomes com erros:
    - Após todas as validações concluídas, inseri todas elas dentro de um código para conseguir remover as linhas que tem dados incorretos, para assim podermos levar para uma comparação com o sistema

- Comparação com o Sistema:
    - Concluindo, peguei a base de dados final com os nomes restantes sem nenhum erro de dados, e a partir dela fiz uma comparação com os dados da planilha de sistema, comparando CPF com CPF, nome com nome, etc, analisando também se há dados que precisam ser atualizados ou não, e se ha clientes ja existentes na base.
 
- Criação JSON:
  - Criei um JSON levando em conta as informações da base de dados e o modelo pedido.

- Criação XLSX:
  - Com os resultados obtidos, consegui gerar um xlsx mostrando os  que não se enquadravam e porquê
