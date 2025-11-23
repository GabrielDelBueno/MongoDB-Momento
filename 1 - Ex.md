Relatório Empresa Momento
1. Conhecendo a Empresa
Descrição: Relatório geral sobre a empresa Momento, apresentando visão sobre estrutura, departamentos, escritórios e equipe.

1.1 Informações Gerais
Total de funcionários: 24
Funcionários no Departamento de Tecnologia: 6
Total de departamentos: 7
Tecnologia
Recursos Humanos
Dados
Executivo
Vendas
Marketing
Financeiro
Total de escritórios: 4
Países: IRE, ENG, USA, EQU
1.2 Metodologia
Foram utilizados métodos como find, $group e $sum para realizar consultas no MongoDB, garantindo a apuração precisa das informações.

1.3 Scripts Utilizados
Inserção de funcionário:

db.funcionarios.insertOne({
  "nome": "Bianca Costa de Melo",
  "salario": 2000,
  "departamento": ObjectId('85992103f9b3e0b3b3c1fe74'),
  "cargo": "Desenvolvedora",
  "escritorio": "São Paulo",
  "dataAdmissao": "2026-01-01",
  "email": "bianca.costamelo1@gmail.com"
})
Contagem de funcionários total:

db.funcionarios.countDocuments()
Contagem de funcionários por departamento:

db.funcionarios.find({departamento: ObjectId("85992103f9b3e0b3b3c1fe74")}).count()
Listagem de departamentos:

db.departamentos.aggregate([
  { $project: { _id: 0, nome: 1 } },
  { $group: {
      _id: null,
      nomes: { $push: "$nome" },
      total: { $sum: 1 }
  }}
])
Listagem de escritórios por país:

db.escritorios.aggregate([
  { $project: { _id: 0, pais: 1 } },
  { $group: {
      _id: null,
      nomes: { $push: "$pais" },
      total: { $sum: 1 }
  }}
])
