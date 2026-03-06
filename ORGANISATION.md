# Organisation
Ich habe festgestellt, dass sich demokratische Strukturen sehr gut in GitHub abbilden lassen.
Die unteren Grafiken zeigen, wie sich das Zusammenspiel aus Gewerkschaft, Mitgliedern und Öffentlichkeit in einem OpenSource Projekt abbilden lassen. Natürlich wäre es sinnvoll, hier weitere Unterprojekte anzulegen, die gleichen Mechanismen folgen, sodass es thematische GitHub-Projekte gibt. CyberVK könnte Templates bereitstellen, wenn Projekte im CyberVK beschlossen, und Arbeitsgruppen festgelegt sind. So können Verantwortliche in ihrem Projekt frei agieren und sind trotzdem der Satzung verpflichtet. Wer nicht warten möchte, kann natürlich immer forken und diee Bürokratie wird später erledigt, oder gar nicht. So gibt es lose und innergewerkschaftliche Zusammenarbeit, die nicht ausbremst, jedem alle Freiheiten gewährt, aber den Konsens im CyberVK trotzdem vereinen kann.

## Anonymität
Da Gewerkschaftsarbeit nicht immer gern gesehen ist, lässt sich Anonymität herstellen, indem der eigene public key bei der Gewerkschaft registriert werden kann. Somit ist mit minimalen personenbeziehbaren Daten sichergestellt, dass das Wahlrecht sichergestellt ist, alle rechtlichen Rahmenbedingungen an gewerkschaltliche Arbeit eingehalten werden und niemand außen vor gelassen wird.

## CyberJAV und CyberSBV und vielleicht auch CyberSRV?
Typischerweise hat innerbetriebliche Mitbestimmung weitere Aspekte: Es gibt die JAV, die sich um Belange der Azubis und Studierenden und jungen Menschen kümmert. Dann gibt es die SBV, die das Gleiche für schwerbehinderte Menschen in Betrieben tut. Im Digitalen Raum könnten solche Menschen sich darum kümmern, dass Projekte in einfacher Sprache, einfacher Nutzbarkeit, für Menschen mit schlechter Sicht oder schlechtem Gehör zugänglich bleiben. Vielleicht braucht es gerade im Digitalen auch eine CyberSRV (**SeniorInnen- und RentnerInnenvertretung**). Das wäre schön, um auch alten Menschen, die noch nicht so digital aufgewachsen sind, Zugang und Teilhabe zu ermöglichen.

Ich denke, das wäre auch für einen CyberVK wichtig, um nicht den Fokus auf diese Menschen zu verlieren.

```mermaid
flowchart TB

  PUB["Öffentlichkeit\n(read access)"]
  FORK["Fork des Repositories\n(eigene Vorschläge entwickeln)"]
  PRPUB["Pull Request aus Fork"]

  REPO["Offizielles VK GitHub Repository"]

  subgraph MEMBERS["Gewerkschaftsmitglieder"]
    VOTE["Digitale Wahl\nMaintainer wählen"]
    CAND["Digitale Kandidatur\nAgenda / Ziele / Steckbrief"]
  end

  subgraph VK["VK Maintainer Team"]
    MAINT["Maintainer\n(gewählte Vertrauensleute)"]
    AGENDA["Agenda & Projekte\n(GitHub Projects)"]
    ISSUES["Issues & Discussions\n(Themenverwaltung)"]
    PRS["Pull Requests reviewen"]
  end

  subgraph VKL["VKL Leitung"]
    VKL_ELECT["Maintainer wählen VKL"]
    VKL_NODE["VKL\nkoordiniert Agenda & Meetings"]
  end

  subgraph UNION["Gewerkschaft"]
    BALLOT["Digitaler Wahlschein"]
    RULES["Satzung / Code of Conduct"]
    OMB["Ombudsstelle\nSatzungskonformität"]
  end

  PUB --> FORK
  FORK --> PRPUB
  PRPUB --> PRS

  PUB -->|"liest"| REPO

  CAND --> VOTE
  BALLOT --> VOTE
  VOTE --> MAINT

  MAINT --> PRS
  MAINT --> ISSUES
  MAINT --> AGENDA

  MAINT --> VKL_ELECT
  VKL_ELECT --> VKL_NODE

  VKL_NODE --> AGENDA

  RULES --> REPO
  OMB --> PRS

  REPO --> UNION
```


# Pull-Request
```mermaid
flowchart LR

  IDEA["Idee / Thema"]

  PUBLIC["Öffentlichkeit"]
  MEMBER["Mitglied"]

  FORK["Fork des Repositories"]

  ISSUE["Issue<br/>Themenvorschlag"]

  DISC["Discussion<br/>Debatte"]

  PR["Pull Request"]

  CHECK["Automatische Checks<br/>Commit Signing<br/>Satzung / CoC"]

  REVIEW["VK Review<br/>(Maintainer)"]

  DECISION{"VK Entscheidung"}

  MERGE["Merge<br/>Beschluss"]

  CHANGE["Überarbeitung"]

  CLOSE["Closed"]

  RELEASE["Release / Protokoll"]

  UNION["Rückkopplung<br/>Gewerkschaft"]

  IDEA --> PUBLIC
  IDEA --> MEMBER

  PUBLIC --> FORK
  FORK --> PR

  MEMBER --> ISSUE
  ISSUE --> DISC
  DISC --> PR

  PR --> CHECK
  CHECK --> REVIEW

  REVIEW --> DECISION

  DECISION -->|angenommen| MERGE
  DECISION -->|Überarbeiten| CHANGE
  DECISION -->|abgelehnt| CLOSE

  CHANGE --> PR

  MERGE --> RELEASE
  RELEASE --> UNION
``
