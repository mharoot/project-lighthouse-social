# Project Lighthouse Social

An end-to-end web application built with **C# and .NET**, designed as a social platform where users can share, comment on, and rate photos of lighthouses from around the world.  
_(You can follow the full development process in the [YouTube playlist](https://www.youtube.com/playlist?list=PLY-17mI_rla6Kt-Ri6nP1pE62ZyE-6wjS).)_

A primary goal of this project is to explore foundational software engineering concepts—such as abstraction, dependency inversion, and responsibility allocation—while gradually evolving the codebase toward a consistent architectural style.

---

## Current Task List *(as of 10.18.2025)*

### Domain Layer Improvements
- [ ] **EntityBase – Audit Fields:** Add `CreatedAt`, `ModifiedAt`, `DeletedAt` fields to `EntityBase`. *(EntityBase.cs:6)*

### Application Layer Improvements
- [ ] **AddCommentHandler – Component Configuration:** Improve component configuration. *(AddCommentHandler.cs:22)*
- [ ] **CreateLighthouseHandler – User ID Management:** Replace `Guid.Empty` with authentication context. *(CreateLighthouseHandler.cs:29,47,65,87)*
- [ ] **CreateUserHandler – User ID Management:** Replace `Guid.Empty` with authentication context. *(CreateUserHandler.cs:25,41,58,76)*
- [ ] **LighthouseDtoValidator – Primary Key Design:** Review and refine primary key approach. *(LighthouseDtoValidator.cs:17)*

### Data Layer Improvements
- [ ] **PhotoRepository – Reflection ID Assignment:** Replace reflection-based ID assignment with a clean solution. *(PhotoRepository.cs:151)*
- [ ] **CachedCountryDataReader – Mapper Usage:** Add mapping layer between `Country` and `CountryDto`. *(CachedCountryDataReader.cs:74)*

### Infrastructure Layer Improvements
- [ ] **ExternalCommentAuditor – Runtime Service Discovery:** Resolve service address dynamically at runtime. *(ExternalCommentAuditor.cs:15)*
- [ ] **ExternalCommentAuditor – Consul Integration:** Integrate HashiCorp Consul for service discovery. *(ExternalCommentAuditor.cs:16)*
- [ ] **CachedConfigurationService – Cache Invalidation:** Improve cache invalidation logic. *(CachedConfigurationService.cs:242)*

### Backoffice Improvements
- [ ] **Lighthouse Create – Unknown Fields:** Populate CameraType, Resolution, Lens, and UserId with real values. *(Create.cshtml.cs:114)*
- [ ] **Lighthouse Delete – Photo Relationship:** Correct deletion of primary photos. *(List.cshtml.cs:70)*
- [ ] **Photo Deletion Error Handling:** Notify user if lighthouse deletion succeeds but photo deletion fails. *(List.cshtml.cs:75)*

### Photo Management Improvements
- [ ] **IsPrimary Business Rule:** Enforce a single primary photo per lighthouse.
- [ ] **Photo Validation:** Validate that only one primary photo exists.
- [ ] **Backoffice Photo Gallery:** Provide a gallery to view all photos and change the primary photo.

### Worker Service Improvements
- [ ] **Event Handler – Switch Case:** Replace switch-case with a more flexible structure. *(RabbitMqEventConsumerService.cs:122)*
- [ ] **PhotoUploadedEventHandler – Missing Logic:** Implement actual business logic (currently logs only). *(PhotoUploadedEventHandler.cs:23)*

---

## Project Overview

A social platform for lighthouse enthusiasts around the world.

### Features
- Upload and share **photos** of lighthouses.
- Access **detailed information** about global lighthouses.
- Leave **comments** and **ratings** on photos.

### Goals
- Explore C# and .NET via a real project.
- Continuously refactor for cleaner architecture.
- Apply essential software engineering principles.
- Understand the development needs of scalable systems.

### Target Audience

**Minimum Profile**
- Basic C# and OOP knowledge  
- Awareness of clean code standards  
- Willing to research and learn while following the project  

**Ideal Profile**
- Questions and understands SOLID principles  
- Familiar with technical debt management  
- Experience with distributed systems and Docker  
- Understands service architectures beyond simple Web APIs  

---

## Challenges

- Managing and storing user-uploaded photos  
- Moderating user comments  
- Verifying authenticity of user submissions  
- Using AI/ML for categorization and tagging  
- Handling high-volume uploads efficiently  
- Maintaining resilience in distributed systems  

---

## Content Plan

All project sessions from 00–62 are available in the YouTube playlist:  
https://www.youtube.com/playlist?list=PLY-17mI_rla6Kt-Ri6nP1pE62ZyE-6wjS

---

## Sonarqube Setup

```bash
dotnet tool install --global dotnet-sonarscanner

dotnet sonarscanner begin /k:"Project-Ligthouse-Social" /d:sonar.host.url="http://localhost:9000" /d:sonar.token="your_generated_token"

dotnet build

dotnet sonarscanner end /d:sonar.token="your_generated_token"
