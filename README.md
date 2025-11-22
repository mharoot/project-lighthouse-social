# project-lighthouse-social

Development of an end-to-end Web project using C#. The topic is a social platform where photos of lighthouses around the world are shared, commented on, and rated. _(You can also follow the project progress on the [YouTube](https://www.youtube.com/playlist?list=PLY-17mI_rla6Kt-Ri6nP1pE62ZyE-6wjS) channel)_ One of my main goals in the project is to reveal the need for legendary topics in the software world as much as possible. For example, creating a project skeleton based on certain principles _(abstractions, dependency inversion, responsibility distribution, etc.)_ without following any architectural pattern, then evaluating the correctness of the approach with questions, identifying open points, and converting it to a standardized architectural pattern.

---

## Current Task List *(as of 10.18.2025)*

### Domain Layer Improvements

- [ ] **EntityBase - Audit Fields:** Audit fields such as `CreatedAt`, `ModifiedAt`, `DeletedAt` can be added to the `EntityBase` class. *(EntityBase.cs:6)*

### Application Layer Improvements

- [ ] **AddCommentHandler - Component Configuration:** Required components need to be configured more cleanly. *(AddCommentHandler.cs:22)*

- [ ] **CreateLighthouseHandler - User ID Management:** In a real application, the user ID should be retrieved from the authentication context. Currently, `Guid.Empty` is used. *(CreateLighthouseHandler.cs:29, 47, 65, 87)*

- [ ] **CreateUserHandler - User ID Management:** In a real application, the user ID should be retrieved from the authentication context. Currently, `Guid.Empty` is used. *(CreateUserHandler.cs:25, 41, 58, 76)*

- [ ] **LighthouseDtoValidator - Primary Key Design:** The primary key design of the table should be reviewed. *(LighthouseDtoValidator.cs:17)*

### Data Layer Improvements

- [ ] **PhotoRepository - ID Assignment via Reflection:** In the `PhotoRepository.MapPhoto` method, IDs are assigned using reflection. This approach should be abandoned in favor of a cleaner solution. *(PhotoRepository.cs:151)*

- [ ] **CachedCountryDataReader - Mapper Usage:** Consider using a mapper between Country and CountryDto. *(CachedCountryDataReader.cs:74)*

### Infrastructure Layer Improvements

- [ ] **ExternalCommentAuditor - Runtime Service Discovery:** The service address should be discovered at runtime, not hardcoded. *(ExternalCommentAuditor.cs:15)*

- [ ] **ExternalCommentAuditor - HashiCorp Consul Integration:** A service discovery mechanism can be set up with HashiCorp Consul. *(ExternalCommentAuditor.cs:16)*

- [ ] **CachedConfigurationService - Cache Invalidation:** Cache invalidation functions can be organized and improved. *(CachedConfigurationService.cs:242)*

### Backoffice Improvements

- [ ] **Lighthouse Create - Unknown Fields:** When creating a lighthouse, fields marked as "Unknown" during photo upload (CameraType, Resolution, Lens, UserId) should be filled with real data. *(Create.cshtml.cs:114)*

- [ ] **Lighthouse Delete - Photo Relation:** When deleting a lighthouse, the ID of the main (primary) photo of that lighthouse should be identified and deleted. Currently, lighthouse ID is assumed to be the same as the photo ID. *(List.cshtml.cs:70)*

- [ ] **Photo Deletion Error Handling:** If lighthouse deletion succeeds but photo deletion fails, the user should be informed and a decision should be made on how to proceed. *(List.cshtml.cs:75)*

### Photo Management Improvements

- [ ] **IsPrimary Business Rule:** A lighthouse can have multiple photos, but only one can be primary. Implementation is required for this rule.

- [ ] **Photo Validation:** A validation mechanism can be added to ensure that there is only one primary photo per lighthouse.

- [ ] **Backoffice Photo Gallery:** A feature to view all photos of a lighthouse and change the primary photo can be added.

### Worker Service Improvements

- [ ] **Event Handler - Switch Case Structure:** Instead of managing different event types with a switch case in `RabbitMqEventConsumerService.ProcessEventAsync`, a more flexible structure should be established. *(RabbitMqEventConsumerService.cs:122)*

- [ ] **PhotoUploadedEventHandler - Missing Business Logic:** The actual business logic should be implemented in `PhotoUploadedEventHandler.HandleAsync`. Currently, only logging is performed. *(PhotoUploadedEventHandler.cs:23)*

---

## Project Topic

Develop a social sharing platform for lighthouse enthusiasts.

## General Features of the Project

- Platform users can share **photos** of lighthouses they capture.  
- Users can learn **comprehensive and detailed information** about lighthouses around the world.  
- Users can **comment on** and **rate** lighthouse photos.

## Goals

The main objectives of developing this project are:

- Learn the C# and .Net platform by creating an example project.  
- Apply regular refactoring to improve the code.  
- Use AI assistants _(minimally)_.  
- Discover, apply, and question fundamental software principles.  
- Identify, discuss, and apply architectural needs in software development.

## Target Audience

### Minimum Profile

- Has basic knowledge of C# programming.  
- Has basic knowledge of Object Oriented Programming (OOP).  
- Is aware of clean code concepts and standards.  
- Queries, researches, evaluates, and applies rather than applying blindly.

### Ideal Profile

- Questions SOLID principles.  
- Has ideas about managing technical debt.  
- Is curious about software architectures.  
- Uses Docker in their own systems.  
- Knows that there are service development standards beyond Web APIs.  
- Is familiar with the challenges of distributed systems.  
- Queries, researches, evaluates, and applies rather than applying blindly.

## Challenges

- Where and how will user-uploaded photos be stored? _(Size, storage location, read/write speeds, distributed topology usage)_  
- How to moderate user comments and prevent undesired content?  
- How to verify that a photo belongs to the correct lighthouse?  
- How to use AI tools during categorization or tagging to check photo authenticity?  
- How to process, validate, and classify photos from multiple users in different locations without impacting system performance?  
- How to prevent chaotic situations in the distributed system involving external services, and ensure system resilience?

## Content Plan

- [x] [Episode 00 - Project Lighthouse Social Introduction](https://youtu.be/xO4S60bfZPU)  
- [x] [Episode 01 - Creating the Domain Project](https://youtu.be/fIsvAwxnnIQ)  
- [x] [Episode 02 - Adding Entity Objects](https://youtu.be/dDZHq-vI18U)  
- [x] [Episode 03 - Adding Enumeration-based Types](https://youtu.be/cCW44l7fgX0)  
- [x] [Episode 04 - Adding Sample Contracts (Interfaces)](https://youtu.be/_cta_s9zM1U)  
- [x] [Episode 05 - Application Layer](https://youtu.be/SmnrE73VvUo)  
- [x] [Episode 06 - Writing Handler Objects](https://youtu.be/x6u7uMxw8qU)  
- [x] [Episode 07 - Unit Tests for Handler Classes](https://youtu.be/P_uRenWyE54)  
- [x] [Episode 08 - Using Validator for DTO Objects](https://youtu.be/MrqTqc9d2q8)  
- [x] [Episode 09 - Using Sonarqube for Technical Debt Prevention](https://youtu.be/XUiG1MwSq1o)  
- [x] [Episode 10 - Adding Comment Audit Component](https://youtu.be/54GMi9i2W-4)  
- [x] [Episode 11 - Developing Comment Moderation Service with OpenAI Moderation API](https://youtu.be/PU9SqkPt41o)  
- [x] [Episode 12 - Writing End-to-End Integration Tests](https://youtu.be/vdFRhsLcqhM)  
- [x] [Episode 13 - PostgreSQL Database Preparation](https://youtu.be/z8G9iThiiDE)  
- [x] [Episode 14 - Developing Data Layer and Repository Classes](https://youtu.be/pA8xsOmsZpI)  
- [x] [Episode 15 - Developing Application Layer and LighthouseService Component](https://youtu.be/ovhQM9L_hhQ)  
- [x] [Episode 16 - Developing Terminal-Based Client Application](https://youtu.be/Frbquqiq4Us)  
- [x] [Episode 17 - Developing MinIO-Supported PhotoStorage Component](https://youtu.be/RnCqWo9Bhs8)  
- [x] [Episode 18 - Using PhotoStorageService on Client Side](https://youtu.be/pfPqZ1SkHdM)  
- [x] [Episode 19 - Vault Integration I](https://youtu.be/CN52vnOzfT4)  
- [x] [Episode 20 - Vault Integration II](https://youtu.be/GadLQoJNfw4)  
- [x] [Episode 21 - Keeping the Client Application Running](https://youtu.be/B8VHWE8xbZU)  
- [x] [Episode 22 - Cache Integration I](https://youtu.be/24CHSgqMaB4)  
- [x] [Episode 23 - Cache Integration II](https://youtu.be/z9t0rKR5g_8)  
- [x] [Episode 24 - Redis Integration](https://youtu.be/rrRxhuo8w0E)  
- [x] [Episode 25 - Developing Redis Service Component](https://youtu.be/gRPlFqGVTCQ)  
- [x] [Episode 26 - Building Pipeline Objects](https://youtu.be/rliAGCQpGmE)  
- [x] [Episode 27 - Writing and Integrating Pipeline Behavior Components](https://youtu.be/Y1uZuewmLAs)  
- [x] [Episode 28 - Monitoring Pipeline Flow with Debugging](https://youtu.be/p1IQqc5cD6g)  
- [x] [Episode 29 - Creating Lighthouse Web API Project](https://youtu.be/WI9lOd8uVs4)  
- [x] [Episode 30 - Fixing Web API Debug and Runtime Errors](https://youtu.be/EO1IED3soQ8)  
- [x] [Episode 31 - Adding a New Feature to the Project](https://youtu.be/8rV-mUXj4YQ)  
- [x] [Episode 32 - Returning All Data! Using Paging Technique](https://youtu.be/Il3GcRWGKmA)  
- [x] [Episode 33 - Technical Debt is Unavoidable! Sonarqube Detects](https://youtu.be/kajGEmY_r8M)  
- [x] [Episode 34 - Query Data via HTTP with OData Service](https://youtu.be/FlJSnSSMMpk)  
- [x] [Episode 35 - What if we don't need every DI-registered Component?](https://youtu.be/r34uuX8ycCQ)  
- [x] [Episode 36 - Introduction to Keycloak](https://youtu.be/rKk1iRMmXME)  
- [x] [Episode 37 - Keycloak-Based Authorization in Web API Project](https://youtu.be/nJr1yM_Em7s)  
- [x] [Episode 38 - Sending Logs to Elasticsearch](https://youtu.be/rP4i3yqtAP8)  
- [x] [Episode 39 - Keeping Vault Info on Cache *(We Opened a Can of Worms)*](https://youtu.be/t6nnL11wOnI)  
- [x] [Episode 40 - Better Error Management *(Result Pattern Refactoring)*](https://youtu.be/2GA8q-jjNGI)  
- [x] [Episode 41 - Adapting Graylog for Incoming Comments](https://youtu.be/OmaopxCVLF8)  
- [x] [Episode 42 - Current State and Returning to Store with PhotoController](https://youtu.be/Ng4Yuhqruyo)  
- [x] [Episode 43 - SAGA Pattern for Distributed Transaction Management During Photo Upload](https://youtu.be/TA1CF6C4iyA)  
- [x] [Episode 44 - Adapting SAGA Pattern to Photo Upload Process](https://youtu.be/i1iln8Ym96U)  
- [x] [Episode 45 - SAGA Pattern Tests During Photo Upload](https://youtu.be/Q2SsV1HGa8A)  
- [x] [Episode 46 - Preparations for Event-Based System](https://youtu.be/2Kdka9T9Gmo)  
- [x] [Episode 47 - Developing Event Publisher Component for RabbitMQ](https://youtu.be/XglgWP3w37M)  
- [x] [Episode 48 - Will Events Reach RabbitMQ?](https://youtu.be/Ibfz3ScqgOc)  
- [x] [Episode 49 - Where Are RabbitMQ Messages? (Queue Creation & Listening)](https://youtu.be/NzYOm4NJT5s)  
- [x] [Episode 50 - First Steps for Razor-Based Backoffice Application](https://youtu.be/h1PFUQ20g90)  
- [x] [Episode 51 - Creating Page to Add a New Lighthouse](https://youtu.be/CpPu6jPQW2c)  
- [x] [Episode 52 - Creating Lighthouse Listing Page](https://youtu.be/edF1Cg-cnjs)  
- [x] [Episode 53 - Application Layer Updates to Fetch Country Info](https://youtu.be/mBG8Wj74h10)  
- [x] [Episode 54 - Binding Select Control in Razor Page to Service Layer](https://youtu.be/oGSCAO27UwI)  
- [x] [Episode 55 - Should We Call the Service Every Time for Country List?](https://youtu.be/WM1tk8TiTNw)  
- [x] [Episode 56 - Successfully Created New Lighthouse in Razor Page. What About Photo?](https://youtu.be/CjS6Wrq2lLg)  
- [x] [Episode 57 - Razor-Side Updates for Saving and Validating Photos](https://youtu.be/7JOnD7Q0F7c)  
- [x] [Episode 58 - Finally Managed Photo Upload from Backoffice Application!](https://youtu.be/UYExTeffZws)  
- [x] [Episode 59 - Creating Worker Service Project to Consume Events](https://youtu.be/eERBKN6ZZ9Y)  
- [x] [Episode 60 - Adding RabbitMQ Integration to Worker Service](https://youtu.be/Ymc7_OpvB_Y)  
- [ ] [Episode 61 - Fix Code Errors and Make Worker Service Functional]  
- [ ] [Episode 62 - Handler Count Will Increase. Remove Switch Cases!]

---

## Sonarqube

A static code analysis tool, **Sonarqube**, is used to prevent technical debt. In a product launched locally via **docker-compose**, the following steps are sufficient to start scanning:

```bash
# Install the scanning tool for Dotnet
dotnet tool install --global dotnet-sonarscanner

# In the solution folder, run:
# Token information will vary according to your setup
dotnet sonarscanner begin /k:"Project-Ligthouse-Social" /d:sonar.host.url="http://localhost:9000"  /d:sonar.token="your_generated_token"

dotnet build

dotnet sonarscanner end /d:sonar.token="your_generated_token"
```

Periodic Sonarqube scans can measure the project's code quality compliance. It is recommended to monitor.

## Dockerize Steps for JudgeDredd Service

```bash
# In docker-compose, declare a service for the JudgeDredd folder
# Then start build in the folder containing docker-compose
docker-compose build

# Afterwards, start the services
docker compose up -d

# Requests can be sent to JudgeDredd service running on port 5005 for testing
```

---

## Current Vault Information

Path: **ProjectLighthouseSocial-Dev**

```json
{
  "DbConnStr": "Host=localhost;Port=5432;Database=lighthousedb;Username=johndoe;Password=somew0rds",
  "KeycloakAudience": "account",
  "KeycloakAuthority": "http://localhost:8400/",
  "KeycloakClientId": "lighthouse-service-client",
  "KeycloakClientSecret": "Lupgay1UcpJA7vRDOr7MsrBJN5B7bJoN",
  "KeycloakClockSkew": "5",
  "KeycloakRealm": "ProjectLighthouseSocialRealm",
  "KeycloakRequireHttpsMetadata": "false",
  "KeycloakValidateAudience": "true",
  "KeycloakValidateIssuer": "true",
  "KeycloakValidateIssuerSigningKey": "true",
  "KeycloakValidateLifetime": "true",
  "MinIOAccessKey": "admin",
  "MinIOSecretKey": "password",
  "RabbitMQUser": "admin",
  "RabbitMQPassword": "admin1234"
}
```

## If There Are Issues with Redis Cache Values

For example, if a new version of a secret defined in Vault is released. If the cache is active, the Vault values need to be reloaded. Normally, this can be done by calling the Cache Invalidation method, but just in case, it is also possible to proceed by deleting the relevant key via Docker. For instance, if we want to delete Vault settings, we can use the following command:

```bash
docker exec -it plh-redis redis-cli del vault:keycloak_settings
```

## Redis Cache Tests

During Redis cache testing, we may want to enter the Docker container to check keys or delete them manually. Below are practical commands we can use for this purpose.

```bash
# Access the Redis container
docker exec -it plh-redis sh

# Run Redis CLI
redis-cli

# List all keys
keys *

# Add, list, delete Key-Value
set Environment "Development"
get Environment

set user:Service "{\"user\":\"apiAccount\"}" EX 3600   # 1 hour expiration time
get user:Service
del user:Service

# Check if a key exists
exists user:Service

# Check the remaining lifetime of a key
TTL user:Service
```

## Tasks and Questions

- [ ] **Caching in Comment Moderation:** The **JudgeDredd** service sends a text content to the **OpenAI Moderation API** for review. If the same comment is repeatedly sent as a type of attack, the **OpenAI** service might be called numerous times. For identical incoming requests, previously received responses _(e.g., already flagged=true)_ can be cached for a certain period and returned immediately.
  - [ ] Multiple submissions of the same request could also indicate an attack. A mechanism can be developed to detect this, take precautions, and issue warnings.
- [x] **Repository Contracts:** Is it correct for repository contracts to reside in the **Domain** layer? Or, if they are to reside there, which behaviors should the contracts include? Should contracts only covering **Create, Retrieve, Update, Delete** functionalities and directly related to the Domain be placed here, while contracts containing **Business Rules** be placed elsewhere?
- [x] **Access to Handler Components:** The core layer of the project is the **Application** library. Considering the contracts _(Contracts folder)_ we expose to UI, API, Terminal clients from this layer, should **Handler** classes be closed to the outside?
- [ ] **Unit of Work:** The **HandleAsync** methods in handler components operate a specific workflow. Should this workflow pattern, including **DTO** validations, different business rules, transactions, logging, etc., be collected in a higher-level structure? _(For example, within a unit of work)_
- [x] **Photo Storage:** The part that will occupy the most physical space and grow fastest in the project is lighthouse photos. Can a local container be used as the storage location? For example, **AWS S3 API** compatible [MinIO](https://min.io/docs/minio/container/index.html) or another equivalent storage solution.
- [x] **Persistence:** Entities in the project domain are neither numerous nor complex. Data can be stored in a schema-based database system _(e.g., **PostgreSQL**)_. Initially, we can proceed with a **Database First** model instead of **Entity Framework Core** and **Code-First**, using **Dapper** for access.
- [ ] **Service Health Check/Discovery:** The number of external services like **JudgeDredd** will increase. As the system grows, many instruments like **PostgreSQL Server**, **Storage Service**, **RabbitMQ**, **Keycloak**, etc., will also be included in the solution. Checking whether these services are active and managing ports or IPs that vary by environment will be needed. [HashiCorp Consul](https://developer.hashicorp.com/consul/docs/intro) can be used for this purpose.
- [ ] **Membership Management:** A hybrid model can be preferred for authenticating subscribers. **Identity Provider** can be **[Keycloak](https://www.keycloak.org/)**, and user profile data can be stored in a database. Our project does not need to handle authentication details directly.
- [x] **Secret Keys:** The project will include sensitive information like database addresses, API keys, and secrets. These should be stored securely and resolved at runtime. A Vault system can be used for managing secrets. Options include **[Hashicorp Vault](https://developer.hashicorp.com/vault)** or **[Localstack](https://github.com/localstack/localstack)**.
- [ ] **CLI Tool:** A terminal tool can be developed for end users who are familiar with CLI _(Command Line Interface)_ usage.
- [ ] **Public API:** Can the project provide a publicly accessible API service? For example, lighthouse information could be exposed externally. This would be a service outside of the standard web interface, useful for other applications.
- [ ] **Reporting:** What kind of reports can the project offer? For instance, lighthouses with the most popular photos, users with the best photos, countries with the most visited lighthouses, active lighthouses list, etc. What kind of application could serve as a basis for these reports?
- [ ] **Integration Tests:** As the number of services and components grows, how can integration tests be improved strategically? For example, integration tests can be written for cases involving **JudgeDredd** or **PhotoStorage** components, using a TestContainer at runtime.
- [ ] **Recommendation System:** A recommendation system can be added to suggest lighthouses to users based on certain criteria or display lighthouses they may want to visit.

## Checklist

At the end of the project and video tutorial series, we should be able to answer the following questions:

- [x] Were the basic features of **C#** covered?
- [x] Were **OOP** _(Object Oriented Programming)_ principles applied?
- [x] Were **SOLID** principles implemented?
- [ ] Was the code cleared of **technical debt**?
- [ ] Did the project evolve into a specific software architecture style?
- [x] Was at least one **REST**-based Web API used in the project?
- [ ] Was a **gRPC**-based service used in the project?
- [x] Was a **Razor**-based Web application developed?
- [ ] Were services written in different programming languages used?
- [ ] Was a distributed system architecture established?
- [ ] If a distributed system architecture was established, were necessary **resilience** measures taken?
- [ ] For the distributed system architecture, were monitoring, logging, alert mechanisms, etc., implemented?
