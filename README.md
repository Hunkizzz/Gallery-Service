### Netflix OSS 

##### Used: Eureka Server, Config Server, Config Client, Zuul Api Gateway, Feign Client, RestTemplate, WebClient, Hystrix, Ribbon, Security (JWT), Spring WebFlux + MongoDB + Docker

_____

### Introduction

Мое знакомство со стеком началось больше полугода назад, и я нашел в нем определенные классные фичи, которые работают из коробки и которые, как мне кажется, достаточно интересные.
Я начал писать статьи в блоге и частично переводить документацию на русский язык, т.к. на русском довольно простой и понятной документации я не нашел, когда изучал данный материал.

В ходу статьи буду стараться давать ссылки на свои статьи. 
Надеюсь кто-то найдет из этого что-нибудь полезное.

В этом небольшом примере рассмотрим все из вышеуказанных топиков.
В этом примере я намешал всего и постарался показать все фишки вместе. Не пугайтесь :) 

Я понимаю, что далеко до совершенства, но цель данного примера показать стандартные возможности Spring Cloud (Netflix OSS).

Если вы нашли какие-либо неточности или видите, что можно что-то улучшить, предложите свои изменения и я с радостью добавлю их. Давайте сделаем это вместе :)

____

### Cloud Computing
    
Облачные вычисления — это предоставление вычислительных служб (серверов, хранилища, баз данных, сетей, программного обеспечения, аналитики и т.д.) посредством интернета. 
Такие службы ускоряют внедрение каких-либо инноваций, повышают гибкость ресурсов и обеспечивают экономию благодаря высокой масштабируемости. 
Пользователь обычно платит только за облачные службы, которые он использет.
    
`Какие проблемы это решает ?`  
- Затраты

Облачные вычисления позволяют избежать капитальных затрат на приобретение оборудования и программного обеспечения, настройку и эксплуатацию.

- Скорость

Большинство облачных вычислительных служб предоставляются в режиме самообслуживания и по запросу.

- Глобальный масштаб

Преимущества служб облачных вычислений включают возможность эластичного масштабирования. 

- Производительность

Для локальных центров обработки данных обычно требуются много стоек и серверов, а также настройка оборудования. Облачные вычисления позволяют избежать многих из этих задач.
Самые большие облачные вычислительные службы работают в мировой сети безопасных центров обработки данных, которые регулярно обновляются до самого последнего поколения быстрого и эффективного вычислительного оборудования. 

- Надежность

Облачные вычисления делают резервное копирование данных, аварийное восстановление и непрерывность бизнес-процессов 

- Безопасность

Многие поставщики облачных служб предлагают широкий набор политик, технологий и средств контроля, которые в целом повышают уровень безопасности, помогая защитить данные, приложения и инфраструктуру от потенциальных угроз.
    
_____

### Зачем Spring Cloud если есть Kubernetes ?

Если вам нужны некоторые из ваших микросервисов на другом языке, то `Kubernetes` может это сделать, если не бояться потратить деньги на инвестиции в ваш технический стек, чтобы иметь более широкую и менее зависимую систему.

Если вам нужна быстрая разработка, хорошо интегрированная со стеком Spring без большого участия DevOps - то здесь не обойтись без `Spring Cloud`.


`Spring Cloud` имеет богатый набор хорошо интегрированных библиотек Java для решения всех проблем во время выполнений. 
В результате у самих микросервисов есть библиотеки для различных задач: 

- для обнаружения клиентов
- для балансировки нагрузки
- для обновления конфигурации
- для отслеживания показателей и т.д. 

`Kubernetes` предназначен не только для платформы Java, и решает проблемы распределенных вычислений в общем для всех языков. 
Он предоставляет услуги по управлению конфигурацией, обнаружению сервисов, балансировке нагрузки, трассировке, метрикам, запланированным заданиям и т.д. 

Некоторые библиотеки, такие как `Hystrix`, `Spring Boot`, одинаково полезны для обеих сред. Есть области, где обе платформы являются `взаимодополняющими` и могут быть объединены вместе для создания более мощного решения (такие примеры - `KubeFlix` и `Spring Cloud Kubernetes` например).

##### Spring Cloud Kubernetes:

    https://github.com/spring-cloud/spring-cloud-kubernetes
    http://www.ofbizian.com/2016/12/spring-cloud-compared-kubernetes.html

Он нужен чтобы облегчить интеграцию приложений Spring Cloud и Spring Boot, работающих в Kubernetes.

##### KubeFlix:

Kubernetes integration with Netflix

    https://blog.fabric8.io/kubeflix-kubernetes-integration-with-netflix-69f76d27ef91

____

### Netflix

##### Что такое Netflix ?

Немного биографии.

`Netflix` - это американская развлекательная компания, предоставляющая услуги видео онлайн (online Video streaming) и видео по запросу (Video on demand), основана в 1997 году, штаб-квартира находится в Лос Гатос, Калифорния. Изначально она являлась компанией по дистрибуции  DVD, модель продажи былла отправка  DVD по почте покупателям (DVD Emailing).

В 2006 году `Amazon` объявила о своем большом проекте и совсем не связано с индустрией их бизнеса, это "облачные вычисления" (Cloud computing). 

Сервис, который позже был назван как Amazon S3 (Amazon Simple Storage Service) позволяет пользователям сохранять свои данные в облачных серверах и иметь доступ всегда и везде.

`Netflix` понял что Amazon является нужным для них партнером. Вместо того, чтобы инвестировать много денег в сервера, можно использовать инфраструктуру у Amazon. Так и началось их сотрудничество.

На данный момент Netflix является самой большоей компанией в мире предоставляющей сервис онлайн фильмов и видео по запросу (video on demand).

Почти все ресурсы  Netflix развернуты на  Amazon Web Service (AWS). 

Ниже приведено изображение архитектуры их системы в качестве примера:

![alt text](http://mike.blogs.com/.a/6a00d83451c1bb69e2014e8948cca8970d-pi)

____

### Eureka Server

`Eureka Server` — это приложение, которое содержит информацию обо всех клиентских сервисных приложениях. 
Каждый микросервис регистрируется на сервере Eureka, и Eureka знает все клиентские приложения, работающие на каждом порту и IP-адресе. 
Eureka Server также известен как Discovery Server.

Его аналоги:
- Consul
- Zookeeper
- Cloud Foundry

Если простыми словами, то — это сервер имен или реестр сервисов. Обязанность — давать имена каждому микросервису.
Регистрирует микросервисы и отдает их ip другим микросервисам.

Таким образом, каждый сервис регистрируется в Eureka и отправляет эхо-запрос серверу Eureka, чтобы сообщить, что он активен.

Для этого сервис должен быть помечен как `@EnableEurekaClient`, а сервер `@EnableEurekaServer`.

При указании аннотаций `@EnableDiscoveryClient` тоже отработает, т.к. Eureka является Discovery сервисом, но вот в случае если использовать наоборот - юбой другой Dicovery сервис и использовать аннотацию `@EnableEurekaClient`, так уже не получится.

Eureka Client сбрасывает все HTTP-соединения, которые простаивали более 30 секунд, которые он создал для связи с сервером.

Клиент взаимодействует с сервером следующим образом:

1) Eureka Client регистрирует информацию о запущенном экземпляре на сервере Eureka.

2) Каждые 30 секунд Eureka Client отсылает запрос на сервер и информирует сервер о том, что он (экземпляр) еще жив.
Если сервер не видел обновления в течение 90 секунд, он удаляет экземпляр из своего реестра.

3) Eureka Client получает информацию реестра от сервера и кэширует ее у себя локально. 
Эта информация обновляется периодически (каждые 30 секунд), получая обновления между последним апдейтом и текущим. 
Клиент автоматически обрабатывает дублирующую информацию.

4) Получив обновления, клиент сверяет информацию с сервером, сравнивая количество экземпляров, возвращаемых сервером, и если информация по какой-либо причине не совпадает, вся информация реестра извлекается снова.
Клиент получает информацию в сжатом формате JSON, используя клиент jersey apache.

5) При завершении работы клиент отправляет запрос отмены на сервер. 
Таким образом экземпляр удаляется из реестра экземпляров сервера.
Eureka использует протокол, который требует, чтобы клиенты выполняли явное действие отмены регистрации.

Клиенты, которые использовали 3 неудачные попытки синхронизации с сервером с интервалом в 30 секунд будут удалены автоматически.

##### Взаимодействие серверов между собой:

Серверы Eureka взаимодействуют друг с другом, используя тот же механизм, который используется между клиентом и сервером.

Когда сервер запускается, он пытается получить всю информацию реестра экземпляра от соседнего узла. 

Если при получении информации от узла возникает проблема, сервер проверяет все равноправные узлы.

В случае проблем сервер пытается защитить уже имеющуюся у него информацию.

Более подробную информацию про Eureka вы можете прочитать в моей статье.
Надеюсь она будет полезна.

    https://medium.com/@kirill.sereda/spring-cloud-netflix-eureka-%D0%BF%D0%BE-%D1%80%D1%83%D1%81%D1%81%D0%BA%D0%B8-5b7829481717

Подсказки для настроек в файлах `application.property, application.yml`:

    https://cloud.spring.io/spring-cloud-static/Dalston.SR5/multi/multi__appendix_compendium_of_configuration_properties.html

Минимальные настройки eureka server - это порт и имя, а также `@EnableEurekaServer` над основным классом. Этого будет достаточно.

В нашем примере мы указали следующие настройки в файле `application.yml`

    spring:
      application:
        name: eureka-server
    
    server:
      port: ${PORT:8761}
    
    eureka:
      client:
        register-with-eureka: false  
        fetch-registry: false        
        instance-info-replication-interval-seconds: 10   
      server:
        eviction-interval-timer-in-ms: 50000
        wait-time-in-ms-when-sync-empty: 5

Наш сервер работает на порту 8761 с именем eureka-server.

Более детальное описание других настроек можно увидеть в коде на github.

Ссылка на Eureka Server:

    https://github.com/ksereda/Gallery-Service/tree/master/eureka-server
    
Некоторые настройки в `application.yml` закомментированы. Не обращайте на них внимание, к ним вернемся чуть позже.
    
Основной класс:

    @SpringBootApplication
    @EnableEurekaServer
    public class EurekaServerApplication {
    
    	public static void main(String[] args) {
    		SpringApplication.run(EurekaServerApplication.class, args);
    	}
    
    }
    
Запустите приложение и перейдите в браузере

    http://localhost:8761
    
Вы увидите дашборд для управления.

![alt text](https://www.baeldung.com/wp-content/uploads/2016/08/Screenshot_20160819_073151.png)

___

### Eureka Client

Для того, чтобы сервис стал клиентом Eureka, ему необходимо над основным классом указать `@EnableEurekaClient`

    @SpringBootApplication
    @EnableEurekaClient
    public class GalleryServiceApplication {
    
        public static void main(String[] args) {
            SpringApplication.run(GalleryServiceApplication.class, args);
        }
    
    }

В нашем примере все остальные сервисы будут по совместительству клиентами Eureka, не важно, каку функцию они выполняют.

___

### Gallery-Service

Рассмотрим `gallery-service`.

Он представляет обычный CRUD.

Мы будем использовать базу MongoDB, Spring WebFlux для реактивности и Lombok.

У нас есть Bucket модель с темами для изучения 

    @Data
    @Builder
    @AllArgsConstructor
    @Document(collection = "buckets")
    public class Bucket {
    
        @Id
        private String id;
    
        @NotBlank
        @Size(max = 10)
        private String title;
    
        private String description;
        private int personalNumber;
        private String imageLink;
    
    }
    
У нас есть контроллер `BucketController` , который обрабатывает запросы через реактивный репозиторий

    @Repository
    public interface BucketRepository extends ReactiveMongoRepository<Bucket, String> {
    }

Все достаточно просто.

Файл настроек также прост

    spring:
      application:
        name: gallery-service
      data:
        mongodb:
          uri: mongodb://localhost:27017/gallerydb
    
    server:
      port: 8081
    
    eureka:
      client:
        serviceUrl:
          defaultZone: ${EUREKA_URI:http://localhost:8761/eureka}
      instance:
        preferIpAddress: true

Используем MongoDB в докере на порту 27017 с именем базы gallerydb

Запустите Eureka Server вначале, а затем запустите наш сервис и перейдите на

    http://localhost:8081/
    
чтобы получить информацию что наш сервис работает.

Если вы перейдете в Eureka

    http://localhost:8761
    
Вы увидите что Eureka увидела наш сервис (имя и на каком порту он работает).
Сервер и клиент обменялись эхо запросами и поддерживают связь.

Также при старте gallery-service в консоли вы можете увидеть строки

    2019-08-29 15:53:41.923  INFO [gallery-service,,,] 1333 --- [  restartedMain] com.netflix.discovery.DiscoveryClient    : Getting all instance registry info from the eureka server
    2019-08-29 15:53:42.389  INFO [gallery-service,,,] 1333 --- [  restartedMain] com.netflix.discovery.DiscoveryClient    : The response status is 200
    
    2019-08-29 15:53:42.410  INFO [gallery-service,,,] 1333 --- [  restartedMain] o.s.c.n.e.s.EurekaServiceRegistry        : Registering application gallery-service with eureka with status UP
    
что означает, что сервис зарегистрировался в Eureka и получил подтверждение.

Непосредственно в консоли самой Eureka можно увидеть следующее

    2019-08-29 15:53:42.484  INFO 1053 --- [nio-8761-exec-1] c.n.e.registry.AbstractInstanceRegistry  : Registered instance GALLERY-SERVICE/192.168.97.121:gallery-service:8081 with status UP (replication=false)
    2019-08-29 15:53:43.056  INFO 1053 --- [nio-8761-exec-3] c.n.e.registry.AbstractInstanceRegistry  : Registered instance GALLERY-SERVICE/192.168.97.121:gallery-service:8081 with status UP (replication=true)
    
Eureka успешно зарегистрировала gallery-service.

Вы также можете запустить gallery-service не запуская перед ним Eureka, тогда вы увидите что сервис поднялся, но не смог зарегистрироваться в Eureka и получите сообщение об ошибке

    2019-08-29 15:58:42.529  WARN [gallery-service,,,] 1333 --- [freshExecutor-0] c.n.d.s.t.d.RetryableEurekaHttpClient    : Request execution failed with message: java.net.ConnectException: В соединении отказано (Connection refused)
    2019-08-29 15:58:42.529 ERROR [gallery-service,,,] 1333 --- [freshExecutor-0] com.netflix.discovery.DiscoveryClient    : DiscoveryClient_GALLERY-SERVICE/192.168.97.121:gallery-service:8081 - was unable to refresh its cache! status = Cannot execute request on any known server
    
    com.netflix.discovery.shared.transport.TransportException: Cannot execute request on any known server
    
Но вы сможете работать с ним.

Каждые 30 секунд сервис будет слать эхо запрос на Eureka и ждать что она ответит ему взаимностью.

Ссылка на gallery-service

    https://github.com/ksereda/Gallery-Service/tree/master/gallery-service
    
Некоторые настройки в `application.yml` закомментированы. Не обращайте на них внимание, к ним вернемся чуть позже.

В основном классе я указал

    	@Bean
    	CommandLineRunner run(BucketRepository bucketRepository) {
    		return args -> {
    			bucketRepository.deleteAll()
    					.thenMany(Flux.just(
    							new Bucket("1", "Java", "OOP", 280, "http://infopulse-univer.com.ua/images/trenings/java.png"),
    							new Bucket("2", "Java", "Steram API", 437, "https://www.hdwallpaperslife.com/wp-content/uploads/2018/09/JAVA14-480x270.png"),
    							new Bucket("3", "Java", "Collections", 14, "https://i.ytimg.com/vi/oOOESCvGGcI/hqdefault.jpg"),
    							new Bucket("4", ".NET", "Basic", 1213, "https://upload.wikimedia.org/wikipedia/commons/0/0e/Microsoft_.NET_logo.png"),
    							new Bucket("5", "C++", "Basic", 870, "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSmgIz9Ug-MVzBQJMcgXedOXTqHWGmbSu5pPDivz8hrfo_GE0HZEA"),
    							new Bucket("6", "JavaScript", "Angular 8", 155, "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTg41zepuyHbew8bIsTYeKWJ9RYOnnV922lNa85-fQTVrKDG19K2w")
    					)
    							.flatMap(bucketRepository::save))
    					.thenMany(bucketRepository.findAll())
    					.subscribe(System.out::println);
    
    		};
    	}

чтобы при старте приложения атвоматически создались данные, которые отобразятся в нашей MongoDB (чтобы не создавать вручную).

Как настроить MongoDB я опишу ниже.

Перейдите в браузере на 

    http://localhost:8081/getAll
    
чтобы получить все данные из базы.

Аналогично /create, /update, /delete

- если вы перейдете на

    
    http://localhost:8081/stream/buckets
    
вы получите все данне из базы стримом.

Здесь во всю используется прелесть реактивной системы с 
    
    MediaType.TEXT_EVENT_STREAM_VALUE

- перейдите на

    
    http://localhost:8081/stream/buckets/default

И будете получать каждую секунду новое деволтное значение

- перейдите на

    
    http://localhost:8081/stream/buckets/delay
    
При помощи Flux мы можем получить все обьекты из базы с интервалом в 2 секунды каждый. 
Здесь мы сэмулировали ситуацию, которая позволяет получить данные по мере их поступления. 
Это одна из основных идей реактивного программирования.

Мы подписываемся на поток и ждем данные. Spring сам уведомит нас о поступлении данных.

Основная концепция реактивного программирования базируется на неблокирующем вводе/выводе.

Напрмиер при старте приложения в нашей базе находится 4 записи а не 6. без использовании реактивности мы бы получили 4 записи. Потом кто-либо в этот промежуток времени добавил еще 2 записи и когда мы сделали второй запрос, мы бы получили 6 записей.

С использованием потоков `Mono/Flux` мы сэмулировали такую ситуацию и за один запрос сможем получить все данные с небольшим интервалом.

____

### Reactive

##### Зачем использовать реактивные типы ?

Реактивные типы не предназначены для того, чтобы вы могли обрабатывать ваши запросы или данные быстрее, на самом деле они привносят небольшие накладные расходы по сравнению с обычной блокировкой. 

Их сила заключается в их способности одновременно обслуживать больше запросов и более эффективно обрабатывать операции с задержкой, такие как запрос данных с удаленного сервера. 

Они позволяют вам обеспечить лучшее качество обслуживания и предсказуемое планирование пропускной способности, изначально имея дело со временем и задержкой, не затрачивая больше ресурсов. 

В отличие от традиционной обработки, которая блокирует текущий поток во время ожидания результата, `Reactive API`, который ожидает, ничего не стоит, запрашивает только тот объем данных, который он способен обработать, и предоставляет новые возможности, поскольку он имеет дело с потоком данных, а не только с отдельными элементами.


Следуя документации `Spring WebFlux`, Spring Framework использует Reactor для своей собственной реактивной поддержки. 

`Reactor` - это реализация `Reactive Streams`, которая еще больше расширяет базовый Publisher контракт Reactive Streams с типами Flux и Mono, чтобы обеспечить декларативные операции над последовательностями данных. 

На стороне сервера Spring поддерживает аннотации и функциональные модели программирования. Использование модели аннотаций `@Controller` и других аннотаций также поддерживается Spring MVC. 

Реактивный контроллер будет очень похож на стандартный REST-контроллер для синхронных служб.

##### Что такое WebFlux ?

Обратите внимание, что вам нужна Spring Boot версии 2.xx для использования модуля `Spring WebFlux`.

Для поддержки реактивного программирования и создания реактивных систем команда Spring Boot создала совершенно новый веб-стек под названием `Spring WebFlux`. 
Этот новый веб-стек поддерживает аннотированные контроллеры, функциональные конечные точки, WebClient (аналог RestTemplate в Spring Web MVC), WebSockets и многое другое.

WebFlux по умолчанию использует `Netty`. 
`Tomcat` не поддерживает реактивщину.

Если можно сказать прсотыми словами, то
`Реактивное программирование` — это программирование с асинхронными потоками(streams) данных.
Т.е. можно слушать поток и реагировать на события в нем. Можем фильтровать поток как нам вздумается, объединять потоки, кроме того потоки могут быть входными параметрами других потоков.

`Поток` - это некая последовательность чего-либо, остортированных по времени.
Нам лишь надо подписаться на поток. 
Наблюдатель (observers) подписывается на поток.

##### Основная концепция реактивного программирования:

Неблокирующий ввод/вывод.

Есть два варианта получить данные:

- Pull

Это когда мы сами делаем запрос на получение и нам приходит ответ.

- Push

Когда данные сами нас уведомляют об изменениях и выталкивают данные нам. 

Реактивное приложение, это когда приложение само извещает нас об изменении своего состояния. Не мы делаем запрос и проверяем, а не изменилось ли там что-то, а приложение само нам сигнализирует. 
Ну и конечно эти события, эти сигналы мы соответственно можем обрабатывать.

##### Основные приемущества:

- Реактивность дает слабую связанность.

- В некоторых случаях это дает возможность писать более простой и понятный код. 

Например мы можем взять обычную коллекцию, преобразовать ее к реактивной коллекции и тогда мы будем иметь коллекцию событий об изменении данных в ней. 
Мы очень просто получаем только те данные, которые изменились. 
По этой коллекции мы можем делать выборку, фильтровать и т.д. 

Если бы мы это делали традиционным способом, то нам нужно было бы закэшировать текущие данные, потом делать запрос на получение новых данных и сравнить их с текущим значением. Не удобно.

Чтобы получить данные, мы обращаемся к базе данных, получаем данные и отдаем пользователю.
Если у вас в этот момент времени на секунду пропадет интернет то вы получите ошибку. Беда.

Реактивщина нам поможет в данном случае.

Аналог для примера: Gmail, Facebook, Instagram, Twitter. 
Когда у вас плохой интернет, вы не получаете ошибку, а просто ждете результат больше обычного. 

##### Обязанности:

- Приложение должно отдавать пользователю результат за полсекунды

- Обеспечить отзывчивость под нагрузкой

- Система остается в рабочем состоянии даже, если один из компонентов отказал.

- Elastic: Данный принцип говорит о том, что система должна занимать оптимальное количество ресурсов в каждый промежуток времени.

- Общение между сервисами должно происходить через асинхронные сообщения. Это значит, что каждый элемент системы запрашивает информацию из другого элемента, но не ожидает получение результата сразу же. Вместо этого он продолжает выполняеть свои задачи.


##### Когда стоит использовать ?

Реативщину стоит использовать, когда есть поток событий, растянутый во времени (например, пользовательский ввод).

Функционал, написанный при помощи реактивных потоков, может быть легко дополнен и расширен.

Что касается меня, я сильно запарился по этой теме :)
Но это вовсе не значит что надо использовать реактивщину везде.

____

### MongoDB

Я запускаю MongoDB в докере.

При условии что у вас установлен docker, приступим.

    docker pull mongo
    
Docker сольет с docker-hub актуальную версию

Проверить можем так

    docker images

В результате увидим все текущие образы, которые у вас скачаны (на данный момент у вас должен быть он всего один, при условии что вы раньше не пользовались docker)

##### Запуск Mongo

По умолчанию используется порт 27017, поэтому можем не указывать его

    docker run mongo

или можете явно указать порт

    docker run mongo --port 27017

Открываем новую консоль, пишем

    mongo

Вы попали в оболочку Mongo.

При условии что вы запустили Eureka Server и gallery-service (он настроен с MongoDB на порту 27017) вы можете в оболочке Mongo написать

    use gallerydb
    
где `gallerydb` - Это имя базы (см файл `application.yml`)

Затем выполнить в ней

    show collections
    
и вы увидите объект `buckets` (см Bucket класс)

Затем выполнить 

    db.buckets.find()
    
И вы получите все данные (6 объектов), которые создались по умолчанию при старте приложения.

Если хотите запустить вторую Mongo на другом порту

    docker run mongo --port 27018
    
Открываем новую консоль, пишем

    mongo

Я также написал статью для более подробной информации:

    https://medium.com/@kirill.sereda/%D0%B7%D0%B0%D0%BF%D1%83%D1%81%D0%BA-%D0%BD%D0%B5%D1%81%D0%BA%D0%BE%D0%BB%D1%8C%D0%BA%D0%BE-mongodb-%D0%B2-docker-7667c04d8e7d

____

### User-Service

В нашем примере также есть `user-service`.

Он будет общаться с `gallery-service` и будет получать данные из базы данных непосредственно через `gallery-service`.

Сам он с БД не связан.

Есть несколько вариантов использования данной коммуникации:

- RestTemplate

- Feign Client

- WebClient (поскольку у нас реактивная система). 
Т.к. `Feign Client` не дружит с реактивщиной (хотя недавно вышел патч для использования Feign в реактивной системе - Reactive Feign Client, или можно использовать OpenFeign - реализация от Netflix, либо же использовать спецаильный для этого WebClient)

В данном примере мы рассморим все 3 варианта.

В кратце:

Наш `user-service` будет получать данные из `базы данных` через `gallery-service`. 
В случае выхода из строя БД или `gallery-service` мы будем использовать библиотеку `Hystrix`, которая вместо ошибки будет возвращать нам дефолтное значение либо вы можете настроить реплику сервиса `gallery-service`, и в случае выхода из строя самого сервиса, вы будете обращаться к его реплике. 
Пользователь ничего не заметит.
Очень удобно.
Также наш user-service будет использовать `Ribbon` - балансировщик нагрузки между репликами другим сервисов.
У нас будет Movie-service с запасной репликой, и мы натсроим `Load Balancer`.
Также к user-service я прикрутил `ELK (Elastic Search Kibana)` для просмотра логов.
Также ы прикрутим сюда `JWT Security` и только admin сможет создавать новые Bucket в базе данных.


Сам user-service находится по ссылке:

    https://github.com/ksereda/Gallery-Service/tree/master/user-service
    
    
Настройки в файле `application.yml` аналогичные gallery-service.

Те настройки, которые закоментированы, мы рассмотрим чуть позже, когда дойдем до `Config Server` и `Config Client`.


У нас есть `UserController`, в котором мы будем общаться с gallery-service через RestTemplate, FeignClient и WebClient.

Также у нас есть `LogInterceptor`, который будет выводить в консоль время выолнения нашего каждого запроса на нашем сервисе.

Также у нас есть точно такой же класс Bucket (как и в gallery-service) - это обязательное условие для общения через FeignClient и WebClient.
Но здесь Lombok мы не сможем применить, т.к. WebClient с ним не особо дружит.

В этом примере я намешал всего и постарался показать все фишки вместе. Не пугайтесь :) 

____

### Feign Client

Это простой и гибкий http-клиент, который нативно интегрирован с `Ribbon`.

`Feign` использует интерфейсы аннотированные `@FeignClient` чтобы генерировать API запросы и мапить ответ на Java классы.

Он шлет http запросы другим сервисам.
 
Его особенность в том, что нам не нужно знать где и на каком порту находится какой-то сервис.

Мы просто говорим Feign клиенту, иди к “Васе” и получи у него всех пользователей. Далее Feign обращается к Eureka Server и спрашивает где находится “Вася”.

Если “Вася” регистрировался в Eureka Server, то Eureka будет всё знать о “Васе” (где он находится, на каком порту, его URL и т.д.).

Вам нужно только описать, как получить доступ к удаленной службе API, указав такие детали, как URL, тело запроса и ответа, принятые заголовки и т. д. Клиент Feign позаботится о деталях реализации.

`Netflix` предоставляет `Feign` в качестве абстракции для вызовов на основе REST, благодаря которым микросервисы могут связываться друг с другом, но разработчикам не нужно беспокоиться о внутренних деталях REST.

Нужно указать аннотацию `@EnableFeignClients` над основным классом.

Теперь у нашего `user-service` будут уже 3 аннотации

    @SpringBootApplication
    @EnableEurekaClient
    @EnableFeignClients


На интерфейс ставим аннотацию `@FeignClient(name = “Вася”)` и указываем имя того сервиса, который нам нужен (в пояснении я описывал сервис под названием “Вася”). 
В том сервисе будет выполняться некая логика по работе с базой и настройки коннекта к базе, или получение всех пользователей и т.д.

Более детально про замечательный Feign Client я написал в статье:

    https://medium.com/@kirill.sereda/spring-cloud-netflix-feign-%D0%BF%D0%BE-%D1%80%D1%83%D1%81%D1%81%D0%BA%D0%B8-7b8272e8e110
    
В нашем примере в `UserController` мы указали путь

        @RequestMapping(path = "/getAllDataFromGalleryService")
        public List<Bucket> getDataByFeignClient(Model model) {
            List<Bucket> list = ServiceFeignClient.FeignHolder.create().getAllEmployeesList();
            return list;
        }
        
Теперь нам необходимо сделать сервис с бизнес логикой.
Делаем интерфейс `ServiceFeignClient`

    @FeignClient(name = "gallery-service", url = "http://localhost:8081/", fallback = Fallback.class)
    public interface ServiceFeignClient {
    
        class FeignHolder {
            public static ServiceFeignClient create() {
                return HystrixFeign.builder().encoder(new GsonEncoder()).decoder(new GsonDecoder()).target(ServiceFeignClient.class, "http://localhost:8081/", new FallbackFactory<ServiceFeignClient>() {
                    @Override
                    public ServiceFeignClient create(Throwable throwable) {
                        return new ServiceFeignClient() {
                            @Override
                            public List<Bucket> getAllEmployeesList() {
                                System.out.println(throwable.getMessage());
                                return null;
                            }
                        };
                    }
                });
            }
        }
    
        @RequestLine("GET /show")
        List<Bucket> getAllEmployeesList();
    
    }

Смотрите, здесь мы указываем имя сервиса, к которому хотим обратиться (в аннотации), затем указываем, что в случае ошибки (недоступнсоти сервиса gallery-service или базы данных) у нас отработает наш кастомный Fallback класс с какой-то нашей кастомной логикой.

В самой реализации Feign мы должны использовать GsonEncoder и GsonDecoder - для этого добавить зависимости в pom.

Во всей этой неразберихе у нас вызывается в итоге метод `getAllEmployeesList`

    @RequestLine("GET /show")
    List<Bucket> getAllEmployeesList();
    
Внимание!

Метод должен иметь возвращаемое значение и по сигнатуре быть точно таким же как и метод на gallery-service, который мы вызываем, а именно метод по пути

    /show
    
Сам путь также должен быть идентичным.

Идем в наш gallery-service и видим вызываемый нами метод на получение всех данных

        @GetMapping(path = "/show")
        public Flux<Bucket> getAllEmployeesList() {
            return bucketRepository.findAll();
        }
        
Теперь когда мы будем вызывать URL 
 
    http://localhost:8082/getAllDataFromGalleryService
    
на нашем user-service, он посмотрит на аннотацию @FeignClient(name = “gallery-service”) и увидит, что там указан сервис `gallery-service`, он пойдет в Eureka Server, спросит про `gallery-service`, Eureka Server скажет ему где он находится и Feign Client по этому же URL в BucketController вызовет метод 

        @GetMapping(path = "/show")
        public Flux<Bucket> getAllEmployeesList() {
            return bucketRepository.findAll();
        }
        
Все очень просто.

____


### RestTemplate

