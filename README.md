# Anotações do Framework Spring

_Este documento descreve várias anotações disponíveis no Spring Framework, organizadas por módulos em ordem alfabética._

## Índice

- [Spring Beans 6.0.12](#spring-beans)
- [Spring Boot 3.1.4](#spring-boot)
- [Spring Cloud AWS 3.0.2](#spring-cloud-aws)
- [Spring Cloud Openfeign 4.0.4](#spring-cloud-openfeign)
- [Spring Context 6.0.12](#spring-context)
- [Spring Core 6.0.12](#spring-core)
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

${\color{yellow}@ Async}$ : _@Async é usada para marcar um método como candidato à execução assíncrona._

**Parâmetros:**

- `value`: _Usado para especificar um valor de qualificador para operações assíncronas específicas._

${\color{yellow}@Bean}$ : _@Bean é usada para indicar que um método produz um bean a ser gerenciado pelo contêiner Spring._

**Parâmetros:**

- `value \ name`: _Você pode especificar um nome ou vários nomes para o bean._
- `autowireCandidate`: _Permite determinar se o bean é um candidato para ser injetado em outros beans por padrão. O valor padrão é true._
- `initMethod`: _Permite especificar o nome de um método que será chamado no bean durante a inicialização._
- `destroyMethod`: _Permite especificar o nome de um método que será chamado no bean quando o contexto do aplicativo for fechado._

${\color{yellow}@Cacheable}$ : _@Cacheable é usada para definir o comportamento de armazenamento em cache para os métodos anotados e permite que você ajuste o comportamento de armazenamento em cache com base em várias condições e configurações personalizadas._

**Parâmetros:**

- `value \ cacheNames`: _Permite especificar o nome ou os nomes das caches onde os resultados das invocações do método serão armazenados._
- `key`: _Permite especificar uma expressão Spring Expression Language (SpEL) para calcular a chave dinamicamente para cada invocação do método._
- `keyGenerator`: _Permite especificar o nome de um KeyGenerator personalizado que será usado para gerar as chaves. É mutuamente exclusivo com o atributo key._
- `cacheManager`: _Permite especificar o nome de um CacheManager personalizado que será usado para criar um **CacheResolver** padrão se nenhum estiver configurado._
- `cacheResolver`: _Permite especificar o nome de um **CacheResolver** personalizado que será usado para determinar o cache para a invocação do método._
- `condition`: _Permite especificar uma expressão SpEL que determina se a invocação do método deve ser armazenada em cache ou não._
- `unless`: _Permite especificar uma expressão SpEL que veta o armazenamento em cache se a condição avaliada for true._
- `sync`: _Permite sincronizar a invocação do método se várias threads estiverem tentando carregar um valor para a mesma chave. A sincronização pode ser usada para evitar que várias threads executem a mesma invocação simultaneamente._

${\color{yellow}@CacheConfig}$ : _@CacheConfig é usada para definir configurações padrão de cache em nível de classe._

**Parâmetros:**

- `cacheNames`: _Permite especificar o nome ou os nomes das caches onde os resultados das invocações do método serão armazenados._
- `keyGenerator`: _Permite especificar o nome de um KeyGenerator personalizado que será usado para gerar as chaves. É mutuamente exclusivo com o atributo key._
- `cacheManager`: _Permite especificar o nome de um CacheManager personalizado que será usado para criar um **CacheResolver** padrão se nenhum estiver configurado._
- `cacheResolver`: _Permite especificar o nome de um **CacheResolver** personalizado que será usado para determinar o cache para a invocação do método._

${\color{yellow}@CacheEvict}$ : _@CacheEvict é usada para indicar que um método ou todos os métodos em uma classe acionam operações de esvaziamento da cache._

**Parâmetros:**

- `cacheNames`: _Permite especificar o nome ou os nomes das caches onde os resultados das invocações do método serão armazenados._
- `key`: _Permite especificar uma expressão Spring Expression Language (SpEL) para calcular a chave dinamicamente para cada invocação do método._
- `keyGenerator`: _Permite especificar o nome de um KeyGenerator personalizado que será usado para gerar as chaves. É mutuamente exclusivo com o atributo key._
- `cacheManager`: _Permite especificar o nome de um CacheManager personalizado que será usado para criar um **CacheResolver** padrão se nenhum estiver configurado._
- `cacheResolver`: _Permite especificar o nome de um **CacheResolver** personalizado que será usado para determinar o cache para a invocação do método._
- `condition`: _Permite especificar uma expressão SpEL que determina se a invocação do método deve ser armazenada em cache ou não._
- `unless`: _Especifica se todas as entradas dentro do cache devem ser removidas._
- `beforeInvocation`: _Especifica se a operação de esvaziamento da cache deve ocorrer antes da invocação do método._

${\color{yellow}@CachePut}$ : _@CachePut é usada para indicar que um método ou todos os métodos em uma classe acionam operações de armazenamento em cache, que armazenam os resultados do método nas caches especificadas._

**Parâmetros:**

- `cacheNames`: _Permite especificar o nome ou os nomes das caches onde os resultados das invocações do método serão armazenados._
- `keyGenerator`: _Permite especificar o nome de um KeyGenerator personalizado que será usado para gerar as chaves. É mutuamente exclusivo com o atributo key._
- `cacheManager`: _Permite especificar o nome de um CacheManager personalizado que será usado para criar um **CacheResolver** padrão se nenhum estiver configurado._
- `cacheResolver`: _Permite especificar o nome de um **CacheResolver** personalizado que será usado para determinar o cache para a invocação do método._
- `condition`: _Permite especificar uma expressão SpEL que determina se a invocação do método deve ser armazenada em cache ou não._
- `unless`: _Permite especificar uma expressão SpEL que veta o armazenamento em cache se a condição avaliada for true._

${\color{yellow}@Caching}$ : _@Caching é uma anotação de agrupamento para várias anotações de cache, sejam elas do mesmo tipo (por exemplo, várias anotações @Cacheable) ou de tipos diferentes (por exemplo, @Cacheable, @CachePut e @CacheEvict). Essa anotação permite que você defina várias operações de cache em um único local._

**Parâmetros:**

- `cacheable`: _Permite que você especifique uma ou mais anotações @Cacheable que descrevem as operações de cache de leitura (ou seja, quando um valor é buscado em uma cache)._
- `put`: _Permite que você especifique uma ou mais anotações @CachePut que descrevem as operações de cache de gravação (ou seja, quando um valor é armazenado em uma cache)._
- `evict`: _Permite que você especifique uma ou mais anotações @CacheEvict que descrevem as operações de evicção de cache (ou seja, quando um valor é removido de uma cache)._

${\color{yellow}@Component}$ : _@Component é uma anotação do Spring Framework que indica que uma classe anotada é um "componente". Os componentes são considerados candidatos para detecção automática quando se utiliza configuração baseada em anotações e digitalização do classpath._

**Parâmetros:**

- `value`: _Permite fornecer uma sugestão para um nome lógico do componente._

${\color{yellow}@ComponentScan}$ : _@ComponentScan é usada para configurar diretivas de varredura de componentes para classes anotadas com @Configuration._

**Parâmetros:**

- `basePackages`: _Path de pacotes do projeto para verificar propriedades de configuração._
- `basePackageClasses`: _Alternativa ("Type-safe") especificando os pacotes para verificar as propriedades de configuração. O pacote de cada classe especificada será verificado._
- `nameGenerator`: _A classe **BeanNameGenerator** a ser usada para nomear os componentes detectados no contêiner Spring._
- `scopeResolver`: _A classe **ScopeMetadataResolver** a ser usada para resolver o escopo dos componentes detectados._
- `scopedProxy`: _Controla a geração de proxies para os componentes detectados, o que pode ser necessário quando se usam escopos no estilo de proxy._
- `resourcePattern`: _Controla quais arquivos de classe são elegíveis para a detecção de componentes._
- `useDefaultFilters`: _Indica se a detecção automática de classes anotadas com @Component, @Repository, @Service ou @Controller deve ser ativada._
- `includeFilters \ excludeFilters`: _Filtros que podem ser usados para incluir ou excluir beans do contexto de aplicação. Isso é útil para personalizar o ambiente de teste._
- `lazyInit`: _Especifica se os beans escaneados devem ser registrados para inicialização tardia. O padrão é false._

${\color{yellow}@ComponentScans}$ : _@ComponentScans é uma anotação de contêiner que agrega várias anotações @ComponentScan. Ela pode ser usada para declarar várias anotações @ComponentScan agrupadas, permitindo que você configure várias diretivas de varredura de componentes em uma única classe de configuração._

**Parâmetros:**

- `value`: _Usado para especificar uma ou mais anotações @ComponentScan que contêm as configurações de varredura de componentes._

${\color{yellow}@Conditional}$ : _@Conditional é usada no Spring Framework para controlar a condição sob a qual um componente é registrado no contêiner de aplicativos. Isso permite que você registre componentes somente quando determinadas condições são atendidas._

**Parâmetros:**

- `value`: _Permite que todas as classes de condição que devem corresponder para que o componente seja registrado.

${\color{yellow}@Configuration}$ : _@Configuration é usada no Spring Framework para marcar uma classe como uma classe de configuração._

**Parâmetros:**

- `value`: _Atributo permite que você especifique explicitamente o nome da definição de bean do Spring associada à classe @Configuration._
- `proxyBeanMethods`: _(desde a versão 5.2) Este atributo controla se os métodos @Bean dentro da classe @Configuration devem ser proxy, a fim de garantir o comportamento do ciclo de vida do bean._
- `enforceUniqueMethods`: _(desde a versão 6.0) Controla se os métodos @Bean devem ter nomes de métodos exclusivos._

${\color{yellow}@Controller}$ : _@Controller indica que a classe é um controlador, o que significa que ela lida com solicitações da web, processa as solicitações e fornece respostas apropriadas._

**Parâmetros:**

- `value`: _Sugere um nome lógico para o componente que será registrado no contêiner Spring._

${\color{yellow}@DependsOn}$ : _@DependsOn é usada para controlar explicitamente a ordem de inicialização e, para beans singleton, a ordem de destruição dos beans no contexto do Spring._

${\color{yellow}@Description}$ : _@Description é usada no contexto do Spring Framework para adicionar uma descrição textual a definições de beans derivados de classes anotadas com @Component ou de métodos anotados com @Bean._

**Parâmetros:**

- `value`: _Descrição textual que você deseja associar ao bean._

${\color{yellow}@DateTimeFormat}$ : _@DateTimeFormat é usada no Spring Framework para declarar como um campo, parâmetro de método ou atributo de anotação deve ser formatado como data ou hora._

**Parâmetros:**

- `style`: _Define o estilo de formatação da data ou hora. O valor padrão é "SS" para um estilo de data curto e hora curta._
- `iso`: _Define o formato ISO da data ou hora. Os formatos ISO suportados são definidos na enumeração ISO. O valor padrão é ISO.NONE, indicando que esse atributo deve ser ignorado._
- `pattern`: _Permite especificar um padrão de formato personalizado para a data ou hora. O padrão segue o estilo do **SimpleDateFormat**._
- `fallbackPatterns`: _Define um conjunto de padrões personalizados de fallback em caso de falha na conversão usando o padrão principal, ISO ou estilo. Isso é útil quando você deseja permitir formatações flexíveis para entrada de usuário._

${\color{yellow}@EnableAsync}$ : _@EnableAsync é usada no Spring Framework para habilitar a capacidade de execução assíncrona de métodos._

**Parâmetros:**

- `annotation`: _Permite indicar o tipo de anotação de "async" que deve ser detectada em nível de classe ou método. Por padrão, o Spring detectará tanto a anotação @Async do Spring._
- `proxyTargetClass`: _Controla se proxies baseados em classes (CGLIB) devem ser criados em oposição a proxies baseados em interfaces padrão do Java._
- `mode`: _Indica como o conselho assíncrono deve ser aplicado. O padrão é AdviceMode.PROXY, que permite a interceptação de chamadas por meio do proxy._
- `order`: _Controla a ordem em que o AsyncAnnotationBeanPostProcessor deve ser aplicado. O padrão é **Ordered.LOWEST_PRECEDENCE**._

${\color{yellow}@EnableAspectJAutoProxy}$ : _@EnableAspectJAutoProxy é usada para habilitar o suporte ao tratamento de componentes marcados com a anotação @Aspect do AspectJ._

**Parâmetros:**

- `proxyTargetClass`: _Controla se proxies baseados em classes (CGLIB) devem ser criados em oposição a proxies baseados em interfaces padrão do Java._
- `exposeProxy`: _Indica se o proxy deve ser exposto pelo framework AOP como um ThreadLocal para recuperação por meio da classe AopContext do Spring._

${\color{yellow}@EnableCaching}$ : _@EnableCaching é usada para habilitar o suporte ao gerenciamento de cache baseado em anotações no Spring._

**Parâmetros:**

- `proxyTargetClass`: _Controla se proxies baseados em classes (CGLIB) devem ser criados em oposição a proxies baseados em interfaces padrão do Java._
- `mode`: _Indica como o conselho assíncrono deve ser aplicado. O padrão é AdviceMode.PROXY, que permite a interceptação de chamadas por meio do proxy._
- `order`: _Indica como o aconselhamento de cache deve ser aplicado. O padrão é AdviceMode.PROXY._

${\color{yellow}@EnableLoadTimeWeaving}$ : _@EnableLoadTimeWeaving é usada para ativar um carregador de tempo de execução (Load Time Weaver) para um contexto de aplicação Spring. Isso é útil quando se deseja realizar tecelagem (weaving) de aspectos, especialmente no contexto do AspectJ, durante o tempo de carregamento de classes._

**Parâmetros:**

- `aspectjWeaving`: _Controla se a tecelagem AspectJ deve ser ativada. Os valores possíveis para aspectjWeaving são: **AspectJWeaving.ENABLED**, **AspectJWeaving.DISABLED**, **AspectJWeaving.AUTODETECT**_

${\color{yellow}@EnableMBeanExport}$ : _@EnableMBeanExport é usada para habilitar a exportação de MBeans (Managed Beans) em um contexto Spring, facilitando a exposição de beans gerenciados como MBeans em um servidor JMX (Java Management Extensions). Isso permite monitorar e gerenciar esses beans usando ferramentas de gerenciamento JMX._

**Parâmetros:**

- `defaultDomain`: _Define o domínio padrão a ser usado ao gerar ObjectNames JMX. Um ObjectName JMX é uma identificação exclusiva usada para identificar um MBean. Se não for fornecido, o domínio padrão é usado._
- `server`: _Permite especificar o nome do bean MBeanServer ao qual os MBeans devem ser exportados. Por padrão, o servidor MBean padrão da plataforma é usado._
- `registration`: _Especifica a política a ser usada ao tentar registrar um MBean sob um ObjectName que já existe. Os valores possíveis para esse atributo são: **RegistrationPolicy.FAIL_ON_EXISTING**, **RegistrationPolicy.IGNORE_EXISTING** e **RegistrationPolicy.REPLACE_EXISTING**_

${\color{yellow}@EnableScheduling}$ : _@EnableScheduling é usada em classes de configuração do Spring para habilitar a capacidade de execução de tarefas agendadas. Essas tarefas agendadas são definidas por meio de anotações @Scheduled._

${\color{yellow}@EventListener}$ : _@EventListener é usada no Spring Framework para marcar um método como um ouvinte de eventos da aplicação. Esse método será invocado quando o evento especificado ocorrer._

**Parâmetros:**

- `value / classes`: _Especificar os tipos de eventos que o ouvinte deve manipular._
- `condition`: _Este atributo permite que você especifique uma expressão Spring Expression Language (SpEL) que controla condicionalmente se o método do ouvinte é chamado._
- `id`: _A partir do Spring 5.3.5, você pode usar o atributo id para especificar um identificador exclusivo para o ouvinte. Isso é útil quando você precisa identificar ou remover o ouvinte posteriormente._

${\color{yellow}@Import}$ : _@Import é usada para importar um ou mais componentes no contexto de aplicação._

**Parâmetros:**

- `value`: _@Configuration, ImportSelector, ImportBeanDefinitionRegistrar ou classes de componentes regulares para importar._

${\color{yellow}@ImportResource}$ : _@ImportResource é usada no Spring Framework para importar definições de beans de recursos externos, como arquivos XML de configuração, para o contexto de aplicação. É semelhante à anotação @Import, mas é usada para importar recursos externos, enquanto @Import é usada para importar classes de configuração e outros componentes._

**Parâmetros:**

- `locations`: _Pode usar os prefixos de carregamento de recursos, como classpath:, file:, etc._
- `reader`: _Você pode substituir o leitor padrão **BeanDefinitionReader**._

${\color{yellow}@ImportRuntimeHints}$ : _@ImportRuntimeHints é usada no contexto do Spring Framework para indicar que uma ou mais implementações da interface RuntimeHintsRegistrar devem ser processadas._

**Parâmetros:**

- `value`: _Onde você lista as classes que contêm dicas de tempo de execução para serem usadas na otimização do seu aplicativo._

${\color{yellow}@Indexed}$ : _@Indexed é usada para indicar que o elemento anotado representa um estereótipo (stereotype) que deve ser indexado no contexto do Spring._

${\color{yellow}@Lazy}$ : _@Lazy é usada para indicar se um bean deve ser inicializado de forma preguiçosa (lazy initialization) ou de forma imediata (eager initialization) em um contexto do Spring._

**Parâmetros:**

- `value`: _Indica se a inicialização lenta deve ocorrer._

${\color{yellow}@ManagedAttribute}$ : _@ManagedAttribute é usada para indicar que um determinado método de um bean deve ser exposto como um atributo JMX._

**Parâmetros:**

- `defaultValue`: _Permite definir um valor padrão para o atributo no descritor JMX._
- `description`: _Usado para definir uma descrição para o atributo no descritor JMX._
- `currencyTimeLimit`: _Controla a duração de tempo em que o valor do atributo permanece válido._
- `persistPolicy`: _Usado para indicar como o valor do atributo deve ser persistido._
- `persistPeriod`: _Controla a frequência com que o valor do atributo é persistido._

${\color{yellow}@ManagedMetric}$ : _@ManagedMetric é usada para indicar que um método de um bean deve ser exposto como um atributo JMX, com informações adicionais para indicar que se trata de uma métrica._

**Parâmetros:**

- `category`: _Especifica a categoria à qual a métrica pertence. Pode ser usado para organizar as métricas em grupos relacionados._
- `currencyTimeLimit`: _Controla a duração de tempo em que o valor do atributo permanece válido._
- `description`: _Permite fornecer uma descrição da métrica, explicando o que ela representa._
- `displayName`: _Especifica um nome amigável para a métrica que pode ser exibido em ferramentas de gerenciamento e monitoramento._
- `metricType`: _Define o tipo da métrica, que pode ser um dos seguintes: **MetricType.GAUGE** e **MetricType.COUNTER**._
- `persistPeriod`: _Controla a frequência com que o valor do atributo é persistido._
- `persistPolicy`: _Usado para indicar como o valor do atributo deve ser persistido._
- `unit`: _Define a unidade da métrica, indicando qual é a unidade de medida dos valores da métrica, como "bytes," "milissegundos," "solicitações," etc._

${\color{yellow}@ManagedNotification}$ : _@ManagedNotification é usada para indicar que um bean em um aplicativo JMX emite notificações JMX. Notificações JMX são mensagens que um bean envia para notificar eventos ou mudanças de estado._

**Parâmetros:**

- `name`: _Especifica o nome da notificação JMX. O nome deve ser exclusivo dentro do contexto JMX. É usado para identificar a notificação e, portanto, deve ser exclusivo para evitar conflitos._
- `description`: _Permite fornecer uma descrição da métrica, explicando o que ela representa._
- `notificationTypes`: _Especifica os tipos de notificação que podem ser gerados por esta notificação. Os tipos de notificação são strings que descrevem o tipo da notificação, como "error," "warning," "info," etc. Uma notificação pode ter vários tipos._

${\color{yellow}@ManagedNotifications}$ : _@ManagedNotifications é um container de nível de tipo usada para agrupar uma ou mais declarações da anotação @ManagedNotification._

**Parâmetros:**

- `value`: _Agrupamento de anotações @ManagedNotification._

${\color{yellow}@ManagedOperation}$ : _@ManagedOperation é usada para indicar que um método deve ser exposto como uma operação JMX._

**Parâmetros:**

- `description`: _Permite fornecer uma descrição da métrica, explicando o que ela representa._
- `currencyTimeLimit`: _Controla a duração de tempo em que o valor do atributo permanece válido._

${\color{yellow}@ManagedOperationParameter}$ : _@ManagedOperationParameter é usada para fornecer metadados sobre os parâmetros de uma operação JMX._

**Parâmetros:**

- `name`: _Permite especificar o nome do parâmetro da operação._
- `description`: _Permite fornecer uma descrição da métrica, explicando o que ela representa._

${\color{yellow}@ManagedOperationParameters}$ : _@ManagedOperationParameters é um container de nível de tipo usada para agrupar uma ou mais declarações da anotação @ManagedOperationParameter._

**Parâmetros:**

- `value`: _Agrupamento de anotações @ManagedOperationParameter._

${\color{yellow}@ManagedResource}$ : _@ManagedResource é usada para registrar instâncias de uma classe com um servidor JMX._

**Parâmetros:**

- `value / objectName`: _permite especificar o nome do objeto JMX sob o qual a instância da classe será registrada no servidor JMX._
- `description`: _Permite fornecer uma descrição da métrica, explicando o que ela representa._
- `currencyTimeLimit`: _Controla a duração de tempo em que o valor do atributo permanece válido._
- `log`: _permite especificar o nome do objeto JMX sob o qual a instância da classe será registrada no servidor JMX._
- `logFile`: _permite especificar o nome do objeto JMX sob o qual a instância da classe será registrada no servidor JMX._
- `persistPolicy`: _Usado para indicar como o valor do atributo deve ser persistido._
- `persistPeriod`: _Controla a frequência com que o valor do atributo é persistido._
- `persistName`: _Especifica um nome para os dados persistidos._
- `persistLocation`: _Especifica o local onde os dados persistidos serão armazenados._

${\color{yellow}@NumberFormat}$ : _@NumberFormat é usada para declarar que um campo, método ou parâmetro de método deve ser formatado como um número._

**Parâmetros:**

- `style`: _Especifica o estilo de formatação a ser usado para o campo._
- `pattern`: _Permite que você especifique um padrão de formatação personalizado._

${\color{yellow}@Primary}$ : _@Primary é usada para indicar que um bean deve ser preferido quando existem vários candidatos qualificados para atender a uma dependência com um único valor._

**Parâmetros:**

- `style`: _Especifica o estilo de formatação a ser usado para o campo._
- `pattern`: _Permite que você especifique um padrão de formatação personalizado._

${\color{yellow}@Profile}$ : _@Profile é usada para indicar que um componente deve ser registrado e processado somente quando um ou mais perfis específicos estão ativos no aplicativo Spring._

**Parâmetros:**

- `value`: _Aceita um array de strings representando os nomes dos perfis._

${\color{yellow}@PropertySource}$ : _@PropertySource é usada para carregar propriedades a partir de arquivos de configuração, que podem ser arquivos .properties ou arquivos XML._

**Parâmetros:**

- `name`: _Indica o nome exclusivo desta fonte de propriedades. Se omitido, o nome será gerado com base na origem subjacente._
- `value`: _Indica as localizações dos arquivos de propriedades a serem carregados. O padrão é suportado para diferentes formatos de arquivo, como *.properties ou *.xml._
- `ignoreResourceNotFound`: _Indica se uma falha ao encontrar um recurso de propriedades deve ser ignorada. Definir isso como true é apropriado se o arquivo de propriedades for completamente opcional. O padrão é false._
- `encoding`: _Especifica uma codificação de caracteres específica para os recursos fornecidos. Por exemplo, você pode definir UTF-8 como a codificação._
- `factory`: _Especifica uma fábrica personalizada de PropertySource a ser usada._

${\color{yellow}@PropertySources}$ : _@PropertySources é uma anotação container que permite agregar várias anotações @PropertySource._

**Parâmetros:**

- `value`: _Agrupamento de anotações @PropertySource._

${\color{yellow}@Repository}$ : _@Repository é usada para marcar classes que desempenham o papel de repositórios de dados, geralmente para acesso a banco de dados._

**Parâmetros:**

- `value`: _Pode indicar uma sugestão de nome de componente lógico._

${\color{yellow}@Role}$ : _@Role é usada para indicar o "papel" (role) de um bean._

**Parâmetros:**

- `value`: _Permite especificar um valor inteiro que representa o papel do bean no contexto da aplicação._

${\color{yellow}@Scope}$ : _@Scope é usada para definir o escopo de uma instância gerenciada pelo Spring, o que afeta a vida útil da instância e como ela é compartilhada ou criada._

**Parâmetros:**

- `scopeName`: _Permite especificar o nome do escopo a ser usado para as instâncias do tipo anotado. O escopo se refere à vida útil da instância do bean._
- `proxyMode`: _Permite especificar se o componente deve ser configurado como um proxy de escopo._

${\color{yellow}@Scheduled}$ : _@Scheduled é usada no Spring Framework para agendar a execução de um método de maneira programada._

**Parâmetros:**

- `cron`: _Especifica uma expressão cron que define quando a tarefa será executada._
- `fixedDelay`: _Define um atraso fixo entre o término de uma invocação do método agendado e o início da próxima invocação. O atraso é especificado em milissegundos._
- `fixedRate`: _Define um intervalo fixo entre invocações consecutivas do método agendado, independentemente de quando o método anterior terminou. O intervalo é especificado em milissegundos._
- `initialDelay`: _Define um atraso inicial antes da primeira invocação do método agendado. O atraso é especificado em milissegundos._
- `zone`: _Especifica a zona de tempo na qual a expressão cron deve ser avaliada. Por padrão, ele usa a zona de tempo do servidor._
- `fixedDelayString / fixedRateString / initialDelayString`: _Versões alternativas dos atributos acima que permitem usar valores de string, incluindo suporte a expressões SpEL._
- `timeUnit`: _Permite especificar a unidade de tempo para os atributos fixedDelay, fixedRate, initialDelay, fixedDelayString, fixedRateString e initialDelayString._

${\color{yellow}@Schedules}$ : _@Schedules é uma anotação de contêiner que permite agrupar várias anotações @Scheduled em um único local._

**Parâmetros:**

- `value`: _Agrupamento de anotações @Scheduled._

${\color{yellow}@Service}$ : _@Service é usada para indicar que uma classe é um "Serviço" no contexto de um aplicativo Spring._

**Parâmetros:**

- `value`: _Permite especificar um nome para o componente._

${\color{yellow}@ Validated}$ : _@Validated é usada para indicar que uma classe, método ou argumento de método deve ser validado._

**Parâmetros:**

- `value`: _Permite especificar grupos de validação personalizados que serão aplicados durante a validação._

## Spring-core


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