Relatório Empresa Momento
Nível 01: Conhecendo a Empresa
Descrição: Relatório geral sobre a empresa momento para conhecer mais sobre a empresa
1: Funcionários que temos ao total na empresa: 24

2: Funcionários que trabalham no Departamento de Tecnologia: 6

3: Liste todos os departamentos que existem na empresa. Quantos são?:

'Tecnologia',
'Recursos Humanos',
'Dados',
'Executivo',
'Vendas',
'Marketing',
'Financeiro'
total: 7

4: Quantos escritórios a Momento possui? Em quais países?

'IRE',
'ENG',
'USA',
'EQU'
total: 4

Metodologia:
Foram utilizados métodos como: find, $group e $sum para fazer as consultas no mongoBD.

Informações:
Scripts usados:

1

db.funcionarios.countDocuments()
2

db.funcionarios.find({departamento: ObjectId("85992103f9b3e0b3b3c1fe74")}).count()
3

db.departamentos.aggregate([
  { $project: { _id: 0, nome: 1 } },
  { 
    $group: {
      _id: null,
      nomes: { $push: "$nome" },
      total: { $sum: 1 }
    }
  }
])
4

db.escritorios.aggregate([
  { $project: { _id: 0, pais: 1 } },
  { 
    $group: {
      _id: null,
      nomes: { $push: "$pais" },
      total: { $sum: 1 }
    }
  }
])

Conclusão do Relatório Momento - Nível 01: Conhecendo a Empresa
O Relatório Momento - Nível 01: Conhecendo a Empresa forneceu uma visão inicial e quantitativa da estrutura organizacional da Momento. Os dados coletados revelam que a empresa opera com um total de 24 funcionários distribuídos por 7 departamentos distintos: Tecnologia, Recursos Humanos, Dados, Executivo, Vendas, Marketing e Financeiro. Notavelmente, o Departamento de Tecnologia representa uma fatia significativa, contando com 6 funcionários.
