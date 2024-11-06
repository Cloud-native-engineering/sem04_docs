---
layout: default
title: 4.6 Servicekosten
parent: 4. Service Design
nav_order: 6
---

# 4.6 Servicekosten

In diesem Abschnitt werden die Kosten analysiert, die mit dem Betrieb des TuringPi Cluster entstehen. Dabei werden die Hardware- sowie die Kosten für den Betrieb aufgelistet.

## Direkte Kosten

Die Direkte Kosten in diesem Fall beinhalten die ganze Anschaffungskosten des TuringPi clusters.

| **Kostenpunkt**         | **Betrag (CHF)** |
| ----------------------- | ---------------- |
| TuringPi 2 Board        | 240.-            |
| 4x RK1 8GB RAM Module   | 565.-            |
| 4x 2TB NVMe Festplatten | 395              |
| Sonstige Hardware       | 100              |
| **Gesamtkosten**        | **1'300**        |

## Betriebskosten

Die Betriebskosten beinhalten alle laufenden Kosten, die für den Betrieb und die Wartung des Clusters anfallen. Dazu gehören unter anderem die Kosten für die Infrastruktur, die Überwachung und den Support. Im Normalfall würden diese Kosten detailliert aufgelistet werden, aber für die Semesterarbeit werden nur die Stromkosten berücksichtigt.

Die Stromkosten im Durchschnitt für eine Kilowattstunde betragen in der Schweiz 29 Rappen. Es wird in diesem Beispiel angenommen, dass der TuringPi mit allen Rechenmodulen auf Volllast läuft und somit 80 Watt benötigt.

Um die jährlichen Stromkosten zu berechnen, gehen wir wie folgt vor:

1. **Leistungsaufnahme in Kilowatt**: 80 Watt = 0.08 Kilowatt
2. **Stunden pro Tag**: 24 Stunden
3. **Tage pro Jahr**: 365 Tage
4. **Kilowattstunden pro Jahr**: 0.08 kW _ 24 Stunden _ 365 Tage = 700.8 kWh
5. **Kosten pro Kilowattstunde**: 29 Rappen = 0.29 CHF

Jährliche Stromkosten: 700.8 kWh \* 0.29 CHF/kWh = 203.23 CHF

Die jährlichen Stromkosten für den Betrieb des TuringPi Clusters betragen somit etwa 203.23 CHF.

## FinOps Optimierung

Um die Kosten weiter zu reduzieren, könnten einige Compute-Module heruntergefahren werden, wenn diese nicht benötigt werden. Dies könnte automatisiert werden mit einem Scheduler, wie zum Beispiel einem Cron-Script. Durch das gezielte Abschalten nicht benötigter Ressourcen kann der Energieverbrauch weiter gesenkt und somit die Betriebskosten reduziert werden.

Angenommen, wir können die Compute-Module für 12 Stunden pro Tag herunterfahren, würde sich der Energieverbrauch wie folgt ändern:

1. **Leistungsaufnahme in Kilowatt**: 80 Watt = 0.08 Kilowatt
2. **Stunden pro Tag**: 12 Stunden
3. **Tage pro Jahr**: 365 Tage
4. **Kilowattstunden pro Jahr**: 0.08 kW _ 12 Stunden _ 365 Tage = 350.4 kWh
5. **Kosten pro Kilowattstunde**: 29 Rappen = 0.29 CHF

Jährliche Stromkosten bei 12 Stunden Betrieb pro Tag: 350.4 kWh \* 0.29 CHF/kWh = 101.62 CHF

Durch das Herunterfahren der Compute-Module für 12 Stunden pro Tag könnten die jährlichen Stromkosten auf etwa 101.62 CHF reduziert werden.

## Gesamtkosten über 5 Jahre

In diesem Beispiel wird davon ausgegangen, dass der Cluster nach 5 Jahren abgeschrieben ist. Somit werden die Kosten über diesen Zeitraum berechnet. Nach 5 Jahren sind nur noch die Stromkosten relevant.

| **Kostenpunkt**          | **Betrag (CHF)**       |
| ------------------------ | ---------------------- |
| Direkte Kosten           | 1'300                  |
| Betriebskosten (5 Jahre) | 203.23 \* 5 = 1'016.15 |
| **Gesamtkosten**         | **2'316.15**           |

Mit Optimierung durch Herunterfahren der Compute-Module:

| **Kostenpunkt**          | **Betrag (CHF)**     |
| ------------------------ | -------------------- |
| Direkte Kosten           | 1'300                |
| Betriebskosten (5 Jahre) | 101.62 \* 5 = 508.10 |
| **Gesamtkosten**         | **1'808.10**         |
