# Config Server Profile  

Repositório destinado para configurações sensiveis das aplicações que compoem o ecossistema Brazona Tech.

Qualquer variavel necessária para aplicação ou para o ambiente k8s, estão disponíveis nesse repositório, através do pipeline do github, as informações alteradas nos arquivos são aplicadas nos respectivos ambientes.

## Estrutura do projeto

``` text
├── application
│   └── local
│       └── application.yml
│   └── dsv
│       └── application.yml
│       └── configmap.yml
│       └── .env
│   └── hmg
│       └── application.yml
│       └── configmap.yml
│       └── .env
│   └── stg
│   └── prd
├── docs
│   └── CONTRIBUTING.md
│   └── CODE_OF_CONDUCT.md
│   └── PULL_REQUEST_TEMPLATE.md
└── README.md
```

### Detalhes da Estrutura

A estrutura do repositório segue um padrão de pasta e arquivos para organização e correto aplicação do pipeline.

``` text
│   └── dsv
│       └── application.yml
│       └── configmap.yml
│       └── .env
```

- ***application.yml*** : Arquivo com as propriedades da aplicação.

- ***configmap.yml*** : Arquivo com os valores das variáveis de ambiente no **K8S**

- ***.env*** : Arquivo com os valores das variáveis de ambiente **localhost**, além de fornecer valores para o pipeline de build e deploy.

## Fluxo de Trabalho - Deploy Ambientes

O fluxo de trabalho são processos definidos para dar direção a etapa de desenvolvimento , homologação e lançamento.

As alterações são aplicadas em determinado ambiente através das **branchs**, ao publicar uma alteração numa das branchs ***principais*** o pipeline executa a atualização, a tabela abaixo descreve a relação entre branch e o respectivo ambiente:

### Tabela Branch x Ambiente

| Branch | Ambiente |
| --- | --- |
| develop | Aplica no ambiente __DSV__ |
| release/** | Aplica no ambiente __HMG__ |
| pre-release/** | Aplica no ambiente __STG__ |
| main | Aplica no ambiente __PRD__ |

## Licença

> [!IMPORTANT]
> *O código fonte neste projeto não possui licença de uso.*

É terminantemente proibido reproduzir, distribuir, alterar, utilizar engenharia reversa ou valer-se de qualquer tentativa de reverter ao seu código-fonte qualquer dos componentes que compõem o SOFTWARE, bem como utilizar subterfúgios para burlar a quantidade de usuários licenciados.
