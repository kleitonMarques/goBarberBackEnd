# Passo a passo para subir a aplicação

## NODE
Versão '12.16.1'

## DOCKER E BANCO DE DADOS
- Instalar o docker engine pelo terminal
- Baixar a imagem do postgres no docker
```
docker run --name gostack_postgres -e POSTGRES_PASSWORD=docker -p 5432:5432 -d postgres
```

- Comandos útils para Docker
```
docker ps -a
docker start ID
docker stop ID
docker container rm <container ID> <container ID>
```

- Atualizando apt
```
sudo apt update
```

- Se não tiver o snap instalado no seu ubuntu (terminal), será necessário instalar
```
sudo apt install snapd
```

Instalar dbeaver com Snap
```
sudo snap install dbeaver-ce
```

- Utilizando o dbeaver, inicie o postegres clicando em 'nova conexão'
- selecionando postgres e mantendo a senha 'docker' colocada na criação da imagem acima
- Na aba PostgresSQL selecione a opção 'Show all databases'
- Clicando com o botão direito do mouse em Postgres selecione 'Criar' => 'Banco de dados'
- Coloque o mesmo nome informado no arquivo na proprieda 'database' do arquivo 'ormconfig.json'

## CRIANDO AS MIGRATIONS NO BANCO
- Executando as migrations
```
yarn typeorm migration:run
```

- Caso em momento precise reverter o que foi criado no banco durante o desenvolvimento
```
yarn typeorm migration:revert
```

- Caso precise criar um nova migration
```
yarn typeorm migration:create -n NameMigration
```

- Para verificar as migrations que foram executadas
```
yarn typeorm migration:show
```

- Caso a migrations ja tenha sido mergeada, não é possivel fazer uma alteração no banco utilizando o 'revert', é necessário criar outra migration


## INICIANDO PROJETO NO AMBIENTE DE LOCAL
- Instalar todas as dependência
```
yarn
```

- Start do projeto
```
yarn dev:server
```

# Conceitos da arquitetura

## MODEL
- É a representação de como um dado é salvo dentro da aplicação

## Repositorio
- Que vai trabalhar com esse dado Listar/Deletar/Criar/Alterar

## Service
- Armazena a regra de negócio da aplicação
- O service nunca tem acesso a requisiçao e a resposta, tem acesso apenas ao que recebe do dado, 'request'

# Sequência de criação de uma nova rota