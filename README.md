# 1. Microservices

 <p>Програм хангамж архитектурын хамгийн чухал бөгөөд түгээмэл чиг хандлагын нэг юм. Amazon, Netflix, Spotify, Uber зэрэг олон компаниудын архитектур үүн дээр суурилсан байдаг.</p>

> Microservices: бие даан ашиглах боломжтой модулиуд.

<strong>Жишээ:</strong> цахим худалдааны системийг дараахь модулиудад хувааж болно.

<div align="center">
  <img src="pics\1\ecomm_system.JPG" alt="E-commerce system">
  <br>
</div>
<br>

<p>Уламжилалт аргаар эдгээр бүх модулийг нэг симтемд хэрэгжүүлдэг. Аль нэг модулийн өөрчлөлтийг зөвхөн бүх програмын шинэ хувилбарыг бүх модулиудтай нь хамтад нь хийж болдог. Гэсэн хэдий ч, модулиудыг <strong>Microservices</strong> болгон хэрэгжүүлэх үед захиалгын үйл явцыг бусад модулиудаас үл хамааран өөрчлөх боломжгүй, харин үүнийг бие даан оруулах боломжтой.</p>

---

## Давуу талууд:

* <h3>Microservices for scaling development</h3>

  <p>Хөгжүүлэлтийн багууд ихэвчлэн нарийн төвөгтэй төслүүд дээр хамтран ажиллах шаардлагатай болдог. Төслүүдийг бие биенээсээ хамааралгүй ажиллах боломжтой жижиг хэсгүүдэд хувааж болно.</p>

<div align="center">
  <img src="pics\1\team_working.JPG" alt="microarchticture team_working">
  <br>
</div>

* <h3>Replacing legacy systems</h3>
* <h3>Sustainable development</h3>
* <h3>Replaceability of microservices</h3>
  <p>Monolithic архитектуртай харьцуулахад Микро сервисийг цаашид хадгалах боломжгүй үед дахин шинэчилэхэд илүү амархан байдаг.</p>
* [<h3>Continuous delivery</h3>](https://continuous-delivery-book.com/)

<div align="center">
  <img src="pics\1\continuous_pipeline.JPG" alt="Microservices continuous delivery pipeline">
  <br>
</div>

* <h3>Robustness</h3>
  <p>Санах ойн алдагдал гарсан тохиолдолд зөвхөн энэ microservices-д нөлөөлж, гацдаг. Бусад service-үүд ажилласаар байна.</p>

* <h3>Free technology choice</h3>
* <h3>Security</h3>

-----

# 2. Micro and Macro Architecture

## Defination:

> micro architecture: comprises all decisions that can be made individually for each microservice.

> macro architecture: consists of all decisions that can be made at a global level and apply to all microservices.

<div align="center">
  <img src="pics\1\micro_macro.JPG" alt="micro and macro architecture">
  <br>
</div>
<br>
<p>макро архитектур нь бүх микро үйлчилгээнд хамаатай бол микро архитектур нь бие даасан микро үйлчилгээтэй харьцдаг бөгөөд ингэснээр микро үйлчилгээ бүр өөрийн гэсэн microservice архитектуртай байдаг.</p>

## Bounded context and strategic design

<p>Regarding to the domain architecture, the concept of micro and macro architecture has long been a common practice. A macro architecture divides the domains into coarse-grained modules. These modules are further divided as part of the micro architecture.</p>

For example, an e-commerce system can be divided into modules and sub-modules as follows:

* Customer registration
* Order process
  * Data validation
  * Freight charge calculation
* Payment
* Shipping

<p>The internal architecture of the order process module is, however, hidden from the outside and can be altered without affecting other modules. This flexibility to change one module without influencing the other modules is one of the main advantages of modular software development.</p>

<div align="center">
  <img src="pics\1\domain_modules.JPG" alt="multiple domain modules">
  <br>
</div>
<br>

* To <strong>search</strong> successfully, data, such as descriptions, images or prices, must be stored for the products. Important customer data can include, for example, the recommendations that can be determined based on past orders.

* To process orders in the <strong>order process</strong> module, the contents of the shopping cart have to be tracked. For products, only basic information is required such as name and price. Similarly, not too much data concerning the customer is necessary. The most important component of the domain model of this module is the shopping cart. It is then turned into an order that has to be handed over and processed by the other bounded contexts.

* For <strong>payment</strong>, the payment-associated information like credit card numbers has to be kept for each customer.

* For <strong>shipping</strong>, the delivery address is required information about the customer while the size and the weight are necessary information about the product.


## Domain-driven design: defination

<p><strong>Domain-driven design (DDD)</strong> offers a collection of patterns for the domain model of a system. For microservices, the patterns in the area of strategic design are the most interesting. They describe how a domain can be subdivided.</p>

* Domain-driven design offers many more patterns that, for example, facilitate the model of individual modules. The original [DDD book](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215) provides a lot more information. It introduces the term “domain-driven design” and comprehensively describes DDD.

* The more compact book [Domain-driven Design Distilled](https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420) focuses on design, bounded context, and domain events.

* The [Domain-Driven Design Reference](https://domainlanguage.com/ddd/reference/) is also by the author of the original DDD book. It contains all DDD patterns but without any additional explanation or examples.

## User interface

<p>If microservices have their own user interface (UI), the look and feel of microservices can be a micro or macro architecture decision.</p>

<p><strong>Micro</strong>: sometimes a system has different types of users (back office and customers, for example) with different requirements for the UI which are often incompatible with a uniform look and feel. A micro architecture decision for the UI is suitable in this case.</p>

  * Often there are concerns that a microservice level decision will cause inconsistencies in the look and feel; however, the UI can also diverge in a monolithic system. Hence, defining appropriate style guides and artifacts is the only way to achieve a consistent look and feel for large systems, regardless of the use of microservices.

<p><strong>Macro</strong>: Often a system should have a uniform UI; therefore, the look and feel must be a macro architecture decision.</p>

  * Shared CSS and JavaScript are often not enough to ensure a common style of the UI of all microservices since uniform technical artifacts can be used to implement very different types of user interfaces. Therefore, a style guide must become part of the macro architecture.

<br>
<div align="center">
    <img src="pics\1\macro_decision.JPG" alt="macro decision">
</div>
<br>

<div align="center">
  <img src="pics\1\micro_decision.JPG" alt="micro decision">
</div>
<br>

### The following table shows the typical micro and macro architecture decisions:

| Micro or Macro      | Micro Architecture | Macro Architecture     |
| :---        |    :----:   |          ---: |
| Programming Language |	Continuous Delivery Pipeline	| Communication Protocol |
| Database |	Authorization |	Authentication |
| Look and Feel |	Tests of the Microservice in Isolation	| Integration Tests
| Documentation	| | |

----

# 3. Docker

## What's Docker

<p>Docker represents a lightweight alternative to virtualization. Although Docker does not provide as much isolation as a virtualization, it is practically as lightweight as a process.</p>

## Shared kernel

<p>Instead of having a complete virtual machine of their own, Docker containers share the kernel of the operating system on the Docker host. The Docker host is the system on which the Docker containers run. The processes from the containers, therefore, appear in the process table of the operating system on which the Docker containers are running.</p>

## Optimized file system

<p>
Finally, the file system is optimized. There are layers in the file system. When a microservice reads a file, it goes through the layers from top to bottom until it finds the data. The containers can share layers.
<br>
<br>
The drawing below shows this more precisely. The file system layer at the bottom represents a simple Linux installation with the Alpine Linux distribution. Another layer is the Java installation. Both applications share these two layers, which are stored only once on the hard disk, although both microservices use them.
<br>
<br>
Only the applications are stored in file system layers that are exclusively available to a single container. The lower layers cannot be changed. The microservices can only write to the top layer. The reuse of the layers reduces the storage requirements of the Docker containers.
<br>
<br>
It is easily possible to start hundreds of containers on a laptop. This is not surprising: after all, it is also possible to start hundreds of processes on a laptop. Docker has no significant overhead compared to a process. Compared to virtual machines, however, the performance benefits are outstanding.
</p>

<div align="center">
  <img src="pics\1\layer_docker.JPG" alt="File system Layers in Docker">
</div>
<br>
<br>
<div align="center">
  <img src="pics\1\docker_overview.JPG" alt="Docker overview">
</div>
<br>

* The Docker host is the machine on which the Docker containers run. It can be a virtual machine or a physical machine.

* Docker containers run on the Docker host.

* The containers typically contain a process.

* Each container has its own network interface with its own IP address. This network interface is only accessible from the Docker internal network. However, there are also ways to allow access from outside this network.

* In addition, each container has its own file system.

* When a container is started, the Docker image creates the first version of the Docker file system. When the container has been started, the image is extended by another layer into which the container can write its own data.

* All Docker containers share the kernel of the Docker host.

## Dockerfiles

<p>The creation of Docker images is done via files named Dockerfile. One of Docker’s strengths is that <a href="https://docs.docker.com/engine/reference/builder/">Dockerfiles</a> are easy to write and therefore, the rolling out of software can be automated without any problems.</p>

- <strong>FROM</strong> The creation of Docker images is done via files named Dockerfile. One of Docker’s strengths is that Dockerfiles are easy to write and therefore, the rolling out of software can be automated without any problems.

- <strong>RUN</strong> defines commands that execute to create the Docker image. In essence, a <b>Dockerfile</b> is a shell script that installs the software.

- <strong>CMD</strong> defines what happens when the Docker container is started. Typically, only one process should run in one Docker container. This is started by <b>CMD</b>.

- <strong>COPY</strong> copies files in the Docker image. <b>ADD</b> does the same; however, it can also unpack archives and download files from a URL on the Internet. <b>COPY</b> is simpler to understand because it does not extract archives, for example. Also, from a security perspective, it can be problematic to download software from the Internet into Docker containers. Therefore, <b>COPY</b> should be given preference over <b>ADD</b>.

```sql
  FROM openjdk:11.0.2-jre-slim
  COPY target/customer.jar .
  CMD /usr/bin/java -Xmx400m -Xms400m -jar customer.jar
  EXPOSE 8080
```

#### A Dockerfile for obtaining a Ubuntu installation with updates looks like this:

```sql
FROM ubuntu:15.04
RUN apt-get update ; apt-get dist-upgrade -y -qq
```

# 4. Technical Micro Architecture

> Microservices давуу талуудын нэг нь microservice тус бүрт өөр өөр технологи ашиглах боломжтой байдаг.

## Requirements

<br>
<div align="center">
  <img src="pics\1\micro_arch_req.JPG" alt="Technical micro Architecture">
</div>
<br>

### Communication

<p>Microservices have to communicate with other microservices. This requires UI integration in the web UI or protocols such as REST or messaging.</p>

> It is a macro architecture decision which communication protocol is used (see [Architecture Decisions](https://www.educative.io/courses/introduction-microservice-principles-concepts/x1AxVB44q19)).

> The macro architecture decision influences the micro architecture.

### Operation
<br>

- <b>Configuration</b>

  <p>The microservice has to be adapted to different scenarios. It is possible to use custom code for reading the configuration. However, an existing library can facilitate this task and promote a uniform application configuration.</p>

<br>
<div align="center">
  <img src="pics\1\configuration.JPG" alt="configuration">
</div>
<br>

- Deployment

  <p>The microservice has to be installed in an environment and has to run in this environment.</p>

  <br>
  <div align="center">
    <img src="pics\1\deployment.JPG" alt="deployment">
  </div>
  <br>  

- Logs

  <p>Writing log files is easy. However, the format should be uniform for all microservices.

  In addition, a simple log file is not enough when a server has to collect the logs from all microservices and provide them for analysis.

  Therefore, technologies have to be in place for formatting the log outputs and for sending them to the server where all logs are stored and analyzed.
  </p>

  <br>
  <div align="center" >
    <img src="pics\1\logs.JPG" alt="logs">
  </div>
  <br>

- Metrics

  <p>Metrics have to be delivered to the central monitoring infrastructure.

  This requires appropriate frameworks and libraries. In principle, different libraries can be used for implementing a macro architecture rule for which instance predefines a log format and a log server.

  In this case, the micro architecture has to choose a library for the microservice. Macro architecture rules can also determine the library.

  However, this limits the technological freedom of the microservices to those programming languages which can use the chosen library.
  </p>
