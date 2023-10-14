# Anotações do Framework Spring

_Este documento descreve várias anotações disponíveis no Spring Framework, organizadas por módulos em ordem alfabética._

## Índice

- [Spring Boot 3.1.4](#Spring-boot 3.1.4)
- [Spring Data JPA](#spring-data-jpa)
- [Spring Security](#spring-security)
- ...

## Spring-boot 3.1.4

<span style="color:yellow"><strong>@ConfigurationProperties</strong></span> : _Mapeia propriedades de configuração definidas em arquivos de propriedades ou YAML para objetos Java._

**Parâmetros:**

- `prefix`: O prefixo das propriedades a serem vinculadas.
- `ignoreInvalidFields`: Sinalizador para indicar que, ao vincular a este objeto, campos inválidos devem ser ignorados.
- `ignoreUnknownFields`: Sinalizador para indicar que, ao vincular a este objeto, campos desconhecidos devem ser ignorados.

<span style="color:yellow"><strong>@ConfigurationPropertiesBinding</strong></span> : _É uma anotação do Spring Boot usada para criar conversores personalizados para propriedades de configuração._

<span style="color:yellow"><strong>@ConfigurationPropertiesScan</strong></span> : _É uma anotação do Spring Boot usada para escanear pacotes em busca de classes de propriedades de configuração._

**Parâmetros:**

- `basePackages`: _Path de pacotes do projeto para verificar propriedades de configuração._
- `basePackageClasses`: _Alternativa ("Type-safe") especificando os pacotes para verificar as propriedades de configuração. O pacote de cada classe especificada será verificado._

<span style="color:yellow"><strong>@ConstructorBinding</strong></span> : _É uma anotação do Spring Boot que indica a vinculação de propriedades de configuração a construtores, facilitando a criação de objetos imutáveis._

<span style="color:yellow"><strong>@DefaultValue</strong></span> : _É uma anotação do Spring Boot que pode ser usada para especificar o valor padrão ao vincular a uma propriedade imutável. Essa anotação também pode ser usada com propriedades aninhadas para indicar que um valor deve sempre ser vinculado (em vez de vincular nulo). O valor desta anotação só será utilizado se a propriedade não for encontrada nas fontes de propriedades utilizadas pelo **Binder**._

**Parâmetros:**

- `value`: _O valor padrão da propriedade. Pode ser uma matriz de valores para propriedades de coleção ou baseadas em matriz._

<span style="color:yellow"><strong>@DataSizeUnit</strong></span> : _É uma anotação do Spring Boot que pode ser usada para alterar a unidade padrão usada ao converter um DataSize._

**Parâmetros:**

- `value`: _O **DataUnit** a ser usado se nenhum for especificado._

<span style="color:yellow"><strong>@DeprecatedConfigurationProperty</strong></span> : _É uma anotação do Spring Boot usada para marcar propriedades de configuração como obsoletas e fornecer uma mensagem de aviso quando são usadas._

**Parâmetros:**

- `reason`: _O motivo da descontinuação._
- `replacement`: _O valor que deve ser usado (se houver)._

<span style="color:yellow"><strong>@DependsOnDatabaseInitialization</strong></span> : _É uma anotação do Spring Boot que define que um bean depende da inicialização do banco de dados, garantindo que a inicialização do banco de dados seja concluída antes do bean ser criado._

<span style="color:yellow"><strong>@Delimiter</strong></span> : _É uma anotação do Spring Boot que permite definir um delimitador personalizado para valores de propriedades de configuração, especialmente útil ao lidar com listas em propriedades._

**Parâmetros:**

- `value`: _O delimitador a ser usado ou **NONE** se todo o conteúdo precisar ser tratado como um único elemento._

<span style="color:yellow"><strong>@DurationFormat</strong></span> : _É uma anotação do Spring Boot que permite personalizar o formato de durações, como as usadas em propriedades de configuração, para facilitar a leitura e escrita._

**Parâmetros:**

- `value`: _O estilo do formato de duração._

<span style="color:yellow"><strong>@EnableConfigurationProperties</strong></span> : _É uma anotação do Spring Boot usada para habilitar a vinculação automática de propriedades de configuração a classes de configuração._

**Parâmetros:**

- `value`: _Maneira conveniente de registrar rapidamente beans anotados **@ConfigurationProperties** com Spring._

<span style="color:yellow"><strong>@JsonComponent</strong></span> : _É uma anotação do Spring Boot usada para registrar um componente como um manipulador de serialização e desserialização JSON, permitindo personalizar a forma como objetos são convertidos para JSON e vice-versa._

**Parâmetros:**

- `value`: _Indica um nome lógico sugerido para o componente e pode ser convertido em um **bean**. Padrão é uma string vazia._
- `type`: _Define os tipos que o componente manipula para serialização/desserialização. Essa configuração é especialmente importante para deserializadores de chaves (**KeyDeserializer**) e pode ser usada para limitar o tratamento a subclasses de tipos inferidos._
- `scope`: _Especifica o escopo sob o qual o serializador/desserializador deve ser registrado com o módulo. O valor padrão é **Scope.VALUES**, que se aplica a serializadores/desserializadores de conteúdo de valor. O escopo **Scope.KEYS** pode ser usado para serializadores/desserializadores de chaves._

<span style="color:yellow"><strong>@JsonMixin</strong></span> : _É uma anotação que permite criar uma classe que define anotações personalizadas para controlar a forma como objetos são convertidos em JSON ou de JSON para objetos, aplicando essas anotações a classes específicas. Isso facilita a personalização da serialização e desserialização JSON._

**Parâmetros:**

- `value`: _Permite especificar as classes que serão usadas como classes de mistura (mixin classes) para controlar a serialização e desserialização de objetos JSON._

<span style="color:yellow"><strong>@Name</strong></span> : _É uma anotação do Spring Boot que pode ser usada para especificar o nome ao vincular a uma propriedade imutável._

**Parâmetros:**

- `value`: _O nome da propriedade a ser usada para associação._

<span style="color:yellow"><strong>@Nested</strong></span> : _É uma meta-anotação do Spring Boot que deve ser adicionada às anotações que indicam que um campo é do tipo aninhado. Usado para garantir que as dicas de reflexão corretas sejam registradas._

<span style="color:yellow"><strong>@NestedConfigurationProperty</strong></span> : _É uma anotação do Spring Boot usada para indicar que uma propriedade de configuração complexa está aninhada dentro de outra propriedade de configuração._

<span style="color:yellow"><strong>@PeriodFormat</strong></span> : _É uma anotação do Spring Boot que permite personalizar o formato de períodos, como os usados em propriedades de configuração, para facilitar a leitura e escrita._

**Parâmetros:**

- `value`: _O estilo de formato do período._

<span style="color:yellow"><strong>@PeriodUnit</strong></span> : _É uma anotação do Spring Boot que permite definir a unidade padrão para valores de período em propriedades de configuração, simplificando a configuração._

**Parâmetros:**

- `value`: _A unidade de período a ser usada se nenhuma for especificada._

<span style="color:yellow"><strong>@ServletComponentScan</strong></span> : _É uma anotação do Spring Boot usada para escanear pacotes em busca de classes Servlet, Filter e Listener para configuração automática no contexto do aplicativo web._

**Parâmetros:**

- `basePackages`: _Path de pacotes do projeto para verificar propriedades de configuração._
- `basePackageClasses`: _Alternativa ("Type-safe") especificando os pacotes para verificar as propriedades de configuração. O pacote de cada classe especificada será verificado._

<span style="color:yellow"><strong>@SpringBootApplication</strong></span> : _essa anotação diz ao Spring Boot que essa classe deverá ser usada como base para configurar toda nossa aplicação._

**Parâmetros:**

- `exclude`: Uma matriz de classes de configuração para serem excluídas da configuração automática.
- `excludeName`: Uma matriz de nomes de classes de configuração para serem excluídas da configuração automática.
- `scanBasePackages`: Um ou mais pacotes para serem escaneados em busca de componentes anotados.
- `scanBasePackageClasses`: Uma ou mais classes que servem como base para a varredura de pacotes em busca de componentes anotados.
- `nameGenerator`: Uma classe para gerar nomes de beans automaticamente.
- `proxyBeanMethods`: Uma configuração que controla se os métodos de bean devem ser proxy por CGLIB.

<span style="color:yellow"><strong>@SpringBootConfiguration</strong></span> : _É uma anotação do Spring Boot usada para marcar classes de configuração específicas do aplicativo. Ela estende a anotação @Configuration do Spring Framework._

**Parâmetros:**

- `proxyBeanMethods`: _Sinalizador que controla se os métodos de bean devem ser proxy por CGLIB. Por padrão, ele é definido como true. Se definido como false, os métodos de bean não serão proxy._