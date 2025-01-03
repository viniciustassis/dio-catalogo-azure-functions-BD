# Gerenciador de Catálogos da Netflix com Azure Functions e Banco de Dados
Este projeto implementa um gerenciador de catálogos para a Netflix utilizando o Azure Functions para processamento serverless e CosmosDB como banco de dados, integrados a um Azure Storage Account para armazenar arquivos. A solução é escalável e otimizada para a nuvem.

## Estrutura do projeto
```
/GerenciadorCatalogosNetflix
│
├── Infraestrutura
│   ├── templates/          # Modelos para criação de recursos no Azure
│   └── setup.sh            # Script para automação da configuração inicial
│
├── Functions
│   ├── SaveToStorage/      # Azure Function para salvar no Storage Account
│   ├── SaveToCosmosDB/     # Azure Function para salvar registros no CosmosDB
│   ├── FilterRecords/      # Azure Function para filtrar registros
│   └── ListRecords/        # Azure Function para listar registros
│
└── README.md
```

## Instruções de Deploy

### Configurar Infraestrutura
```sh
az group create --name GerenciadorNetflix --location eastus
az storage account create --name NetflixStorage --resource-group GerenciadorNetflix --location eastus --sku Standard_LRS
az cosmosdb create --name NetflixCatalog --resource-group GerenciadorNetflix
```

### Deploy das Azure Functions
```sh
func azure functionapp publish <nome-da-funcao>
```

### Configurar conexões
Atualize as variáveis de ambiente nas Azure Functions com as strings de conexão do Storage Account e do CosmosDB