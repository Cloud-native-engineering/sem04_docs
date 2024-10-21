# Semesterarbeit 04 - Can Kubernetes with Distributed Storage Replace a Home NAS?

[![GitHub Pages - Docs](https://github.com/Cloud-native-engineering/sem04_docs/actions/workflows/pages/pages-build-deployment/badge.svg)](https://github.com/Cloud-native-engineering/sem04_docs/actions/workflows/pages/pages-build-deployment)

Im Zeitalter der digitalen Transformation suchen immer mehr private Haushalte nach zuverlässigen und effizienten Lösungen zur Speicherung und Verwaltung ihrer Daten. Ein zentraler Aspekt dabei ist die Datenhoheit und der Speicherort der eigenen Daten, welche beim Enduser liegen und nicht bei einem Cloud-Provider wie OneDrive von Microsoft oder Google Drive von Google. Traditionelle NAS-Systeme (Network Attached Storage) sind zwar weit verbreitet, stossen jedoch zunehmend an ihre Grenzen in Bezug auf Skalierbarkeit, Flexibilität und Verwaltung. Kubernetes (K8s) hat sich als leistungsstarke Plattform zur Orchestrierung von containerisierten Anwendungen etabliert, aber kann K8s mit verteiltem Speicher eine tragfähige Alternative zu einem herkömmlichen NAS für den Heimgebrauch darstellen? Diese Semesterarbeit zielt darauf ab, die Machbarkeit und Vorteile eines solchen Setups zu untersuchen. Durch die Implementierung und den Vergleich von Kubernetes mit verteiltem Speicher und einem traditionellen NAS sollen Aspekte wie Leistung, Benutzerfreundlichkeit, Kosten und Skalierbarkeit bewertet werden. Ziel ist es, zu bestimmen, ob K8s mit verteiltem Speicher eine praktikable und vorteilhafte Lösung für die private Datenspeicherung und -verwaltung bieten kann.

```mermaid
mindmap
  root((K8s with Distributed Storage vs. Home NAS))

    A[K8s with Distributed Storage]
      A1[Advantages]
        A1a["Highly scalable"]
        A1b["Automated failover"]
        A1c["Supports dynamic workloads"]
      A2[Challenges]
        A2a["Complex to set up"]
        A2b["Overkill for small environments"]
        A2c["Requires expertise in Kubernetes and storage solutions"]

    B[Home NAS]
      B1[Advantages]
        B1a["Easy to set up and use"]
        B1b["Centralized, simple file sharing"]
        B1c["Cost-effective for small storage needs"]
      B2[Challenges]
        B2a["Limited scalability"]
        B2b["Less dynamic"]
        B2c["Single point of failure without RAID"]

    C[Key Considerations]
      C1["Storage Needs"]
        C1a["Home NAS: Simple, centralized storage"]
        C1b["K8s: Distributed, scalable storage"]
      C2["Complexity vs. Simplicity"]
        C2a["Home NAS: Low complexity"]
        C2b["K8s: High complexity"]
      C3["Cost and Maintenance"]
        C3a["Home NAS: Low upfront cost, easy maintenance"]
        C3b["K8s: Higher cost, requires maintenance expertise"]

    D[Conclusion]
      D1["Home NAS: Better for basic, small-scale storage needs"]
      D2["K8s: Suitable for large, dynamic environments but overkill for home use"]
```

## Inhaltsverzeichnis

[1. Einleitung](index.md)

[2. Projektorganisation](docs/02_projektorganisation/index.md)

[2.1 Projektmethode](docs/02_projektorganisation/projektmethode.md)

[2.2. Projektorganisation](docs/02_projektorganisation/projektorganisation.md)

[2.3 SWOT Analyse](docs/02_projektorganisation/swot.md)

[2.4 Tools & Software](docs/02_projektorganisation/management.md)

[2.5 GIT Branching Konzept](docs/02_projektorganisation/git_branching_konzept.md)

[2.6 Risikomanagement](docs/02_projektorganisation/risk_management.md)

[2.7 Sprint 01](docs/02_projektorganisation/sprint01/index.md)

[2.7.1 Sprint Planning](docs/02_projektorganisation/sprint01/planning.md)

[2.7.2 Backlog Refinement](docs/02_projektorganisation/sprint01/refinement.md)

[2.7.3 Sprint Review](docs/02_projektorganisation/sprint01/review.md)

[2.7.4 Sprint Retro](docs/02_projektorganisation/sprint01/retro.md)

[2.8 Sprint 02](docs/02_projektorganisation/sprint02/index.md)

[2.8.1 Sprint Planning](docs/02_projektorganisation/sprint02/planning.md)

[2.8.2 Backlog Refinement](docs/02_projektorganisation/sprint02/refinement.md)

[2.8.3 Sprint Review](docs/02_projektorganisation/sprint02/review.md)

[2.8.4 Sprint Retro](docs/02_projektorganisation/sprint02/retro.md)

[2.9 Sprint 03](docs/02_projektorganisation/sprint03/index.md)

[2.9.1 Sprint Planning](docs/02_projektorganisation/sprint03/planning.md)

[2.9.2 Backlog Refinement](docs/02_projektorganisation/sprint03/refinement.md)

[2.9.3 Sprint Review](docs/02_projektorganisation/sprint03/review.md)

[2.9.4 Sprint Retro](docs/02_projektorganisation/sprint03/retro.md)

[3. Service Design](docs/03_service_design/index.md)

[4. Services](docs/04_services/index.md)

[5. Microservices](docs/05_microservices/index.md)

[6. Storage](docs/06_storage/index.md)

[7. Security](docs/07_security/index.md)

[8. Deployment](docs/08_deployment/index.md)

[9. Fazit](docs/09_fazit/index.md)

## Literaturverzeichnis

Das Literaturverzeichnis, welches alle verwendeten Quellen alphabetisch aufgelistet enthält, finden Sie [hier](REFERENCES.md).

## Lizenz

Dieses Werk ist unter einer [Creative Commons Attribution-ShareAlike 3.0 Switzerland License](https://creativecommons.org/licenses/by-sa/3.0/ch/) lizenziert.

## Author Information

Diese Arbeit wurde im Jahr 2024 von [Yves Wetter](https://www.linkedin.com/in/yves-w/) erstellt.

![footer.svg](resources/images/footer.svg)
