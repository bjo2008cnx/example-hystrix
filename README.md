Hystrix Samples
---------------
按以下顺序启动应用程序：

*运行Eureka - 在技术上不需要，但避免其他应用程序
在控制台上找不到Eureka时出现错误，终端位于http://localhost：8761
    cd sample-eureka
    mvn spring-boot:run

*启动Hystrix仪表板应用程序。 这将用于显示Hystrix命令指标，端点可在http：// localhost：8080获得
    cd sample-hystrix-dashboard
    mvn spring-boot:run

* 启动示例服务，端点可在http：// localhost：8889获取
    cd service1
    ./gradlew runApp

* 启动客户端应用程序，端点可在http：// localhost：8888获得

    cd aggregate
    ./gradlew runApp

Endpoints
---------

应该有以下端点可以演示不同的Hystrix功能，请查看http：// localhost：8080 / hystrix.dashboard上的Hystrix仪表板，并使用http：// localhost：8888 / hystrix.stream上提供的Hystrix流
. http://localhost:8888/hello?greeting=World -

Simple Hello World Hystrix Command

. http://localhost:8888/helloObservable?greeting=World - Hello World Command using `HystrixObservableCommand`.

. http://localhost:8888/fallback - Sample Fallback Example

. http://localhost:8888/message?message=Hello&delay_by=0&throw_exception=false - Endpoint which makes a remote request behind a Hystrix command, play around with `delay_by` and `throw_exception` parameters.

.  http://localhost:8888/messageSemaphore?message=Hello&delay_by=0&throw_exception=false - Endpoint which makes a remote request behind a Hystrix command but using Semaphore based isolation strategy, play around with `delay_by` and `throw_exception` parameters.

.  http://localhost:8888/messageCached?message=Hello&delay_by=500&throw_exception=false - Hystrix Command with Caching

. http://localhost:8888/sampleCollapser?id=1 - Hystrix Request Collapsing
