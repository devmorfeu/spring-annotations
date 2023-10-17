# Anotações do Framework Spring

_Este documento descreve várias anotações disponíveis no Spring Framework, organizadas por módulos em ordem alfabética._

## Índice

- [Spring Beans 6.0.12](#spring-beans)
- [Spring Boot 3.1.4](#spring-boot)
- [Spring Cloud AWS 3.0.2](#spring-cloud-aws)
- [Spring Cloud Openfeign 4.0.4](#spring-cloud-openfeign)
- [Spring Context 6.0.12](#spring-context)
- [Spring Data JPA 3.1.5](#spring-data-jpa)

## Spring-beans

${\color{yellow}@ Autowired}$ : _@Autowired é usada em Spring Framework para indicar que uma dependência deve ser automaticamente injetada. Ela pode ser usada em construtores, campos, métodos ou parâmetros._

**Parâmetros:**

- `required`: _valor booleano que define se a dependência anotada é obrigatória ou opcional._

${\color{yellow}@Configurable}$ : _@Configurable é usada para marcar uma classe como elegível para configuração controlada pelo Spring._

**Parâmetros:**

- `value`: _O nome da definição de bean que serve como modelo de configuração. Esse valor permite especificar o nome da definição de bean que deve ser usada para configurar a classe._
- `autowire`: _Define se as dependências devem ser injetadas via autowiring. Por padrão, autowire é definido como Autowire.NO, o que significa que as dependências não serão injetadas automaticamente. Você pode definir isso como **Autowire.BY_TYPE** ou **Autowire.BY_NAME** se desejar realizar a injeção automática de dependências._
- `dependencyCheck`: _Define se a verificação de dependências deve ser executada para objetos configurados. Se definido como true, o contêiner Spring verificará se todas as dependências estão satisfeitas. O padrão é false._
- `preConstruction`: _Define se as dependências devem ser injetadas antes da construção do objeto. Se definido como true, as dependências serão injetadas antes que o construtor seja chamado. O padrão é false._

${\color{yellow}@Lookup}$ : _@Lookup é usada para criar métodos de pesquisa que permitem obter instâncias de beans gerenciados pelo Spring._

**Parâmetros:**

- `value`: _Esse atributo permite sugerir o nome do bean de destino a ser pesquisado. Se não for especificado, o bean de destino será resolvido com base na declaração do tipo de retorno do método anotado._

${\color{yellow}@Qualifier}$ : _@Qualifier é usada como um qualificador para beans candidatos durante a injeção de dependência._

**Parâmetros:**

- `value`: _Atributo que permite especificar um valor que será usado para qualificar um bean durante a injeção de dependência._

${\color{yellow}@ Value}$ : _@Value é usada para indicar um valor padrão ou expressão para um campo, método ou parâmetro de método/constructor anotado. Geralmente, essa anotação é usada para injetar valores por meio de expressões baseadas em SpEL._

**Parâmetros:**

- `value`: _Usado para especificar a expressão real do valor que será injetado._

## Spring-boot

${\color{yellow}@ AutoConfiguration}$ : _@AutoConfiguration é uma anotação do Spring Boot que permite configurar explicitamente o nome do bean associado a uma classe de autoconfiguração e especificar classes que devem ser aplicadas antes ou depois dela. Isso ajuda a controlar a ordem de configuração automática no contexto do aplicativo._

**Parâmetros:**

- `value`: _Define explicitamente o nome do bean associado à classe **@AutoConfiguration**. Se não for especificado, um nome de bean será gerado automaticamente._
- `before`: _Especifica as classes de autoconfiguração que ainda não devem ser aplicadas antes da classe **@AutoConfiguration**._
- `beforeName`: _Define os nomes das classes de autoconfiguração que ainda não devem ser aplicadas antes da classe **@AutoConfiguration**._
- `after`: _Especifica as classes de autoconfiguração que já devem ter sido aplicadas antes da classe **@AutoConfiguration**._
- `afterName`: _Define os nomes das classes de autoconfiguração que já devem ter sido aplicadas antes da classe **@AutoConfiguration**._

${\color{yellow}@ AutoConfigureAfter}$ : _@AutoConfigureAfter é uma anotação do Spring Boot que especifica classes de autoconfiguração que devem ser aplicadas depois de uma determinada classe de autoconfiguração, controlando a ordem de configuração automática._

**Parâmetros:**

- `value`: _Especifica as classes de autoconfiguração que devem ser aplicadas antes da classe anotada, controlando a ordem de configuração automática._
- `name`: _Define os nomes das classes de autoconfiguração que devem ser aplicadas antes da classe anotada, também controlando a ordem de configuração automática. Esta opção foi adicionada na versão 1.2.2 do Spring Boot._

${\color{yellow}@ AutoConfigureBefore}$ : _@AutoConfigureBefore é uma anotação do Spring Boot que especifica classes de autoconfiguração que devem ser aplicadas antes de uma determinada classe de autoconfiguração, controlando a ordem de configuração automática._

**Parâmetros:**

- `value`: _Especifica as classes de autoconfiguração que devem ser aplicadas antes da classe anotada, controlando a ordem de configuração automática._
- `name`: _Define os nomes das classes de autoconfiguração que devem ser aplicadas antes da classe anotada, também controlando a ordem de configuração automática. Esta opção foi adicionada na versão 1.2.2 do Spring Boot._

${\color{yellow}@ AutoConfigureOrder}$ : _@AutoConfigureOrder é uma anotação do Spring Boot que permite especificar a ordem de prioridade de classes de configuração automática, controlando a sequência de configuração durante a inicialização do aplicativo._

**Parâmetros:**

- `value`: _permite definir a prioridade de configuração automática, onde o padrão é 0. Esse valor determina a ordem de execução das classes de configuração automática durante a inicialização do aplicativo Spring Boot. Quanto menor o valor, maior a prioridade._

${\color{yellow}@ AutoConfigurationPackage}$ : _@AutoConfigurationPackage é uma anotação do Spring Boot que escaneia e registra automaticamente pacotes para configuração automática no contexto do aplicativo. Ela identifica o pacote da classe anotada e escaneia outros pacotes a partir dele._

**Parâmetros:**

- `basePackages`: _Path de pacotes do projeto para verificar propriedades de configuração._
- `basePackageClasses`: _Alternativa ("Type-safe") especificando os pacotes para verificar as propriedades de configuração. O pacote de cada classe especificada será verificado._

${\color{yellow}@BatchDataSource}$ : _@BatchDataSource é uma anotação do Spring Boot usada para configurar um **DataSource** específico para o processamento de lotes em aplicações Spring Batch, permitindo o isolamento dos recursos de banco de dados para tarefas de lote._

${\color{yellow}@ConditionalOnBean}$ : _@ConditionalOnBean é uma anotação do Spring Boot que condiciona a ativação de um componente somente se um determinado bean estiver presente no contexto da aplicação. Isso permite controlar a inicialização de componentes com base na existência de outros beans._

**Parâmetros:**

- `value`: _Especifica as classes de beans cuja presença no contexto da aplicação será verificada para a condição._
- `type`: _Especifica os nomes de classes de beans cuja presença no contexto da aplicação será verificada._
- `annotation`: _Especifica os tipos de anotações de classe que decoram os beans a serem verificados._
- `name`: _Especifica os nomes de beans cuja presença no contexto da aplicação será verificada._
- `search`: _Define a estratégia de pesquisa para determinar se o contexto de aplicação hierárquico (contextos pai) deve ser considerado._
- `parameterizedContainer`: _Especifica classes adicionais que podem conter tipos de beans específicos em seus parâmetros genéricos._

${\color{yellow}@ConditionalOnClass}$ : _@ConditionalOnClass é uma anotação do Spring Boot que condiciona a ativação de um componente somente se uma ou mais classes especificadas estiverem presentes no classpath da aplicação. Isso permite controlar a inicialização de componentes com base na disponibilidade de classes._

**Parâmetros:**

- `value`: _Especifica as classes cuja presença no classpath é necessária para ativar a condição._
- `name`: _Especifica os nomes de classes cuja presença no classpath é necessária._

${\color{yellow}@ConditionalOnCloudPlatform}$ : _@ConditionalOnCloudPlatform é uma anotação do Spring Boot que condiciona a ativação de um componente com base na plataforma em nuvem especificada, permitindo configurar componentes para diferentes ambientes de nuvem, como AWS, Google Cloud ou Azure._

**Parâmetros:**

- `value`: _Especifica a plataforma em nuvem esperada para ativar a condição._

${\color{yellow}@ConditionalOnDefaultWebSecurity}$ : _@ConditionalOnDefaultWebSecurity é uma anotação de condição usada no Spring Boot para ativar uma configuração específica de segurança web padrão quando nenhum outro mecanismo de segurança personalizado é configurado na aplicação. Isso fornece uma configuração de segurança web básica, como autenticação de formulário, se nenhum outro mecanismo de segurança estiver presente._

${\color{yellow}@ConditionalOnEnabledResourceChain}$ : _@ConditionalOnEnabledResourceChain é uma anotação de condição usada no Spring Boot para verificar se a cadeia de recursos (Resource Chain) está habilitada na aplicação, permitindo a personalização de recursos, como arquivos estáticos e cache, em aplicativos da web. Isso permite a configuração avançada de recursos, como otimização de cache e versão de recursos._

${\color{yellow}@ConditionalOnExpression}$ : _@ConditionalOnExpression é uma anotação do Spring Boot que condiciona a ativação de um componente com base em uma expressão SpEL (Spring Expression Language) avaliada em tempo de execução, permitindo ativar componentes com base em regras lógicas definidas na expressão._

**Parâmetros:**

- `value`: _Especifica a expressão SpEL a ser avaliada em tempo de execução. Se a expressão retornar **true**, a condição é ativada. Caso contrário, a condição é desativada. O valor padrão é "**true**"._

${\color{yellow}@ConditionalOnGraphQLSchema}$ : _@ConditionalOnGraphQLSchema é uma anotação no Spring Boot que permite condicionar o carregamento de configurações com base na presença de um esquema GraphQL na aplicação, garantindo que as configurações sejam aplicadas somente quando o esquema estiver disponível._

${\color{yellow}@ConditionalOnJava}$ : _@ConditionalOnJava é uma anotação do Spring Boot que condiciona a ativação de um componente com base na versão da plataforma Java, permitindo que os componentes sejam ativados apenas quando a versão Java especificada estiver presente._

**Parâmetros:**

- `range`: _Configura se o valor especificado em **value()** é considerado um limite superior exclusivo ou um limite inferior inclusivo. O padrão é **Range.EQUAL_OR_NEWER** (igual ou mais recente)._
- `value`: _Especifica a versão da plataforma Java a ser verificada._

${\color{yellow}@ConditionalOnJndi}$ : _@ConditionalOnJndi é uma anotação do Spring Boot que condiciona a ativação de um componente com base na disponibilidade de um recurso JNDI (Java Naming and Directory Interface), permitindo que componentes sejam ativados apenas quando o recurso JNDI especificado estiver disponível._

**Parâmetros:**

- `value`: _Especifica os locais JNDI em que pelo menos um deve existir para ativar a condição. Se nenhum local for especificado, a condição será ativada apenas com base na presença de um **InitialContext**._

${\color{yellow}@ConditionalOnMissingBean}$ : _@ConditionalOnMissingBean é uma anotação do Spring Boot que condiciona a ativação de um componente somente se não houver uma instância de bean do mesmo tipo já definida no contexto, permitindo substituir beans padrão com implementações personalizadas._

**Parâmetros:**

- `value`: _Especifica os tipos de classes de beans a serem verificados quanto à ausência._
- `type`: _Especifica os nomes das classes de beans a serem verificados quanto à ausência._
- `ignored`: _Define os tipos de classes de beans a serem ignorados ao identificar beans correspondentes (desde a versão 1.2.5)._
- `ignoredType`: _Define os nomes das classes de beans a serem ignorados ao identificar beans correspondentes (desde a versão 1.2.5)._
- `annotation`: _Especifica as anotações de nível de classe a serem verificadas quanto à ausência._
- `name`: _Define os nomes de beans a serem verificados quanto à ausência._
- `search`: _Estratégia para considerar a hierarquia do contexto da aplicação._
- `parameterizedContainer`: _Classes adicionais que podem conter os tipos de beans especificados em seus parâmetros genéricos (desde a versão 2.1.0)._

${\color{yellow}@ConditionalOnMissingClass}$ : _@ConditionalOnMissingClass é uma anotação do Spring Boot que ativa um componente somente se uma ou mais classes especificadas não estiverem presentes no classpath._

**Parâmetros:**

- `value`: _Especifica os tipos de classes a serem verificados quanto à ausência._

${\color{yellow}@ConditionalOnMissingFilterBean}$ : _@ConditionalOnMissingFilterBean é uma anotação de condição no Spring Boot que verifica se não existe um bean de filtro específico no contexto da aplicação. Isso permite personalizar a configuração de filtros, garantindo que um filtro personalizado seja aplicado apenas se nenhum filtro com o mesmo nome estiver presente._

${\color{yellow}@ConditionalOnNotWarDeployment}$ : _@ConditionalOnMissingClass ativa um componente somente se o app Spring não estiver sendo implantado como um arquivo **WAR**._

${\color{yellow}@ConditionalOnNotWebApplication}$ : _@ConditionalOnNotWebApplication ativa um componente somente se o app Spring não for uma aplicação da web._

${\color{yellow}@ConditionalOnProperty}$ : _@ConditionalOnProperty ativa um componente com base na presença ou valor de uma propriedade de configuração._

**Parâmetros:**

- `prefix`: _Um prefixo que deve ser aplicado a cada propriedade._
- `name`: _O nome das propriedades a serem testadas, com suporte para notação de traço._
- `havingValue`: _A representação em string do valor esperado para as propriedades._
- `matchIfMissing`: _Especifica se a condição deve corresponder quando a propriedade está ausente._

${\color{yellow}@ConditionalOnRepositoryType}$ : _@ConditionalOnRepositoryType é uma anotação que condiciona a configuração de beans com base no tipo de repositório especificado, como CASSANDRA, MONGODB ou Neo4j. Isso permite ajustar o comportamento com base no armazenamento de dados escolhido._

**Parâmetros:**

- `store`: _Especifica o nome do armazenamento de dados, como "cassandra", "couchbase", "mongodb" ou "neo4j", que respalda os repositórios._
- `type`: _Define o tipo de repositório necessário, como RepositoryType.AUTO, RepositoryType.IMPERATIVE, RepositoryType.NONE ou RepositoryType.REACTIVE._

${\color{yellow}@ConditionalOnResource}$ : _@ConditionalOnResource é uma anotação de condição no Spring que ativa uma configuração se um determinado recurso estiver no classpath._

**Parâmetros:**

- `resources`: _Uma ou mais localizações de recursos que devem existir no classpath. A configuração só será ativada se pelo menos uma dessas localizações existir._

${\color{yellow}@ConditionalOnSingleCandidate}$ : _@ConditionalOnSingleCandidate é uma anotação de condição do Spring que ativa a configuração se houver exatamente um candidato (bean) apropriado no contexto do aplicativo._

**Parâmetros:**

- `type`: _O tipo do bean candidato._
- `search`: _Estratégia para considerar o contexto da hierarquia do aplicativo. Por default o valor utilizado é **SearchStrategy.ALL**._

${\color{yellow}@ConditionalOnWarDeployment}$ : _@ConditionalOnWarDeployment é uma anotação do Spring Boot que ativa a configuração somente quando o aplicativo está sendo implantado como um arquivo **WAR** (Web Application Archive). Ela permite que a configuração seja condicional com base no tipo de implantação._

${\color{yellow}@ConditionalOnWebApplication}$ : _@ConditionalOnWebApplication é uma anotação do Spring Boot que ativa a configuração apenas quando o aplicativo é uma aplicação web, como uma Servlet ou uma aplicação Spring MVC._

**Parâmetros:**

- `type`: _Define o tipo de aplicação web, sendo **ANY** , **SERVLET** ou **REACTIVE**._

${\color{yellow}@ConfigurationProperties}$ : _@ConfigurationProperties mapeia propriedades de configuração definidas em arquivos de propriedades ou YAML para objetos Java._

**Parâmetros:**

- `prefix`: O prefixo das propriedades a serem vinculadas.
- `ignoreInvalidFields`: Sinalizador para indicar que, ao vincular a este objeto, campos inválidos devem ser ignorados.
- `ignoreUnknownFields`: Sinalizador para indicar que, ao vincular a este objeto, campos desconhecidos devem ser ignorados.

${\color{yellow}@ConfigurationPropertiesBinding}$ : _@ConfigurationPropertiesBinding é uma anotação do Spring Boot usada para criar conversores personalizados para propriedades de configuração._

${\color{yellow}@ConfigurationPropertiesScan}$ : _@ConfigurationPropertiesScan é uma anotação do Spring Boot usada para escanear pacotes em busca de classes de propriedades de configuração._

**Parâmetros:**

- `basePackages`: _Path de pacotes do projeto para verificar propriedades de configuração._
- `basePackageClasses`: _Alternativa ("Type-safe") especificando os pacotes para verificar as propriedades de configuração. O pacote de cada classe especificada será verificado._

${\color{yellow}@ConstructorBinding}$ : _@ConstructorBinding é uma anotação do Spring Boot que indica a vinculação de propriedades de configuração a construtores, facilitando a criação de objetos imutáveis._

${\color{yellow}@DefaultValue}$ : _@DefaultValue é uma anotação do Spring Boot que pode ser usada para especificar o valor padrão ao vincular a uma propriedade imutável. Essa anotação também pode ser usada com propriedades aninhadas para indicar que um valor deve sempre ser vinculado (em vez de vincular nulo). O valor desta anotação só será utilizado se a propriedade não for encontrada nas fontes de propriedades utilizadas pelo **Binder**._

**Parâmetros:**

- `value`: _O valor padrão da propriedade. Pode ser uma matriz de valores para propriedades de coleção ou baseadas em matriz._

${\color{yellow}@DataSizeUnit}$ : _@DataSizeUnit é uma anotação do Spring Boot que pode ser usada para alterar a unidade padrão usada ao converter um DataSize._

**Parâmetros:**

- `value`: _O **DataUnit** a ser usado se nenhum for especificado._

${\color{yellow}@DeprecatedConfigurationProperty}$ : _@DeprecatedConfigurationProperty é uma anotação do Spring Boot usada para marcar propriedades de configuração como obsoletas e fornecer uma mensagem de aviso quando são usadas._

**Parâmetros:**

- `reason`: _O motivo da descontinuação._
- `replacement`: _O valor que deve ser usado (se houver)._

${\color{yellow}@DependsOnDatabaseInitialization}$ : _@DependsOnDatabaseInitialization é uma anotação do Spring Boot que define que um bean depende da inicialização do banco de dados, garantindo que a inicialização do banco de dados seja concluída antes do bean ser criado._

${\color{yellow}@Delimiter}$ : _@Delimiter é uma anotação do Spring Boot que permite definir um delimitador personalizado para valores de propriedades de configuração, especialmente útil ao lidar com listas em propriedades._

**Parâmetros:**

- `value`: _O delimitador a ser usado ou **NONE** se todo o conteúdo precisar ser tratado como um único elemento._

${\color{yellow}@DurationFormat}$ : _@DurationFormat é uma anotação do Spring Boot que permite personalizar o formato de durações, como as usadas em propriedades de configuração, para facilitar a leitura e escrita._

**Parâmetros:**

- `value`: _O estilo do formato de duração._

${\color{yellow}@EnableAutoConfiguration}$ : _@EnableAutoConfiguration é uma anotação do Spring Boot que ativa a configuração automática, permitindo que o Spring Boot configure automaticamente o aplicativo com base nas dependências e no ambiente._

**Parâmetros:**

- `exclude`: _Especifica classes de configuração automática a serem excluídas._
- `excludeName`: _Especifica nomes de classes de configuração automática a serem excluídos. (Adicionado na versão 1.3.0)._

${\color{yellow}@EnableConfigurationProperties}$ : _@EnableConfigurationProperties é uma anotação do Spring Boot usada para habilitar a vinculação automática de propriedades de configuração a classes de configuração._

**Parâmetros:**

- `value`: _Maneira conveniente de registrar rapidamente beans anotados **@ConfigurationProperties** com Spring._

${\color{yellow}@EntityScan}$ : _@EntityScan é uma anotação usada no Spring para escanear e identificar classes de entidade JPA em um pacote específico ou seus subpacotes, permitindo que o Spring Boot encontre e gerencie entidades persistentes._

**Parâmetros:**

- `basePackages`: _Path de pacotes do projeto para verificar propriedades de configuração._
- `basePackageClasses`: _Alternativa ("Type-safe") especificando os pacotes para verificar as propriedades de configuração. O pacote de cada classe especificada será verificado._

${\color{yellow}@FlywayDataSource}$ : _@FlywayDataSource é uma anotação no Spring Boot que permite configurar um data source separado exclusivamente para o Flyway, uma ferramenta de migração de banco de dados. Isso é útil para separar a fonte de dados usada para migrações de banco de dados da fonte de dados principal da aplicação._

${\color{yellow}@ImportAutoConfiguration}$ : _@ImportAutoConfiguration é uma anotação do Spring Boot que permite importar classes de configuração automática personalizada para o aplicativo Spring Boot, estendendo as configurações padrão._

**Parâmetros:**

- `value / classes`: _Especifica classes de configuração automática personalizada a serem importadas. Pode ser definido diretamente ou por meio de um arquivo no **META-INF/spring** que lista as classes a serem importadas._
- `exclude`: _Especifica classes de configuração automática a serem excluídas, garantindo que não sejam aplicadas._

${\color{yellow}@JsonComponent}$ : _@JsonComponent é uma anotação do Spring Boot usada para registrar um componente como um manipulador de serialização e desserialização JSON, permitindo personalizar a forma como objetos são convertidos para JSON e vice-versa._

**Parâmetros:**

- `value`: _Indica um nome lógico sugerido para o componente e pode ser convertido em um **bean**. Padrão é uma string vazia._
- `type`: _Define os tipos que o componente manipula para serialização/desserialização. Essa configuração é especialmente importante para deserializadores de chaves (**KeyDeserializer**) e pode ser usada para limitar o tratamento a subclasses de tipos inferidos._
- `scope`: _Especifica o escopo sob o qual o serializador/desserializador deve ser registrado com o módulo. O valor padrão é **Scope.VALUES**, que se aplica a serializadores/desserializadores de conteúdo de valor. O escopo **Scope.KEYS** pode ser usado para serializadores/desserializadores de chaves._

${\color{yellow}@JsonMixin}$ : _@JsonMixin é uma anotação que permite criar uma classe que define anotações personalizadas para controlar a forma como objetos são convertidos em JSON ou de JSON para objetos, aplicando essas anotações a classes específicas. Isso facilita a personalização da serialização e desserialização JSON._

**Parâmetros:**

- `value`: _Permite especificar as classes que serão usadas como classes de mistura (mixin classes) para controlar a serialização e desserialização de objetos JSON._

${\color{yellow}@LiquibaseDataSource}$ : _@LiquibaseDataSource é uma anotação usada no Spring Boot para configurar um DataSource específico para o Liquibase, uma ferramenta de controle de versionamento de banco de dados. Isso permite que você defina um DataSource separado para as migrações do Liquibase em relação ao DataSource principal da aplicação._

${\color{yellow}@Name}$ : _@Name é uma anotação do Spring Boot que pode ser usada para especificar o nome ao vincular a uma propriedade imutável._

**Parâmetros:**

- `value`: _O nome da propriedade a ser usada para associação._

${\color{yellow}@Nested}$ : _@Nested é uma meta-anotação do Spring Boot que deve ser adicionada às anotações que indicam que um campo é do tipo aninhado. Usado para garantir que as dicas de reflexão corretas sejam registradas._

${\color{yellow}@NestedConfigurationProperty}$ : _@NestedConfigurationProperty é uma anotação do Spring Boot usada para indicar que uma propriedade de configuração complexa está aninhada dentro de outra propriedade de configuração._

${\color{yellow}@PeriodFormat}$ : _@PeriodFormat é uma anotação do Spring Boot que permite personalizar o formato de períodos, como os usados em propriedades de configuração, para facilitar a leitura e escrita._

**Parâmetros:**

- `value`: _O estilo de formato do período._

${\color{yellow}@PeriodUnit}$ : _@PeriodUnit é uma anotação do Spring Boot que permite definir a unidade padrão para valores de período em propriedades de configuração, simplificando a configuração._

**Parâmetros:**

- `value`: _A unidade de período a ser usada se nenhuma for especificada._

${\color{yellow}@QuartzDataSource}$ : _@QuartzDataSource anotação de um DataSource a ser injetado na configuração automática do Quartz. Pode ser usado em uma fonte de dados secundária, caso exista outra marcada como @Primary._

${\color{yellow}@QuartzTransactionManager}$ : _@QuartzTransactionManager anotação de TransactionManager a ser injetado na configuração automática do Quartz. Pode ser utilizado em um gerenciador de transações secundário, caso exista outro marcado como @Primary._

${\color{yellow}@ServletComponentScan}$ : _@ServletComponentScan é uma anotação do Spring Boot usada para escanear pacotes em busca de classes Servlet, Filter e Listener para configuração automática no contexto do aplicativo web._

**Parâmetros:**

- `basePackages`: _Path de pacotes do projeto para verificar propriedades de configuração._
- `basePackageClasses`: _Alternativa ("Type-safe") especificando os pacotes para verificar as propriedades de configuração. O pacote de cada classe especificada será verificado._

${\color{yellow}@SpringBootApplication}$ : _@SpringBootApplication diz ao Spring Boot que essa classe deverá ser usada como base para configurar toda nossa aplicação._

**Parâmetros:**

- `exclude`: Uma matriz de classes de configuração para serem excluídas da configuração automática.
- `excludeName`: Uma matriz de nomes de classes de configuração para serem excluídas da configuração automática.
- `scanBasePackages`: Um ou mais pacotes para serem escaneados em busca de componentes anotados.
- `scanBasePackageClasses`: Uma ou mais classes que servem como base para a varredura de pacotes em busca de componentes anotados.
- `nameGenerator`: Uma classe para gerar nomes de beans automaticamente.
- `proxyBeanMethods`: Uma configuração que controla se os métodos de bean devem ser proxy por CGLIB.

${\color{yellow}@SpringBootConfiguration}$ : _@SpringBootConfiguration é uma anotação do Spring Boot usada para marcar classes de configuração específicas do aplicativo. Ela estende a anotação @Configuration do Spring Framework._

**Parâmetros:**

- `proxyBeanMethods`: _Sinalizador que controla se os métodos de bean devem ser proxy por CGLIB. Por padrão, ele é definido como true. Se definido como false, os métodos de bean não serão proxy._

## Spring-cloud-aws

${\color{yellow}@ AutoConfigureSqs}$ : _@AutoConfigureSqs é usada para importar automaticamente as configurações do Amazon Simple Queue Service (SQS) em testes típicos. Ela simplifica a configuração de testes relacionados ao SQS no Spring Boot. É frequentemente usada em conjunto com @SqsTest para testes mais específicos relacionados ao SQS._

${\color{yellow}@NotificationMessage}$ : _@NotificationMessage é usada para mapear o valor de notificação do Amazon Simple Notification Service (SNS) para uma variável anotada em métodos de controladores. Isso é comumente usado para lidar com a recepção de notificações do SNS em métodos de controle._

${\color{yellow}@NotificationMessageMapping}$ : _@NotificationMessageMapping é uma anotação para mapear métodos que tratam notificações Amazon SNS em controladores Spring, permitindo que os métodos processem mensagens de notificação de forma eficiente em URLs mapeadas._

**Parâmetros:**

- `path`: _Permite que você defina os caminhos que correspondem a esse mapeamento._

${\color{yellow}@NotificationSubject}$ : _@NotificationSubject é usada para pegar o assunto de uma notificação enviada pelo Amazon Simple Notification Service (SNS) e vinculá-lo a uma variável em um método de um controlador. Isso permite que você acesse o assunto da notificação de forma direta e simples em seu código._

${\color{yellow}@NotificationSubscriptionMapping}$ : _@NotificationSubscriptionMapping é usada para mapear um método de um controlador Spring para lidar com solicitações de confirmação de inscrição SNS (Simple Notification Service) quando o cabeçalho da solicitação x-amz-sns-message-type é definido como "SubscriptionConfirmation" e o método HTTP usado é o POST. Além disso, ele define que a resposta a ser enviada deve ter um status HTTP "NO_CONTENT"._

**Parâmetros:**

- `path`: _Permite que você defina os caminhos que correspondem a esse mapeamento._

${\color{yellow}@NotificationUnsubscribeConfirmationMapping}$ : _@NotificationUnsubscribeConfirmationMapping configura um método para receber notificações de cancelamento de inscrição em um endpoint Amazon SNS._

**Parâmetros:**

- `path`: _Permite que você defina os caminhos que correspondem a esse mapeamento._

${\color{yellow}@SqsListener}$ : _@SqsListener é usada para configurar métodos que processam mensagens em filas do Amazon Simple Queue Service (SQS)._

**Parâmetros:**

- `value \ queueNames`: _Especifica os nomes das filas ou URLs que serão ouvidos por este método. Você pode definir uma ou mais filas separadas por vírgulas para que o método processe mensagens de várias filas._
- `factory`: _Permite especificar o nome de um bean que será usado para criar o MessageListenerContainer para lidar com esse endpoint. É útil se você deseja usar uma configuração personalizada para o contêiner. Por padrão, ele procurará um bean adequado no contexto._
- `id`: _Define um identificador para o MessageListenerContainer criado para lidar com esse endpoint. Se você não fornecer um, um identificador padrão será gerado automaticamente._
- `maxConcurrentMessages`: _Define o número máximo de mensagens que podem ser processadas simultaneamente para cada fila. Isso controla quantas mensagens seu método pode lidar de uma só vez._
- `pollTimeoutSeconds`: _Especifica o tempo máximo em segundos que o método aguardará por mensagens em uma chamada de busca ao SQS._
- `maxMessagesPerPoll`: _Define o número máximo de mensagens que podem ser buscadas de uma só vez. Esse valor é útil ao trabalhar com filas SQS com mensagens agrupadas._
- `messageVisibilitySeconds`: _Controla o tempo de visibilidade das mensagens. Isso define quanto tempo as mensagens serão invisíveis após serem recebidas. Isso é útil para garantir que as mensagens não sejam processadas por vários consumidores ao mesmo tempo._

${\color{yellow}@SqsTest}$ : _@SqsTest é usada para testar componentes que se concentram apenas em funcionalidades baseadas em SQS._

**Parâmetros:**

- `useDefaultFilters`: _Define se os filtros padrão devem ser usados em conjunto com a anotação @SpringBootApplication. Você pode configurar essa opção para incluir ou excluir determinados beans ao testar suas funcionalidades SQS._
- `listeners`: _Especifica as classes de ouvintes a serem testadas. Isso permite que você se concentre nos ouvintes relevantes para o teste._
- `properties`: _Permite que você adicione propriedades no formato "chave=valor" ao ambiente do Spring antes da execução do teste._
- `includeFilters \ excludeFilters`: _Filtros que podem ser usados para incluir ou excluir beans do contexto de aplicação. Isso é útil para personalizar o ambiente de teste._

## Spring-cloud-openfeign

${\color{yellow}@CollectionFormat}$ : _@CollectionFormat é usada para indicar qual formato de coleção deve ser usado ao processar um método anotado._

**Parâmetros:**

- `value`: _Permite definir o formato de coleção a ser usado ao processar o método anotado. Você pode especificar o formato desejado, escolhendo entre as opções fornecidas no enum feign.CollectionFormat (ex: CSV ou SSV)_

${\color{yellow}@EnableFeignClients}$ : _@EnableFeignClients é usada para ativar a varredura de interfaces que declaram ser clientes Feign._

**Parâmetros:**

- `basePackages`: _Path de pacotes do projeto para verificar propriedades de configuração._
- `basePackageClasses`: _Alternativa ("Type-safe") especificando os pacotes para verificar as propriedades de configuração. O pacote de cada classe especificada será verificado._
- `defaultConfiguration`: _Permite definir uma configuração personalizada para todos os clientes Feign. Você pode incluir definições de bean de substituição, como decodificadores, codificadores e contratos, para cada cliente Feign. Veja FeignClientsConfiguration para as configurações padrão._
- `clients`: _Lista de classes anotadas com @FeignClient. Quando não estiver vazia, desabilita a varredura no classpath. É útil quando você deseja especificar explicitamente quais classes devem ser tratadas como clientes Feign, em vez de varrer todo o classpath._

${\color{yellow}@FeignClient}$ : _@FeignClient é usada para declarar que uma interface representa um cliente REST Feign._

**Parâmetros:**

- `name`: _Especifica o nome do serviço com um prefixo de protocolo opcional. Você deve especificar um nome para todos os clientes, independentemente de uma URL ser fornecida._
- `contextId`: _Define o nome do bean que será usado em vez de "name", mas não será usado como um ID de serviço._
- `qualifiers`: _Especifica os qualificadores @Qualifiers para o cliente Feign._
- `url`: _Permite especificar uma URL absoluta ou um nome de host resolvível (o protocolo é opcional)._
- `dismiss404`: _Indica se as respostas 404 devem ser decodificadas em vez de gerar exceções Feign._
- `configuration`: _Permite definir uma classe de configuração personalizada para o cliente Feign. Essa classe pode conter definições de beans de substituição, como decodificadores, codificadores e contratos._
- `fallback`: _Define a classe de fallback para a interface do cliente Feign especificada. A classe de fallback deve implementar a interface anotada com @FeignClient e ser um bean Spring válido._
- `fallbackFactory`: _Define uma fábrica de fallback para a interface do cliente Feign especificada. A fábrica de fallback deve produzir instâncias das classes de fallback que implementam a interface anotada com @FeignClient. Consulte FallbackFactory para obter detalhes._
- `path`: _Especifica um prefixo de caminho a ser usado por todas as correspondências de nível de método._
- `primary`: _Indica se o proxy Feign deve ser marcado como um bean primário. O valor padrão é verdadeiro, o que significa que o proxy Feign será o bean primário._

${\color{yellow}@SpringQueryMap}$ : _@SpringQueryMap é a versão Spring MVC equivalente à anotação @QueryMap do OpenFeign. Ela é usada para mapear parâmetros de consulta de solicitação para um método de um controlador Spring. Isso é útil quando você deseja usar um objeto para representar os parâmetros de consulta em vez de anotar cada parâmetro individualmente. A anotação @SpringQueryMap é aplicada a um parâmetro do método e permite que você use um objeto para coletar todos os parâmetros de consulta da solicitação._

## Spring-context

EM BREVE

## Spring-data-jpa

${\color{yellow}@DisabledOnHibernate61}$ : _@DisabledOnHibernate61 é usada para sinalizar casos de teste do JUnit 5 que devem ser desativados (ignorados) quando a versão 6.1 do Hibernate está no classpath do projeto. Isso é útil quando você deseja evitar a execução de testes que podem não ser compatíveis com uma versão específica do Hibernate. Esses testes serão ignorados quando a versão do Hibernate 6.1 estiver presente no projeto._

${\color{yellow}@DisabledOnHibernate62}$ : _@DisabledOnHibernate62 é usada para sinalizar casos de teste do JUnit 5 que devem ser desativados (ignorados) quando a versão 6.1 do Hibernate está no classpath do projeto. Isso é útil quando você deseja evitar a execução de testes que podem não ser compatíveis com uma versão específica do Hibernate. Esses testes serão ignorados quando a versão do Hibernate 6.2 estiver presente no projeto._

${\color{yellow}@EnableEnversRepositories}$ : _@EnableEnversRepositories é usada para habilitar os repositórios do Envers. Ela funciona como uma anotação meta para @EnableJpaRepositories, substituindo a classe de fábrica padrão dos repositórios por EnversRevisionRepositoryFactoryBean._

**Parâmetros:**

- `basePackages`: _Path de pacotes do projeto para verificar propriedades de configuração._
- `basePackageClasses`: _Alternativa ("Type-safe") especificando os pacotes para verificar as propriedades de configuração. O pacote de cada classe especificada será verificado._
- `includeFilters \ excludeFilters`: _Filtros que podem ser usados para incluir ou excluir beans do contexto de aplicação. Isso é útil para personalizar o ambiente de teste._
- `repositoryImplementationPostfix`: _Usado para configurar o sufixo que será anexado ao nome do repositório ao procurar por implementações personalizadas de repositórios. Por padrão, o sufixo é definido como "Impl"._
- `namedQueriesLocation`: _Usado para configurar a localização do arquivo de propriedades que contém as consultas nomeadas (named queries) para os repositórios. Por padrão, se esse atributo não for especificado, a localização padrão será META-INF/jpa-named-queries.properties._
- `queryLookupStrategy`: _Usado para configurar o mecanismo de busca de estratégia de consulta para os métodos de consulta dos seus repositórios. Por padrão, se esse atributo não for especificado, a estratégia padrão é Key.CREATE_IF_NOT_FOUND._
- `repositoryFactoryBeanClass`: _Usado para configurar a classe FactoryBean que será usada para criar instâncias de repositórios. Por padrão, se esse atributo não for especificado, a classe JpaRepositoryFactoryBean é usada como a classe de fábrica. Essa classe é responsável por criar proxies para os seus repositórios e gerenciar a injeção de dependência._
- `repositoryBaseClass`: _Usado para configurar a classe base dos repositórios a serem criados para uma configuração específica. A classe base dos repositórios é a interface que estende a interface JpaRepository e é usada como base para criar instâncias de repositórios._
- `entityManagerFactoryRef`: _Usado para configurar o nome da definição de bean do EntityManagerFactory que deve ser usado para criar os repositórios descobertos por meio dessa anotação. Por padrão, o nome da definição de bean do EntityManagerFactory é "entityManagerFactory"._
- `transactionManagerRef`: _Usado para configurar o nome da definição de bean do PlatformTransactionManager que deve ser usado para criar os repositórios descobertos por meio dessa anotação. Por padrão, o nome da definição de bean do PlatformTransactionManager é "transactionManager"._
- `considerNestedRepositories`: _Usado para configurar se as interfaces de repositório aninhadas (por exemplo, definidas como classes internas) devem ser descobertas pela infraestrutura de repositórios. Por padrão, essa configuração é definida como false, o que significa que as interfaces de repositório aninhadas não são consideradas na descoberta de repositórios._
- `enableDefaultTransactions`: _ Usado para configurar se as transações padrão devem ser habilitadas para os repositórios Spring Data JPA. A configuração padrão é true, o que significa que as transações padrão estão habilitadas. Quando as transações padrão estão habilitadas, as operações realizadas nos métodos dos repositórios JPA são automaticamente envolvidas em transações gerenciadas pelo Spring, garantindo a consistência dos dados._
- `bootstrapMode`: _Usado para configurar quando os repositórios são inicializados durante o ciclo de vida de inicialização do aplicativo. Isso é relevante ao usar o Spring Data JPA e a anotação @EnableEnversRepositories em uma configuração._
- `escapeCharacter`: _Usado para configurar o caractere usado para escapar os caracteres curinga, como _ e %, em consultas derivadas no Spring Data JPA. Em consultas derivadas, você pode usar curingas para correspondência parcial de strings, mas, em alguns casos, você pode querer pesquisar literais que contêm esses caracteres curinga como parte da string em si._

${\color{yellow}@EnableJpaAuditing}$ : _@EnableJpaAuditing é usada para habilitar a auditoria em JPA (Java Persistence API) por meio de configuração por anotações. A auditoria é o processo de rastreamento de ações em entidades JPA, como criação, modificação e exclusão, para fins de registro e monitoramento._

**Parâmetros:**

- `auditorAwareRef`: _Este atributo permite configurar o nome do bean que implementa a interface AuditorAware. Um AuditorAware é usado para procurar o princípio atual que está executando a ação de auditoria. Por padrão, esse atributo está vazio, o que significa que o mecanismo padrão será usado para determinar o principal atual._
- `setDates`: _Este atributo configura se as datas de criação e modificação devem ser definidas. Se for true, as datas de criação e modificação serão definidas automaticamente ao criar ou modificar entidades. Se for false, as datas não serão definidas automaticamente. O valor padrão é true._
- `modifyOnCreate`: _Este atributo configura se a entidade deve ser marcada como modificada na criação. Se for true, a entidade será considerada modificada quando criada. Se for false, a entidade não será marcada como modificada na criação. O valor padrão é true._
- `dateTimeProviderRef`: _Este atributo permite configurar o nome do bean que implementa a interface DateTimeProvider. Um DateTimeProvider é usado para personalizar o objeto TemporalAccessor usado para definir datas de criação e modificação. Se você não especificar um valor para este atributo, o mecanismo padrão será usado._

${\color{yellow}@EnableJpaRepositories}$ : _@EnableJpaRepositories usada para habilitar a criação de repositórios JPA (Java Persistence API) em um aplicativo Spring. Esses repositórios são usados para acessar e manipular entidades de banco de dados comuns em aplicativos Spring Data._

**Parâmetros:**

- `basePackages`: _Path de pacotes do projeto para verificar propriedades de configuração._
- `basePackageClasses`: _Alternativa ("Type-safe") especificando os pacotes para verificar as propriedades de configuração. O pacote de cada classe especificada será verificado._
- `includeFilters \ excludeFilters`: _Filtros que podem ser usados para incluir ou excluir beans do contexto de aplicação. Isso é útil para personalizar o ambiente de teste._
- `repositoryImplementationPostfix`: _Usado para configurar o sufixo que será anexado ao nome do repositório ao procurar por implementações personalizadas de repositórios. Por padrão, o sufixo é definido como "Impl"._
- `namedQueriesLocation`: _Usado para configurar a localização do arquivo de propriedades que contém as consultas nomeadas (named queries) para os repositórios. Por padrão, se esse atributo não for especificado, a localização padrão será META-INF/jpa-named-queries.properties._
- `queryLookupStrategy`: _Usado para configurar o mecanismo de busca de estratégia de consulta para os métodos de consulta dos seus repositórios. Por padrão, se esse atributo não for especificado, a estratégia padrão é Key.CREATE_IF_NOT_FOUND._
- `repositoryFactoryBeanClass`: _Usado para configurar a classe FactoryBean que será usada para criar instâncias de repositórios. Por padrão, se esse atributo não for especificado, a classe JpaRepositoryFactoryBean é usada como a classe de fábrica. Essa classe é responsável por criar proxies para os seus repositórios e gerenciar a injeção de dependência._
- `repositoryBaseClass`: _Usado para configurar a classe base dos repositórios a serem criados para uma configuração específica. A classe base dos repositórios é a interface que estende a interface JpaRepository e é usada como base para criar instâncias de repositórios._
- `entityManagerFactoryRef`: _Usado para configurar o nome da definição de bean do EntityManagerFactory que deve ser usado para criar os repositórios descobertos por meio dessa anotação. Por padrão, o nome da definição de bean do EntityManagerFactory é "entityManagerFactory"._
- `transactionManagerRef`: _Usado para configurar o nome da definição de bean do PlatformTransactionManager que deve ser usado para criar os repositórios descobertos por meio dessa anotação. Por padrão, o nome da definição de bean do PlatformTransactionManager é "transactionManager"._
- `considerNestedRepositories`: _Usado para configurar se as interfaces de repositório aninhadas (por exemplo, definidas como classes internas) devem ser descobertas pela infraestrutura de repositórios. Por padrão, essa configuração é definida como false, o que significa que as interfaces de repositório aninhadas não são consideradas na descoberta de repositórios._
- `enableDefaultTransactions`: _ Usado para configurar se as transações padrão devem ser habilitadas para os repositórios Spring Data JPA. A configuração padrão é true, o que significa que as transações padrão estão habilitadas. Quando as transações padrão estão habilitadas, as operações realizadas nos métodos dos repositórios JPA são automaticamente envolvidas em transações gerenciadas pelo Spring, garantindo a consistência dos dados._
- `bootstrapMode`: _Usado para configurar quando os repositórios são inicializados durante o ciclo de vida de inicialização do aplicativo. Isso é relevante ao usar o Spring Data JPA e a anotação @EnableEnversRepositories em uma configuração._
- `escapeCharacter`: _Usado para configurar o caractere usado para escapar os caracteres curinga, como _ e %, em consultas derivadas no Spring Data JPA. Em consultas derivadas, você pode usar curingas para correspondência parcial de strings, mas, em alguns casos, você pode querer pesquisar literais que contêm esses caracteres curinga como parte da string em si._

${\color{yellow}@EntityGraph}$ : _@EntityGraph é usada para configurar os grafos de entidades (EntityGraphs) que devem ser usados em métodos de repositório JPA no Spring Data. Os grafos de entidades permitem definir quais atributos das entidades associadas devem ser carregados junto com a entidade principal, evitando problemas de carregamento preguiçoso (lazy loading) e melhorando o desempenho de consultas._

**Parâmetros:**

- `type`: _Este atributo configura o tipo do EntityGraph a ser usado. O valor padrão é EntityGraphType.FETCH, que significa que os atributos listados no EntityGraph serão carregados como FetchType.EAGER. Outro valor disponível é EntityGraphType.LOAD, que trata atributos não listados como FetchType.EAGER e os demais de acordo com suas configurações padrão de FetchType._
- `attributePaths`: _Este atributo permite personalizar o grafo de entidades definindo caminhos de atributos que devem ser carregados de forma ad-hoc. Se este atributo for especificado, o nome do EntityGraph (type()) será ignorado e o EntityGraph será considerado como dinâmico. Isso permite que você defina atributos específicos para carregamento em um método de repositório._

${\color{yellow}@Lock}$ : _@Lock é usada para especificar o tipo de bloqueio (LockModeType) a ser usado ao executar uma consulta ou método de CRUD em um repositório JPA no Spring Data. Os bloqueios são usados para controlar o acesso concorrente aos registros do banco de dados, permitindo que você defina como as transações devem travar os registros durante a execução da consulta._

**Parâmetros:**

- `value`: _Este atributo especifica o tipo de bloqueio a ser usado ao executar a consulta ou método de CRUD. Ele deve ser uma constante do tipo LockModeType, que define o modo de bloqueio desejado. Alguns dos valores comuns incluem:
  LockModeType.NONE: Nenhum bloqueio é aplicado (padrão).
  LockModeType.OPTIMISTIC: Bloqueio otimista, onde as alterações no banco de dados são verificadas antes da gravação.
  LockModeType.OPTIMISTIC_FORCE_INCREMENT: Bloqueio otimista com forçar incremento, usado para forçar a atualização do número de versão.
  LockModeType.PESSIMISTIC_READ: Bloqueio pessimista de leitura.
  LockModeType.PESSIMISTIC_WRITE: Bloqueio pessimista de gravação._

${\color{yellow}@Modifying}$ : _@Modifying usada em métodos de consulta para indicar que a consulta é uma consulta modificadora, o que significa que ela realiza operações que modificam os dados no banco de dados. Isso afeta a forma como a consulta deve ser executada e como o contexto de persistência deve ser gerenciado durante a execução da consulta. Essa anotação é geralmente usada em conjunto com a anotação @Query._

**Parâmetros:**

- `flushAutomatically`: _Este atributo especifica se o contexto de persistência deve ser automaticamente descarregado (flushed) antes de executar a consulta modificadora._
- `clearAutomatically`: _Este atributo especifica se o contexto de persistência deve ser automaticamente limpo (cleared) após a execução da consulta modificadora._

${\color{yellow}@Procedure}$ : _@Procedure é usada para declarar mapeamentos de procedimentos armazenados JPA 2.1 diretamente em métodos de repositório. Isso permite chamar procedimentos armazenados do banco de dados por meio de métodos de repositório JPA, simplificando a interação com procedimentos armazenados._

**Parâmetros:**

- `procedureName`: _Este atributo também especifica o nome do procedimento no banco de dados. O valor padrão é uma string vazia ("")._
- `name`: _Especifica o nome do procedimento no EntityManager. O valor padrão é uma string vazia ("")._
- `outputParameterName`: _Este atributo especifica o nome do parâmetro de saída do procedimento armazenado. O valor padrão é uma string vazia ("")._
- `refCursor`: _Especifica se o procedimento retorna um Ref Cursor do banco de dados. Um Ref Cursor é uma estrutura de dados que pode ser usada para percorrer conjuntos de resultados. O valor padrão é false._

${\color{yellow}@Query}$ : _@Query é usada para declarar consultas personalizadas diretamente em métodos de repositório. Isso permite definir as consultas JPA que serão executadas quando um método anotado com @Query for chamado._

**Parâmetros:**

- `value`: _Esse atributo define a consulta JPA a ser executada quando o método anotado é chamado. O valor padrão é uma string vazia ("")._
- `countQuery`: _Esse atributo permite definir uma consulta especial de contagem que será usada para consultas de paginação a fim de obter o número total de elementos em uma página._
- `countProjection`: _Este atributo define a parte de projeção da consulta de contagem gerada para consultas de paginação. Se nenhum countQuery() nem countProjection() estiver configurado, a consulta de contagem será derivada da consulta original._
- `nativeQuery`: _Esse atributo configura se a consulta é uma consulta nativa (SQL) em vez de uma consulta JPQL. O valor padrão é false._
- `name`: _Especifica o nome da consulta nomeada a ser usada. Se não for definido, uma @NamedQuery com o nome {$domainClass}.${queryMethodName} será usada._
- `countName`: _Especifica o nome da consulta nomeada a ser usada para executar consultas de contagem ao usar a paginação. O padrão é derivar o nome da consulta da consulta nomeada configurada, seguido de `.count`._
- `queryRewriter`: _Esse atributo permite definir um QueryRewriter que deve ser aplicado à string da consulta após a montagem completa da consulta. Isso é útil para modificar ou ajustar a consulta antes de ser executada._

${\color{yellow}@QueryHints}$ : _@QueryHints são dicas para otimizar a execução de consultas no JPA. A anotação @QueryHints permite que essas dicas sejam aplicadas a consultas definidas em métodos de repositório ou derivadas a partir do nome do método._

**Parâmetros:**

- `value`: _Esse atributo permite especificar um ou mais objetos @QueryHint. Os objetos @QueryHint são usados para configurar dicas específicas para a consulta, como hints de cache, dicas de busca, etc._
- `forCounting`: _Esse atributo define se as dicas de consulta configuradas também devem ser aplicadas a consultas de contagem durante a paginação. O valor padrão é true, o que significa que as dicas se aplicam a consultas de contagem._

${\color{yellow}@Temporal}$ : _@Temporal é usada para declarar o tipo de data a ser usado em parâmetros de métodos de consulta. Ela é usada em conjunto com parâmetros de tipo Date para indicar o tipo de data que será usado em uma consulta._

**Parâmetros:**

- `value`: _Este atributo permite definir o tipo de data a ser usado para o parâmetro anotado. O valor padrão é **TemporalType.DATE**, mas você pode especificar outros valores, como **TemporalType.TIME** ou **TemporalType.TIMESTAMP**._