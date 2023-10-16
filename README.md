# Anotações do Framework Spring

_Este documento descreve várias anotações disponíveis no Spring Framework, organizadas por módulos em ordem alfabética._

## Índice

- [Spring Boot 3.1.4](#spring-boot)
- [Spring Data JPA](#spring-data-jpa)
- [Spring Security](#spring-security)
- ...

## Spring-boot

${\color{yellow}@ConfigurationProperties}$ : _Mapeia propriedades de configuração definidas em arquivos de propriedades ou YAML para objetos Java._

**Parâmetros:**

- `prefix`: O prefixo das propriedades a serem vinculadas.
- `ignoreInvalidFields`: Sinalizador para indicar que, ao vincular a este objeto, campos inválidos devem ser ignorados.
- `ignoreUnknownFields`: Sinalizador para indicar que, ao vincular a este objeto, campos desconhecidos devem ser ignorados.

${\color{yellow}@ConfigurationPropertiesBinding}$ : _É uma anotação do Spring Boot usada para criar conversores personalizados para propriedades de configuração._

${\color{yellow}@ConfigurationPropertiesScan}$ : _É uma anotação do Spring Boot usada para escanear pacotes em busca de classes de propriedades de configuração._

**Parâmetros:**

- `basePackages`: _Path de pacotes do projeto para verificar propriedades de configuração._
- `basePackageClasses`: _Alternativa ("Type-safe") especificando os pacotes para verificar as propriedades de configuração. O pacote de cada classe especificada será verificado._

${\color{yellow}@ConstructorBinding}$ : _É uma anotação do Spring Boot que indica a vinculação de propriedades de configuração a construtores, facilitando a criação de objetos imutáveis._

${\color{yellow}@DefaultValue}$ : _É uma anotação do Spring Boot que pode ser usada para especificar o valor padrão ao vincular a uma propriedade imutável. Essa anotação também pode ser usada com propriedades aninhadas para indicar que um valor deve sempre ser vinculado (em vez de vincular nulo). O valor desta anotação só será utilizado se a propriedade não for encontrada nas fontes de propriedades utilizadas pelo **Binder**._

**Parâmetros:**

- `value`: _O valor padrão da propriedade. Pode ser uma matriz de valores para propriedades de coleção ou baseadas em matriz._

${\color{yellow}@DataSizeUnit}$ : _É uma anotação do Spring Boot que pode ser usada para alterar a unidade padrão usada ao converter um DataSize._

**Parâmetros:**

- `value`: _O **DataUnit** a ser usado se nenhum for especificado._

${\color{yellow}@DeprecatedConfigurationProperty}$ : _É uma anotação do Spring Boot usada para marcar propriedades de configuração como obsoletas e fornecer uma mensagem de aviso quando são usadas._

**Parâmetros:**

- `reason`: _O motivo da descontinuação._
- `replacement`: _O valor que deve ser usado (se houver)._

${\color{yellow}@DependsOnDatabaseInitialization}$ : _É uma anotação do Spring Boot que define que um bean depende da inicialização do banco de dados, garantindo que a inicialização do banco de dados seja concluída antes do bean ser criado._

${\color{yellow}@Delimiter}$ : _É uma anotação do Spring Boot que permite definir um delimitador personalizado para valores de propriedades de configuração, especialmente útil ao lidar com listas em propriedades._

**Parâmetros:**

- `value`: _O delimitador a ser usado ou **NONE** se todo o conteúdo precisar ser tratado como um único elemento._

${\color{yellow}@DurationFormat}$ : _É uma anotação do Spring Boot que permite personalizar o formato de durações, como as usadas em propriedades de configuração, para facilitar a leitura e escrita._

**Parâmetros:**

- `value`: _O estilo do formato de duração._

${\color{yellow}@EnableConfigurationProperties}$ : _É uma anotação do Spring Boot usada para habilitar a vinculação automática de propriedades de configuração a classes de configuração._

**Parâmetros:**

- `value`: _Maneira conveniente de registrar rapidamente beans anotados **@ConfigurationProperties** com Spring._

${\color{yellow}@JsonComponent}$ : _É uma anotação do Spring Boot usada para registrar um componente como um manipulador de serialização e desserialização JSON, permitindo personalizar a forma como objetos são convertidos para JSON e vice-versa._

**Parâmetros:**

- `value`: _Indica um nome lógico sugerido para o componente e pode ser convertido em um **bean**. Padrão é uma string vazia._
- `type`: _Define os tipos que o componente manipula para serialização/desserialização. Essa configuração é especialmente importante para deserializadores de chaves (**KeyDeserializer**) e pode ser usada para limitar o tratamento a subclasses de tipos inferidos._
- `scope`: _Especifica o escopo sob o qual o serializador/desserializador deve ser registrado com o módulo. O valor padrão é **Scope.VALUES**, que se aplica a serializadores/desserializadores de conteúdo de valor. O escopo **Scope.KEYS** pode ser usado para serializadores/desserializadores de chaves._

${\color{yellow}@JsonMixin}$ : _É uma anotação que permite criar uma classe que define anotações personalizadas para controlar a forma como objetos são convertidos em JSON ou de JSON para objetos, aplicando essas anotações a classes específicas. Isso facilita a personalização da serialização e desserialização JSON._

**Parâmetros:**

- `value`: _Permite especificar as classes que serão usadas como classes de mistura (mixin classes) para controlar a serialização e desserialização de objetos JSON._

${\color{yellow}@Name}$ : _É uma anotação do Spring Boot que pode ser usada para especificar o nome ao vincular a uma propriedade imutável._

**Parâmetros:**

- `value`: _O nome da propriedade a ser usada para associação._

${\color{yellow}@Nested}$ : _É uma meta-anotação do Spring Boot que deve ser adicionada às anotações que indicam que um campo é do tipo aninhado. Usado para garantir que as dicas de reflexão corretas sejam registradas._

${\color{yellow}@NestedConfigurationProperty}$ : _É uma anotação do Spring Boot usada para indicar que uma propriedade de configuração complexa está aninhada dentro de outra propriedade de configuração._

${\color{yellow}@PeriodFormat}$ : _É uma anotação do Spring Boot que permite personalizar o formato de períodos, como os usados em propriedades de configuração, para facilitar a leitura e escrita._

**Parâmetros:**

- `value`: _O estilo de formato do período._

${\color{yellow}@PeriodUnit}$ : _É uma anotação do Spring Boot que permite definir a unidade padrão para valores de período em propriedades de configuração, simplificando a configuração._

**Parâmetros:**

- `value`: _A unidade de período a ser usada se nenhuma for especificada._

${\color{yellow}@ServletComponentScan}$ : _É uma anotação do Spring Boot usada para escanear pacotes em busca de classes Servlet, Filter e Listener para configuração automática no contexto do aplicativo web._

**Parâmetros:**

- `basePackages`: _Path de pacotes do projeto para verificar propriedades de configuração._
- `basePackageClasses`: _Alternativa ("Type-safe") especificando os pacotes para verificar as propriedades de configuração. O pacote de cada classe especificada será verificado._

${\color{yellow}@SpringBootApplication}$ : _essa anotação diz ao Spring Boot que essa classe deverá ser usada como base para configurar toda nossa aplicação._

**Parâmetros:**

- `exclude`: Uma matriz de classes de configuração para serem excluídas da configuração automática.
- `excludeName`: Uma matriz de nomes de classes de configuração para serem excluídas da configuração automática.
- `scanBasePackages`: Um ou mais pacotes para serem escaneados em busca de componentes anotados.
- `scanBasePackageClasses`: Uma ou mais classes que servem como base para a varredura de pacotes em busca de componentes anotados.
- `nameGenerator`: Uma classe para gerar nomes de beans automaticamente.
- `proxyBeanMethods`: Uma configuração que controla se os métodos de bean devem ser proxy por CGLIB.

${\color{yellow}@SpringBootConfiguration}$ : _É uma anotação do Spring Boot usada para marcar classes de configuração específicas do aplicativo. Ela estende a anotação @Configuration do Spring Framework._

**Parâmetros:**

- `proxyBeanMethods`: _Sinalizador que controla se os métodos de bean devem ser proxy por CGLIB. Por padrão, ele é definido como true. Se definido como false, os métodos de bean não serão proxy._

${\color{yellow}@UtoConfiguration}$ : _É uma anotação do Spring Boot que permite configurar explicitamente o nome do bean associado a uma classe de autoconfiguração e especificar classes que devem ser aplicadas antes ou depois dela. Isso ajuda a controlar a ordem de configuração automática no contexto do aplicativo._

**Parâmetros:**

- `value`: _Define explicitamente o nome do bean associado à classe **@AutoConfiguration**. Se não for especificado, um nome de bean será gerado automaticamente._
- `before`: _Especifica as classes de autoconfiguração que ainda não devem ser aplicadas antes da classe **@AutoConfiguration**._
- `beforeName`: _Define os nomes das classes de autoconfiguração que ainda não devem ser aplicadas antes da classe **@AutoConfiguration**._
- `after`: _Especifica as classes de autoconfiguração que já devem ter sido aplicadas antes da classe **@AutoConfiguration**._
- `afterName`: _Define os nomes das classes de autoconfiguração que já devem ter sido aplicadas antes da classe **@AutoConfiguration**._

${\color{yellow}@AutoConfigurationPackage}$ : _É uma anotação do Spring Boot que escaneia e registra automaticamente pacotes para configuração automática no contexto do aplicativo. Ela identifica o pacote da classe anotada e escaneia outros pacotes a partir dele._

**Parâmetros:**

- `basePackages`: _Path de pacotes do projeto para verificar propriedades de configuração._
- `basePackageClasses`: _Alternativa ("Type-safe") especificando os pacotes para verificar as propriedades de configuração. O pacote de cada classe especificada será verificado._

${\color{yellow}@AutoConfigureBefore}$ : _É uma anotação do Spring Boot que especifica classes de autoconfiguração que devem ser aplicadas antes de uma determinada classe de autoconfiguração, controlando a ordem de configuração automática._

**Parâmetros:**

- `value`: _Especifica as classes de autoconfiguração que devem ser aplicadas antes da classe anotada, controlando a ordem de configuração automática._
- `name`: _Define os nomes das classes de autoconfiguração que devem ser aplicadas antes da classe anotada, também controlando a ordem de configuração automática. Esta opção foi adicionada na versão 1.2.2 do Spring Boot._

${\color{yellow}@AutoConfigureAfter}$ : _É uma anotação do Spring Boot que especifica classes de autoconfiguração que devem ser aplicadas depois de uma determinada classe de autoconfiguração, controlando a ordem de configuração automática._

**Parâmetros:**

- `value`: _Especifica as classes de autoconfiguração que devem ser aplicadas antes da classe anotada, controlando a ordem de configuração automática._
- `name`: _Define os nomes das classes de autoconfiguração que devem ser aplicadas antes da classe anotada, também controlando a ordem de configuração automática. Esta opção foi adicionada na versão 1.2.2 do Spring Boot._

${\color{yellow}@AutoConfigureOrder}$ : _É uma anotação do Spring Boot que permite especificar a ordem de prioridade de classes de configuração automática, controlando a sequência de configuração durante a inicialização do aplicativo._

**Parâmetros:**

- `value`: _permite definir a prioridade de configuração automática, onde o padrão é 0. Esse valor determina a ordem de execução das classes de configuração automática durante a inicialização do aplicativo Spring Boot. Quanto menor o valor, maior a prioridade._

${\color{yellow}@EnableAutoConfiguration}$ : _É uma anotação do Spring Boot que ativa a configuração automática, permitindo que o Spring Boot configure automaticamente o aplicativo com base nas dependências e no ambiente._

**Parâmetros:**

- `exclude`: _Especifica classes de configuração automática a serem excluídas._
- `excludeName`: _Especifica nomes de classes de configuração automática a serem excluídos. (Adicionado na versão 1.3.0)._

${\color{yellow}@ImportAutoConfiguration}$ : _É uma anotação do Spring Boot que permite importar classes de configuração automática personalizada para o aplicativo Spring Boot, estendendo as configurações padrão._

**Parâmetros:**

- `value / classes`: _Especifica classes de configuração automática personalizada a serem importadas. Pode ser definido diretamente ou por meio de um arquivo no **META-INF/spring** que lista as classes a serem importadas._
- `exclude`: _Especifica classes de configuração automática a serem excluídas, garantindo que não sejam aplicadas._

${\color{yellow}@BatchDataSource}$ : _É uma anotação do Spring Boot usada para configurar um **DataSource** específico para o processamento de lotes em aplicações Spring Batch, permitindo o isolamento dos recursos de banco de dados para tarefas de lote._

${\color{yellow}@ConditionalOnBean}$ : _É uma anotação do Spring Boot que condiciona a ativação de um componente somente se um determinado bean estiver presente no contexto da aplicação. Isso permite controlar a inicialização de componentes com base na existência de outros beans._

**Parâmetros:**

- `value`: _Especifica as classes de beans cuja presença no contexto da aplicação será verificada para a condição._
- `type`: _Especifica os nomes de classes de beans cuja presença no contexto da aplicação será verificada._
- `annotation`: _Especifica os tipos de anotações de classe que decoram os beans a serem verificados._
- `name`: _Especifica os nomes de beans cuja presença no contexto da aplicação será verificada._
- `search`: _Define a estratégia de pesquisa para determinar se o contexto de aplicação hierárquico (contextos pai) deve ser considerado._
- `parameterizedContainer`: _Especifica classes adicionais que podem conter tipos de beans específicos em seus parâmetros genéricos._

${\color{yellow}@ConditionalOnClass}$ : _É uma anotação do Spring Boot que condiciona a ativação de um componente somente se uma ou mais classes especificadas estiverem presentes no classpath da aplicação. Isso permite controlar a inicialização de componentes com base na disponibilidade de classes._

**Parâmetros:**

- `value`: _Especifica as classes cuja presença no classpath é necessária para ativar a condição._
- `name`: _Especifica os nomes de classes cuja presença no classpath é necessária._

${\color{yellow}@ConditionalOnCloudPlatform}$ : _É uma anotação do Spring Boot que condiciona a ativação de um componente com base na plataforma em nuvem especificada, permitindo configurar componentes para diferentes ambientes de nuvem, como AWS, Google Cloud ou Azure._

**Parâmetros:**

- `value`: _Especifica a plataforma em nuvem esperada para ativar a condição._

${\color{yellow}@ConditionalOnExpression}$ : _É uma anotação do Spring Boot que condiciona a ativação de um componente com base em uma expressão SpEL (Spring Expression Language) avaliada em tempo de execução, permitindo ativar componentes com base em regras lógicas definidas na expressão._

**Parâmetros:**

- `value`: _Especifica a expressão SpEL a ser avaliada em tempo de execução. Se a expressão retornar **true**, a condição é ativada. Caso contrário, a condição é desativada. O valor padrão é "**true**"._

${\color{yellow}@ConditionalOnJava}$ : _É uma anotação do Spring Boot que condiciona a ativação de um componente com base na versão da plataforma Java, permitindo que os componentes sejam ativados apenas quando a versão Java especificada estiver presente._

**Parâmetros:**

- `range`: _Configura se o valor especificado em **value()** é considerado um limite superior exclusivo ou um limite inferior inclusivo. O padrão é **Range.EQUAL_OR_NEWER** (igual ou mais recente)._
- `value`: _Especifica a versão da plataforma Java a ser verificada._

${\color{yellow}@ConditionalOnJndi}$ : _É uma anotação do Spring Boot que condiciona a ativação de um componente com base na disponibilidade de um recurso JNDI (Java Naming and Directory Interface), permitindo que componentes sejam ativados apenas quando o recurso JNDI especificado estiver disponível._

**Parâmetros:**

- `value`: _Especifica os locais JNDI em que pelo menos um deve existir para ativar a condição. Se nenhum local for especificado, a condição será ativada apenas com base na presença de um **InitialContext**._

${\color{yellow}@ConditionalOnMissingBean}$ : _É uma anotação do Spring Boot que condiciona a ativação de um componente somente se não houver uma instância de bean do mesmo tipo já definida no contexto, permitindo substituir beans padrão com implementações personalizadas._

**Parâmetros:**

- `value`: _Especifica os tipos de classes de beans a serem verificados quanto à ausência._
- `type`: _Especifica os nomes das classes de beans a serem verificados quanto à ausência._
- `ignored`: _Define os tipos de classes de beans a serem ignorados ao identificar beans correspondentes (desde a versão 1.2.5)._
- `ignoredType`: _Define os nomes das classes de beans a serem ignorados ao identificar beans correspondentes (desde a versão 1.2.5)._
- `annotation`: _Especifica as anotações de nível de classe a serem verificadas quanto à ausência._
- `name`: _Define os nomes de beans a serem verificados quanto à ausência._
- `search`: _Estratégia para considerar a hierarquia do contexto da aplicação._
- `parameterizedContainer`: _Classes adicionais que podem conter os tipos de beans especificados em seus parâmetros genéricos (desde a versão 2.1.0)._



