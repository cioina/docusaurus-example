---
sidebar_position: 1
description: Create your first mapper with Mapperly.
---

# Create your first mapper

Create a mapper declaration as a partial class
and apply the `Riok.Mapperly.Abstractions.MapperAttribute` attribute.
Mapperly generates mapping method implementations for the defined mapping methods in the mapper.

```csharp title="Mapper declaration"
[Mapper]
public partial class CarMapper
{
    public partial CarDto CarToCarDto(Car car);
}
```

```csharp title="Mapper usage"
var mapper = new CarMapper();
var car = new Car { NumberOfSeats = 10, ... };
var dto = mapper.CarToCarDto(car);
dto.NumberOfSeats.ShouldBe(10);
```
## Mermaid Examples

### Example 1

```mermaid
block-beta
columns 1
  db(("DB"))
  blockArrowId6<["&nbsp;&nbsp;&nbsp;"]>(down)
  block:ID
    A
    B["A wide one in the middle"]
    C
  end
  space
  D
  ID --> D
  C --> D
  style B fill:#969,stroke:#333,stroke-width:4px
```

### Example 2

```mermaid
block-beta
  columns 3
  a:3
  block:group1:2
    columns 2
    h i j k
  end
  g
  block:group2:3
    %% columns auto (default)
    l m n o p q r
  end  
```

### Example 3

```mermaid
block-beta
  id1[/"This is the text in the box"/]
  id2["This is the text in the box"]
  A[/"Christmas"]
  B["Go shopping"/]
```

### Example 4

```mermaid
block-beta
  blockArrowId<["Label"]>(right)
  blockArrowId2<["Label"]>(left)
  blockArrowId3<["Label"]>(up)
  blockArrowId4<["Label"]>(down)
  blockArrowId5<["Label"]>(x)
  blockArrowId6<["Label"]>(y)
  blockArrowId6<["Label"]>(x, down)
```

### Example 5

```mermaid
block-beta
  columns 3
  Start(("Start")) space:2
  down<[" "]>(down) space:2
  Decision("Make Decision") right<["Yes"]>(right) Process1["Process A"]
  downAgain<["No"]>(down) space r3<["Done"]>(down)
  Process2["Process B"] r2<["Done"]>(right) End(("End"))

  style Start fill:#969;
  style End fill:#696;
```

### Example 6

```mermaid
graph LR
  B("$$\begin{array} {lcl} L(p,w_i) &=& \dfrac{1}{N}\Sigma_{i=1}^N(\underbrace{f_r(x_2 \rightarrow x_1 \rightarrow x_0)G(x_1 \longleftrightarrow x_2)f_r(x_3 \rightarrow x_2 \rightarrow x_1)}_{sample\, radiance\,evaluation\, in\, stage2} \\\\\\ &=& \prod_{i=3}^{k-1}(\underbrace{\dfrac{f_r(x_{i+1} \rightarrow x_i \rightarrow x_{i-1})G(x_i \longleftrightarrow x_{i-1})}{p_a(x_{i-1})}}_{stored\,in\,vertex\, during\,light\, path\, tracing\, in\, stage1})\dfrac{G(x_k \longleftrightarrow x_{k-1})L_e(x_k \rightarrow x_{k-1})}{p_a(x_{k-1})p_a(x_k)}) \end{array}$$")
  A-->B
```

### Example 7

```mermaid
graph LR
  B("$$\sqrt{\frac{\pi(1-\pi)}{n}}$$")
  A-->B
```
## Invalid Diagrams

Those errors should not crash the whole page

### Invalid type

```bash
badType
    participant Alice
    participant Bob
```

### Invalid content

```bash
sequenceDiagram
    badInstruction Alice
    participant Bob
```

## Sequence Diagram

```mermaid
sequenceDiagram
    participant Alice
    participant Bob
    Alice->>John: Hello John, how are you?
    loop Health check
        John->>John: Fight against hypochondria
    end
    Note right of John: Rational thoughts <br/>prevail!
    John-->>Alice: Great!
    John->>Bob: How about you?
    Bob-->>John: Jolly good!
```

## Sequence Diagram (forest theme directive)

It is possible to override default config locally with Mermaid text directives such as:

```bash
%%{init: { "theme": "forest" } }%%
```

```mermaid
%%{init: { "theme": "forest" } }%%

sequenceDiagram
    participant Alice
    participant Bob
    Alice->>John: Hello John, how are you?
    loop Health check
        John->>John: Fight against hypochondria
    end
    Note right of John: Rational thoughts <br/>prevail!
    John-->>Alice: Great!
    John->>Bob: How about you?
    Bob-->>John: Jolly good!
```

## Gantt Chart

```mermaid
gantt
dateFormat  YYYY-MM-DD
title Adding GANTT diagram to mermaid
excludes weekdays 2014-01-10

section A section
Completed task            :done,    des1, 2014-01-06,2014-01-08
Active task               :active,  des2, 2014-01-09, 3d
Future task               :         des3, after des2, 5d
Future task2               :         des4, after des3, 5d
```

## Flow Chart

```mermaid
flowchart TD
    A[Start] --> B{Is it?}
    B -->|Yes| C[OK]
    C --> D[Rethink]
    D --> B
    B ---->|No| E[End]
```

### With Markdown:

```mermaid
flowchart LR
    markdown["`This **is** _Markdown_`"]
    newLines["`Line1
    Line 2
    Line 3`"]
    markdown --> newLines
```

## Class Diagram

```mermaid
 classDiagram
      Animal <|-- Duck
      Animal <|-- Fish
      Animal <|-- Zebra
      Animal : +int age
      Animal : +String gender
      Animal: +isMammal()
      Animal: +mate()
      class Duck{
          +String beakColor
          +swim()
          +quack()
      }
      class Fish{
          -int sizeInFeet
          -canEat()
      }
      class Zebra{
          +bool is_wild
          +run()
      }
```

## State Diagram

```mermaid
stateDiagram-v2
    [*] --> Active

    state Active {
        [*] --> NumLockOff
        NumLockOff --> NumLockOn : EvNumLockPressed
        NumLockOn --> NumLockOff : EvNumLockPressed
        --
        [*] --> CapsLockOff
        CapsLockOff --> CapsLockOn : EvCapsLockPressed
        CapsLockOn --> CapsLockOff : EvCapsLockPressed
        --
        [*] --> ScrollLockOff
        ScrollLockOff --> ScrollLockOn : EvScrollLockPressed
        ScrollLockOn --> ScrollLockOff : EvScrollLockPressed
    }
```

## Entity Relationship Diagram

```mermaid
erDiagram
    CAR ||--o{ NAMED-DRIVER : allows
    CAR {
        string registrationNumber
        string make
        string model
    }
    PERSON ||--o{ NAMED-DRIVER : is
    PERSON {
        string firstName
        string lastName
        int age
    }
```

## User Journey

```mermaid
journey
    title My working day
    section Go to work
      Make tea: 5: Me
      Go upstairs: 3: Me
      Do work: 1: Me, Cat
    section Go home
      Go downstairs: 5: Me
      Sit down: 5: Me
```

:::note

If there's too much space above it's due to a [Mermaid bug](https://github.com/mermaid-js/mermaid/issues/3501)

:::

## Pie Chart

```mermaid
pie showData
    title Key elements in Product X
    "Calcium" : 42.96
    "Potassium" : 50.05
    "Magnesium" : 10.01
    "Iron" :  5
```

## Requirement Diagram

```mermaid
    requirementDiagram

    requirement test_req {
    id: 1
    text: the test text.
    risk: high
    verifymethod: test
    }

    functionalRequirement test_req2 {
    id: 1.1
    text: the second test text.
    risk: low
    verifymethod: inspection
    }

    performanceRequirement test_req3 {
    id: 1.2
    text: the third test text.
    risk: medium
    verifymethod: demonstration
    }

    interfaceRequirement test_req4 {
    id: 1.2.1
    text: the fourth test text.
    risk: medium
    verifymethod: analysis
    }

    physicalRequirement test_req5 {
    id: 1.2.2
    text: the fifth test text.
    risk: medium
    verifymethod: analysis
    }

    designConstraint test_req6 {
    id: 1.2.3
    text: the sixth test text.
    risk: medium
    verifymethod: analysis
    }

    element test_entity {
    type: simulation
    }

    element test_entity2 {
    type: word doc
    docRef: reqs/test_entity
    }

    element test_entity3 {
    type: "test suite"
    docRef: github.com/all_the_tests
    }


    test_entity - satisfies -> test_req2
    test_req - traces -> test_req2
    test_req - contains -> test_req3
    test_req3 - contains -> test_req4
    test_req4 - derives -> test_req5
    test_req5 - refines -> test_req6
    test_entity3 - verifies -> test_req5
    test_req <- copies - test_entity2
```

## Gitgraph (Git) Diagram

```mermaid
%%{init: { 'logLevel': 'debug', 'theme': 'base' } }%%
      gitGraph
        commit
        branch hotfix
        checkout hotfix
        commit
        branch develop
        checkout develop
        commit id:"ash" tag:"abc"
        branch featureB
        checkout featureB
        commit type:HIGHLIGHT
        checkout main
        checkout hotfix
        commit type:NORMAL
        checkout develop
        commit type:REVERSE
        checkout featureB
        commit
        checkout main
        merge hotfix
        checkout featureB
        commit
        checkout develop
        branch featureA
        commit
        checkout develop
        merge hotfix
        checkout featureA
        commit
        checkout featureB
        commit
        checkout develop
        merge featureA
        branch release
        checkout release
        commit
        checkout main
        commit
        checkout release
        merge main
        checkout develop
        merge release
```

## Mermaid in tabs

The following mermaid diagram is shown:

```mermaid
graph LR
  a ---> c(10)
  b ---> c(10)
```

## Mindmap

```mermaid
mindmap
  root((conda-forge))
    (Repos)
        (Package building)
            [*-feedstock]
            [staged-recipes]
            [cdt-builds]
            [msys2-recipes]
        (Maintenance)
            [admin-requests]
            [repodata-patches]
        (Configuration)
            [.github]
            [.cirun]
            [conda-forge-pinning]
            [conda-forge-ci-setup]
            [docker-images]
            [conda-smithy]
        (Automations)
            [admin-migrations]
            [artifact-validation]
            [regro/cf-scripts]
            [conda-forge-webservices]
            [regro/cf-graph-countyfair]
            [regro/libcfgraph + regro/libcflib]
            [feedstock-outputs]
        (Communications)
            [conda-forge.github.io]
            [blog]
            [status]
            [by-the-numbers]
            [conda-forge-status-monitor]
            [feedstocks]
    (Bots & apps)
        [conda-forge-admin]
        [conda-forge-bot]
        [conda-forge-coordinator]
        [conda-forge-daemon]
        [conda-forge-linter]
        [conda-forge-manager]
        [conda-forge-status]
        [regro-cf-autotick-bot]
        [conda-forge-curator]
        [conda-forge-webservices]
    (Delivery)
        [anaconda.org]
        [ghcr.io]
        [quay.io]
    (Installers)
        Miniforge
        Mambaforge
    (CI for builds)
        Azure Pipelines
        Travis CI
        cirun.io
    (Infra)
        Heroku
        Github Actions
        Circle CI
```

## Quadrant Chart

```mermaid
quadrantChart
    title Reach and engagement of campaigns
    x-axis Low Reach --> High Reach
    y-axis Low Engagement --> High Engagement
    quadrant-1 We should expand
    quadrant-2 Need to promote
    quadrant-3 Re-evaluate
    quadrant-4 May be improved
    Campaign A: [0.3, 0.6]
    Campaign B: [0.45, 0.23]
    Campaign C: [0.57, 0.69]
    Campaign D: [0.78, 0.34]
    Campaign E: [0.40, 0.34]
    Campaign F: [0.35, 0.78]
```

## Architecture Diagram

- See https://mermaid.js.org/syntax/architecture
- See https://github.com/facebook/docusaurus/discussions/10508

```mermaid
architecture-beta
    group api(cloud)[API]

    service db(database)[Database] in api
    service disk1(disk)[Storage] in api
    service disk2(disk)[Storage] in api
    service server(server)[Server] in api

    db:L -- R:server
    disk1:T -- B:server
    disk2:T -- B:db
```

## ELK Styling

Mermaid provides an [ELK layout](https://mermaid.js.org/syntax/entityRelationshipDiagram.html#layout)

### Dagre

This is a "classical" Mermaid diagram, using the default Dagre layout.

```mermaid
erDiagram

  COMPANY ||--o{ DEPARTMENT : has
  COMPANY ||--o{ PROJECT : undertakes
  COMPANY ||--o{ LOCATION : operates_in
  COMPANY ||--o{ CLIENT : serves

  DEPARTMENT ||--o{ EMPLOYEE : employs
  DEPARTMENT ||--o{ PROJECT : manages
  DEPARTMENT ||--o{ BUDGET : allocated

  EMPLOYEE }o--o{ PROJECT : works_on
  EMPLOYEE ||--|| ADDRESS : lives_at
  EMPLOYEE }o--o{ SKILL : has
  EMPLOYEE ||--o{ DEPENDENT : supports

  PROJECT ||--o{ CLIENT : for
  PROJECT ||--o{ TASK : contains

```

### ELK er diagram layout

This ER diagram should look different, using the ELK layout.

```mermaid
---
config:
  layout: elk
---
erDiagram

  COMPANY ||--o{ DEPARTMENT : has
  COMPANY ||--o{ PROJECT : undertakes
  COMPANY ||--o{ LOCATION : operates_in
  COMPANY ||--o{ CLIENT : serves

  DEPARTMENT ||--o{ EMPLOYEE : employs
  DEPARTMENT ||--o{ PROJECT : manages
  DEPARTMENT ||--o{ BUDGET : allocated

  EMPLOYEE }o--o{ PROJECT : works_on
  EMPLOYEE ||--|| ADDRESS : lives_at
  EMPLOYEE }o--o{ SKILL : has
  EMPLOYEE ||--o{ DEPENDENT : supports

  PROJECT ||--o{ CLIENT : for
  PROJECT ||--o{ TASK : contains

```

Mermaid also provides a way of setting config parameters using a directive `%%{init:{"layout":"elk"}}%%`

```mermaid
%%{init:{"layout":"elk"}}%%
erDiagram

  COMPANY ||--o{ DEPARTMENT : has
  COMPANY ||--o{ PROJECT : undertakes
  COMPANY ||--o{ LOCATION : operates_in
  COMPANY ||--o{ CLIENT : serves

  DEPARTMENT ||--o{ EMPLOYEE : employs
  DEPARTMENT ||--o{ PROJECT : manages
  DEPARTMENT ||--o{ BUDGET : allocated

  EMPLOYEE }o--o{ PROJECT : works_on
  EMPLOYEE ||--|| ADDRESS : lives_at
  EMPLOYEE }o--o{ SKILL : has
  EMPLOYEE ||--o{ DEPENDENT : supports

  PROJECT ||--o{ CLIENT : for
  PROJECT ||--o{ TASK : contains

```
