---
lab:
  title: Übung 1 - Schützen von Daten in KI-Umgebungen
  module: Module 4 - Protect data in AI environments
---

## WWL-Mandanten – Nutzungsbedingungen

Wenn Ihnen im Rahmen einer Präsenzschulung ein Mandant zugewiesen worden ist, steht dieser für Praxislabs innerhalb der Präsenzschulung zur Verfügung.

Mandanten sollten nicht für Zwecke außerhalb von Praxislabs freigegeben oder verwendet werden. Der in diesem Kurs verwendete Mandant ist ein Testmandant; er kann nach Abschluss des Kurses nicht verwendet oder erreicht werden und ist nicht für Erweiterungen geeignet.

Mandanten dürfen nicht in ein kostenpflichtiges Abonnement konvertiert werden. Die im Rahmen dieses Kurses erworbenen Mandanten verbleiben im Eigentum der Microsoft Corporation, und wir behalten uns das Recht vor, jederzeit auf Mandanten zuzugreifen und diese zurückzuziehen.

# Labor 4 - Übung 1 - Schützen von Daten in KI-Umgebungen

Sie sind Joni Sherman, der Informationssicherheitsadministrator von Contoso Ltd. Da KI-Geräte wie Microsoft Copilot zunehmend in die täglichen Workflows integriert werden, wurde Ihr Team gebeten, den Schutz sensibler Daten zu bewerten und zu verbessern. In dieser Übung erfahren Sie, wie Microsoft Purview DSPM for AI durch die Erzwingung von Richtlinien, die Erkennung von Risiken und die Bewertung der Gefährdung dazu beitragen kann, Dateninteraktionen mit KI-Geräten zu sichern.

**Aufgaben:**

1. Verwenden Sie DSPM for AI, um eine DLP-Richtlinie für generative KI-Sites zu erstellen.
1. Erstellen Sie eine Richtlinie für Insiderrisiken, um riskante KI-Interaktionen zu erkennen
1. Blockieren des Zugriffs von Copilot auf gekennzeichnete Inhalte
1. Führen Sie eine Datenbewertung durch, um nicht gekennzeichnete Inhalte zu erkennen.

## Aufgabe 1 - Verwendung von DSPM for AI zur Erstellung einer DLP-Richtlinie für generative KI- Websites

Um das Risiko von Datenverlusten durch KI-Assistenten zu verringern, starten Sie mit der Erstellung einer DLP-Richtlinie mithilfe der Empfehlung „Verstärken Sie Ihre Datensicherheit“. Diese Richtlinie verwendet den adaptiven Schutz, um das Einfügen oder Hochladen sensibler Daten in KI-Geräte wie ChatGPT und Copilot in Edge, Chrome und Firefox zu beschränken.

1. Melden Sie sich bei der Client 1 VM (SC-401-CL1) im **SC-401-cl1\admin** -Konto an.

1. Navigieren Sie in **Microsoft Edge** zu **`https://purview.microsoft.com`** und melden Sie sich als **Joni Sherman**, `JoniS@WWLxZZZZZZ.onmicrosoft.com` an (wobei ZZZZZZ Ihre eindeutige Mandanten-ID ist, die von Ihrem Anbieter für das Hosting der Übung bereitgestellt wird).

1. Navigieren Sie in Microsoft Purview zu DSPM für AI, indem Sie **Lösungen** > **DSPM für AI** > **Empfehlungen** wählen.

1. Wählen Sie die Empfehlung **Verstärken Sie Ihre Datensicherheit**.

1. Überprüfen Sie auf der Flyout-Seite **Datensicherheit für AI** die Zusammenfassung und wählen Sie dann **Richtlinien erstellen**. Dadurch wird eine vorkonfigurierte DLP-Richtlinie erstellt, die auf generative KI-Sites abzielt.

1. Sobald die Richtlinie erstellt wurde, wählen Sie **Richtlinie anzeigen**.

1. Wählen Sie im Abschnitt **Richtliniendetails** die Option **Richtlinie in Lösung bearbeiten**, um die **Verhinderung von Datenverlusten**-Lösung in Microsoft Purview zu öffnen.

1. Suchen Sie auf der Seite **Richtlinien** die Richtlinie **DSPM für AI - Blockieren sensibler Informationen von AI-Sites** und wählen Sie sie aus.

1. Wählen Sie im Flyout **Simulation anzeigen**.

1. Wählen Sie auf dem Dashboard der Simulation die Option **Bearbeiten der Richtlinie**.

1. Wählen Sie **Weiter** aus, bis Sie die Seite **Auswählen der Anwendung der Richtlinie** erreicht haben. Bestätigen Sie, dass der Geltungsbereich der Richtlinie auf **Geräte** beschränkt ist.

1. Wählen Sie **Weiter** aus.

1. Wählen Sie auf der Seite **Erweiterte DLP-Regeln anpassen** das Symbol mit dem Bleistift neben **Blockieren mit Außerkraftsetzung für Benutzende mit erhöhtem Risiko**, um die Ansicht der Regel anzuzeigen.

1. Überprüfen Sie die Konfiguration der von DSPM für AI erstellten Regel:
   - Unter **Bedingungen** ist zu beachten, welche Typen vertraulicher Informationen enthalten sind und dass die Regel **Adaptiver Schutz** auf der Grundlage eines erhöhten Risikos verwendet.
   - Wählen Sie unter **Aktionen** sowohl für die Aktivität „Hochladen“ als auch für die Aktivität „Einfügen“ neben **Einschränkungen für sensible Dienstdomänen-Gruppen** die Option **Bearbeiten** aus.
   - Stellen Sie in der Konfiguration der Dienstdomänengruppe sicher, dass **Generative KI-Websites** auf **Mit Überschreibung blockieren** festgelegt ist.

1. Wählen Sie **Abbrechen**, um den Regeleditor ohne Änderungen zu beenden.

1. Wählen Sie auf der Seite **Erweiterte DLP-Regeln anpassen** die Option **Weiter** aus.

1. Wählen Sie auf der Seite **Richtlinienmodus** die Option **Die Richtlinie einschalten, wenn sie nicht innerhalb von fünfzehn Tagen nach der Simulation bearbeitet wird** und wählen Sie dann **Weiter**.

1. Wählen Sie auf der Seite **Überprüfen und beenden** die Option **Senden** und dann **Fertig**.

Sie haben eine Richtlinie erstellt, die die Freigabe sensibler Daten durch Benutzende mit hohem Risiko auf generativen KI-Websites verhindert, und die von DSPM für KI festgelegte Richtlinienkonfiguration bestätigt.

## Aufgabe 2 - Erstellen einer Richtlinie für Insiderrisiken, um riskante KI-Interaktionen zu erkennen

Als Nächstes erstellen Sie eine Richtlinie, mit der Sie riskantes Prompt-Verhalten in Copilot erkennen können.

1. Navigieren Sie in Microsoft Purview zu **DSPM für AI**, indem Sie **Lösungen** > **DSPM für AI** > **Empfehlungen** auswählen.

1. Wählen Sie die Empfehlung **Riskante Interaktionen in KI-Apps erkennen (Vorschau)**.

1. Überprüfen Sie auf der Flyout-Seite **Erkennen riskanter Interaktionen in KI-Apps (Vorschau)** die Zusammenfassung und wählen Sie dann **Richtlinie erstellen**.

1. Sobald die Richtlinie erstellt ist, wählen Sie **Richtlinie anzeigen**.

1. Wählen Sie im Abschnitt **Richtliniendetails** die Option **Richtlinie in Lösung bearbeiten**, um den Bereich **Insider-Risikomanagement** von Microsoft Purview zu öffnen.

1. Suchen Sie auf der Seite **Richtlinien** die Richtlinie **DSPM für KI - Erkennen riskanter AI-Nutzung** und wählen Sie sie aus.

1. Wählen Sie im Flyout **Richtlinie bearbeiten**, um die vollständige Konfiguration der Richtlinie zu überprüfen.

1. Beachten Sie auf der Seite **Vorlage auswählen**, dass die Richtlinie die Vorlage **Riskante KI-Verwendung (Vorschau)** verwendet.

1. Wählen Sie **Weiter**, bis Sie die Seite **Wählen Sie das auslösende Ereignis für diese Richtlinie** erreichen.
Bestätigen Sie, dass das auslösende Ereignis **Benutzerkonto von Microsoft Entra ID gelöscht** ist, was potenzielle Offboarding-Risiken signalisiert, die riskanten KI-Aktivitäten vorausgehen oder folgen können.

1. Wählen Sie **Weiter** aus.

1. Erweitern Sie auf der Seite **Indikatoren** die Indikatorenkategorien, um zu überprüfen, welche Signale ausgewählt sind:

   - Zu generativen KI-Websites durchsucht
   - Empfangene sensible Antwort von Copilot
   - Riskanter Prompt in Copilot eingegeben

1. Wählen Sie **Weiter**, bis Sie die Seite **Überprüfen und beenden** erreichen. Wählen Sie dann **Abbrechen**, um den Editor zu verlassen, ohne Änderungen zu machen.

Sie haben eine Richtlinie erstellt, die riskante KI-Interaktionen erkennt, einschließlich Prompts und Antworten, um frühe Anzeichen für riskantes Benutzenden-Verhalten zu erkennen.

## Aufgabe 3 – Blockieren des Zugriffs von Copilot auf gekennzeichnete Inhalte

Sie können das Risiko weiter verringern, indem Sie Copilot daran hindern, durch Vertraulichkeitsbezeichnungen geschützte Inhalte zu verarbeiten oder darauf zu antworten.

1. Navigieren Sie in Microsoft Purview zu **DSPM für AI**, indem Sie **Lösungen** > **DSPM für AI** > **Empfehlungen** auswählen.

1. Wählen Sie die Empfehlung **Schützen Sie sensible Daten, auf die in Microsoft 365 Copilot und Agents verwiesen wird (Vorschau)** aus.

1. Überprüfen Sie die in dieser Empfehlung bereitgestellten Hinweise.

1. Navigieren Sie zu **Lösungen** > **Vermeidung von Datenverlusten** > **Richtlinien**.

1. Wählen Sie **+ Richtlinie erstellen**, und wählen Sie dann **Benutzerdefinierte Richtlinie**.

1. Geben Sie auf der Seite **Benennen Sie Ihre Richtlinie** ein:

   - **Name**: `DLP - Block Copilot access to labeled content`
   - **Beschreibung:** `Prevents Microsoft 365 Copilot from processing or responding with content labeled using sensitivity labels.`

1. Wählen Sie **Weiter** aus, bis Sie die Seite **Auswählen der Anwendung der Richtlinie** erreicht haben.

1. Wählen Sie **Microsoft 365 Copilot (Vorschau)** als Geltungsbereich der Richtlinie und wählen Sie dann **Weiter**, bis Sie die Seite **Erweiterte DLP-Regeln anpassen** erreichen.

1. Wählen Sie **Regel erstellen**, und konfigurieren Sie:

   - **Name**: `Prevent Copilot from accessing labeled data`
   - Wählen Sie unter **Bedingungen** die Option **Bedingung hinzufügen** > **Inhalt enthält** > **Vertraulichkeitsbezeichnungen**. Fügen Sie diese Vertraulichkeitsbezeichnungen hinzu:
     - `Trusted People`
     - `Project - Falcon`
     - `Financial Data`
   - Wählen Sie **Hinzufügen** aus.
   - Wählen Sie unter **Aktionen** **Aktion hinzufügen** > **Copilot an der Verarbeitung von Inhalten hindern (Vorschau)**
   - Wählen Sie **Speichern** am unteren Rand des Flyouts **Regel erstellen**.

1. Wählen Sie auf der Seite **Erweiterte DLP-Regeln anpassen** die Option **Weiter** aus.

1. Wählen Sie auf der Seite **Richtlinienmodus** die Option **Sofortige Aktivierung der Richtlinie**, und wählen Sie dann **Weiter**.

1. Wählen Sie auf der Seite **Überprüfen und beenden** die Option **Senden** und dann **Fertig** auf der Seite **Neue Richtlinie erstellt**.

1. Kehren Sie zu **DSPM für KI-Empfehlungen** zurück, indem Sie **Lösungen** > **DSPM für KI** > **Empfehlungen** wählen.

1. Wählen Sie die Empfehlung **Schützen Sie sensible Daten, auf die in Microsoft 365 Copilot und Agents verwiesen wird (Vorschau)** aus und wählen Sie **Als abgeschlossen markieren**.

Sie haben eine DLP-Richtlinie erstellt, die verhindert, dass gekennzeichnete Inhalte in Copilot-Prompts und -Antworten verwendet werden.

## Aufgabe 4 – Durchführen einer Datenrisikobewertung, um nicht gekennzeichnete Inhalte zu erkennen

Um mögliche Lücken in der Abdeckung der Bezeichnungen zu erkennen, führen Sie eine Datenrisikobewertung durch, um Dateien ohne Vertraulichkeitsbezeichnungen zu identifizieren, auf die Copilot zugreifen könnte.

1. Wählen Sie unter **DSPM für KI** die Empfehlung mit dem Titel **Schützen Sie sensible Daten, auf die in Copilot- und Agent-Antworten verwiesen wird**.

1. Überprüfen Sie im Bereich **Schützen Sie sensible Daten, auf die in Copilot- und Agent-Antworten verwiesen wird** die Zusammenfassung und wählen Sie dann **Zu Einschätzungen wechseln**.

1. Auf der Seite **Datenrisikobewertungen** wählen Sie **Benutzerdefinierte Bewertung erstellen**.

1. Geben Sie auf der Seite **Grundlegende Details** ein:

   - **Name**: `Unlabeled File Exposure Assessment`
   - **Beschreibung:** `Identifies files without sensitivity labels that may be exposed in Microsoft 365 Copilot responses and provides recommendations to reduce oversharing risks.`

1. Wählen Sie **Weiter** aus.

1. Auf der Seite **Benutzende hinzufügen**, wählen Sie **Alle** und dann **Weiter**.

1. Lassen Sie auf der Seite **Zu bewertende Datenquellen hinzufügen** den Standardstandort **SharePoint** ausgewählt, und wählen Sie dann **Weiter**.

1. Wählen Sie auf der Seite **Überprüfen und Ausführen der Datenbewertungsprüfung** die Option **Speichern und Ausführen**.

1. Wählen Sie auf der Seite **Datenbewertung erfolgreich erstellt** die Option **Fertig**.

Sie haben nun Microsoft Purview DSPM für KI verwendet, um KI-bezogene Risiken zu erkennen, Richtlinien zu erzwingen und die Gefährdung sensibler Daten zu bewerten, was Ihrem Unternehmen hilft, KI sicher zu verwenden.
