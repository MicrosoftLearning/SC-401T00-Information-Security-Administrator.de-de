---
lab:
  title: Übung 3 - Vertraulichkeitsbezeichnungen erstellen und verwalten
  module: Module 1 - Implement Information Protection
---

# Übung 1 - Übung 3 - Vertraulichkeitsbezeichnungen erstellen und verwalten

Joni Sherman, ein Administrator für Informationssicherheit bei Contoso Ltd., führt eine Strategie zur Kennzeichnung der Vertraulichkeit ein, um sensible Daten abteilungsübergreifend zu schützen. Dazu konfiguriert sie manuelle und automatische Kennzeichnungen, Unterbezeichnungen und Verschlüsselungsoptionen, einschließlich der Unterstützung von Double Key Encryption (DKE) und der Integration mit Microsoft Defender für Cloud Apps.

**Aufgaben:**

1. Aktivieren der Unterstützung für Vertraulichkeitsbezeichnungen
1. Erstellen einer Vertraulichkeitsbezeichnung
1. Erstellen einer Unterbezeichnung
1. Veröffentlichen von Vertraulichkeitsbezeichnungen
1. Konfigurieren der automatischen Bezeichnung
1. Erstellung und Veröffentlichung einer DKE-Kennzeichnung für in hohem Maße vertrauliche Inhalte
1. Aktivieren der Microsoft Purview-Integration in Defender for Cloud Apps
1. Erstellen einer Dateirichtlinie zur automatischen Kennzeichnung extern freigegebener Dateien

## Aufgabe 1 - Aktivieren Sie den Kundendienst für Vertraulichkeitsbezeichnungen

In dieser Aufgabe aktivieren Sie die Co-Authoring-Funktion für Vertraulichkeitsbezeichnungen, die auch Vertraulichkeitsbezeichnungen für Dateien in SharePoint und OneDrive ermöglicht.

1. Sie sollten immer noch bei Client 1 VM (SC-401-CL1) als **SC-401-CL1\admin**-Konto angemeldet sein und bei Microsoft Purview als Joni Sherman angemeldet sein.

1. Öffnen Sie **Microsoft Edge**, und navigieren Sie dann zu `https://purview.microsoft.com`.

1. Wählen Sie in der linken Navigation **Einstellungen** > **Informationsschutz**.

1. In den **Einstellungen für den Informationsschutz** stellen Sie sicher, dass Sie sich auf der Registerkarte **Co-Authoring für Dateien mit Vertraulichkeitsbezeichnungen** befinden.

1. Aktivieren Sie das Kontrollkästchen für **Ko-Authoring für Dateien mit Vertraulichkeitsbezeichnungen einschalten**.

1. Wählen Sie **Anwenden** am unteren Rand des Bildschirms.

Sie haben erfolgreich den Kundendienst für Vertraulichkeitsbezeichnungen für Dateien in SharePoint und OneDrive aktiviert.

## Aufgabe 2 – Erstellen Sie eine Vertraulichkeitsbezeichnung

In dieser Aufgabe werden Sie eine übergeordnete Vertraulichkeitsbezeichnung für interne Inhalte erstellen. Diese Kennzeichnung enthält grundlegende Einstellungen und dient als übergeordnete Kennzeichnung für abteilungsspezifische Unterbezeichnungen.

1. Sie sollten weiterhin bei Client 1 VM (SC-401-CL1) im **SC-401-CL1\admin**-Konto angemeldet sein.

1. Navigieren Sie in **Microsoft Edge** zu `https://purview.microsoft.com`.

1. Wählen Sie im Microsoft Purview-Portal in der linken Seitenleiste **Lösungen** und dann **Informationsschutz**.

1. Wählen Sie auf der Seite **Microsoft Information Protection** in der linken Seitenleiste **Vertraulichkeitsbezeichnungen**.

1. Auf der Seite **Vertraulichkeitsbezeichnungen** wählen Sie **+ Bezeichnung erstellen**.

1. Die Konfiguration der **Neuen Vertraulichkeitsbezeichnung** wird gestartet. Geben Sie auf der Seite **Basisdetails für diese Bezeichnung bereitstellen** ein:

    - **Name**: `Internal`
    - **Anzeigename**: `Internal`
    - **Beschreibung für Benutzende**: `Internal sensitivity label.`
    - **Beschreibung für Administratoren**: `Internal sensitivity label for Contoso.`

1. Wählen Sie **Weiter** aus.

1. Wählen Sie auf der Seite **Definieren eines Geltungsbereichs für diese Bezeichnung** die Option **Elemente** aus und wählen Sie dann **Dateien** und **E-Mails** aus. Wenn das Kontrollkästchen für **Besprechungen** aktiviert ist, stellen Sie sicher, dass es abgewählt ist.

1. Wählen Sie **Weiter** aus.

1. Wählen Sie auf der Seite **Schutzeinstellungen für gekennzeichnete Elemente festlegen** **Weiter**.

1. Wählen Sie auf der Seite **Automatische Bezeichnung für Dateien und E-Mails** **Weiter**.

1. Wählen Sie auf der Seite **Schutzeinstellungen für Gruppen und Standorte festlegen** die Option **Weiter**.

1. Wählen Sie auf der Seite **Einstellungen überprüfen und fertig stellen** die Option **Bezeichnung erstellen** aus.

1. Wählen Sie auf der Seite **Vertraulichkeitsbezeichnung** die Option **Richtlinie noch nicht erstellen** aus, und wählen Sie dann **Fertig** aus.

Sie haben eine Vertraulichkeitsbezeichnung für den internen Gebrauch erstellt. Diese Kennzeichnung dient als übergeordnete Kennzeichnung für spezifischere Unterbezeichnungen, die in unterschiedlichen Abteilungen verwendet werden.

## Aufgabe 3 - Erstellen einer Unterbezeichnung

Nachdem Sie nun eine Basiskennzeichnung haben, werden Sie eine Unterbezeichnung für personalbezogene Dokumente erstellen. Diese Unterbezeichnung umfasst Schutzeinstellungen und sichtbare Inhaltsmarkierungen, die die interne Handhabung von Daten durch die Personalabteilung unterstützen.

1. Auf der Seite **Vertraulichkeitsbezeichnungen** finden Sie die neu erstellte **Interne** Vertraulichkeitsbezeichnung. Wählen Sie die vertikalen Auslassungspunkte (**...**) daneben, dann wählen Sie **+ Unterbezeichnung erstellen** aus dem Dropdownmenü.

    ![Screenshot des Aktionsmenüs zum Erstellen einer Unterbezeichnung für eine Vertraulichkeitsbezeichnung.](../Media/create-sublabel-button.png)

1. Der Assistent **Neue Vertraulichkeitsbezeichnung** wird gestartet. Geben Sie auf der Seite **Basisdetails für diese Bezeichnung bereitstellen** Folgendes ein:

   - **Name**: `Employee data (HR)`
   - **Anzeigename**: `Employee data (HR)`
   - **Beschreibung für Benutzende**: `This HR label is the default label for all specified documents in the HR Department.`
   - **Beschreibung für Administratoren**: `This label is created in consultation with Ms. Jones (Head of HR department). Contact her if you need to change the label settings.`

1. Wählen Sie **Weiter** aus.

1. Wählen Sie auf der Seite **Definieren eines Geltungsbereichs für diese Bezeichnung** die Option **Elemente** aus und wählen Sie dann **Dateien** und **E-Mails** aus. Wenn das Kontrollkästchen für **Besprechungen** aktiviert ist, stellen Sie sicher, dass es abgewählt ist.

1. Wählen Sie **Weiter** aus.

1. Wählen Sie auf der Seite **Schutzeinstellungen für bezeichnete Elemente auswählen** die Optionen **Zugriff kontrollieren** und **Inhaltsmarkierung anwenden** und wählen Sie dann **Weiter**.

1. Wählen Sie auf der Seite **Zugriffssteuerung** die Option **Konfigurieren der Einstellungen für die Zugriffssteuerung**.

1. Konfigurieren Sie die Verschlüsselungseinstellungen mit diesen Optionen:

   - **Berechtigungen jetzt zuweisen oder die Benutzenden entscheiden lassen?**: Berechtigungen jetzt zuweisen
   - **Benutzender-Zugriff auf Inhalte läuft ab**: Nie
   - **Offlinezugriff erlauben**: Nur für eine bestimmte Anzahl von Tagen
   - **Benutzende haben für so viele Tage Offlinezugriff auf den Inhalt**: 15
   - Wählen Sie den Link **Berechtigungen zuweisen**. Wählen Sie im Flyout-Bedienfeld **Berechtigungen zuweisen** die Option **+ Alle authentifizierten Benutzenden hinzufügen**, und wählen Sie dann **Speichern**, um diese Einstellung zu übernehmen.

1. Auf der Seite **Zugriffssteuerung** wählen Sie **Weiter**.

1. Wählen Sie auf der Seite **Inhaltsmarkierung** den Schalter, um die **Inhaltsmarkierung** zu aktivieren.

1. Aktivieren Sie für jeden der folgenden Typen das Kontrollkästchen und wählen Sie dann das Symbol „Bearbeiten“, um den Text einzugeben:

   |Kennzeichnungstyp|Text|
   |:---|:---|
   |Ein Wasserzeichen hinzufügen|`INTERNAL USE ONLY`|
   |Hinzufügen einer Kopfzeile|`Internal Document`|
   |Hinzufügen einer Fußzeile|`Contoso Confidential`|

1. Wählen Sie **Weiter** aus.

1. Wählen Sie auf der Seite **Automatische Bezeichnung für Dateien und E-Mails** **Weiter**.

1. Wählen Sie auf der Seite **Schutzeinstellungen für Gruppen und Standorte festlegen** die Option **Weiter**.

1. Wählen Sie auf der Seite **Einstellungen überprüfen und fertig stellen** die Option **Bezeichnung erstellen** aus.

1. Wählen Sie auf der Seite **Vertraulichkeitsbezeichnung** die Option **Richtlinie noch nicht erstellen** aus, und wählen Sie dann **Fertig** aus.

Sie haben eine Unterbezeichnung erstellt, die Verschlüsselungs- und Inhaltsmarkierungen auf HR-Dokumente anwendet. Mit dieser Kennzeichnung wird sichergestellt, dass nur authentifizierte Benutzende Zugriff auf die HR-Daten haben und dass sie durch visuelle Markierungen identifiziert werden können.

## Aufgabe 4 - Veröffentlichung von Vertraulichkeitsbezeichnungen

Sie veröffentlichen nun die Vertraulichkeitsbezeichnungen von Intern und HR, so dass die veröffentlichten Vertraulichkeitsbezeichnungen für die Benutzenden in der Personalabteilung zur Anwendung auf ihre HR-Dokumente verfügbar sind.

1. Sie sollten immer noch bei Client 1 VM (SC-401-CL1) als **SC-401-cl1\admin** angemeldet sein, und Sie sollten bei Microsoft Purview als **Joni Sherman** angemeldet sein.

1. In **Microsoft Edge** sollte die Registerkarte des Microsoft Purview-Portals noch geöffnet sein. Falls nicht, navigieren Sie zu **`https://purview.microsoft.com`** > **Lösungen** > **Informationsschutz** > **Vertraulichkeitsbezeichnungen**.

1. Auf der Seite **Vertraulichkeitsbezeichnungen** wählen Sie **Bezeichnungen veröffentlichen**.

1. Die Konfiguration der Veröffentlichung von Vertraulichkeitsbezeichnungen wird gestartet.

1. Wählen Sie auf der Seite **Wählen Sie die zu veröffentlichenden Vertraulichkeitsbezeichnungen** den Link **Wählen Sie die zu veröffentlichenden Vertraulichkeitsbezeichnungen**.

1. Aktivieren Sie im Flyout-Bereich **Vertraulichkeitsbezeichnungen zum Veröffentlichen** die Kontrollkästchen **Intern** und **Intern/Mitarbeitende Person (HR)** und wählen Sie dann **Hinzufügen** unten auf der Flyout-Seite.

1. Zurück auf der Seite **Wählen Sie die zu veröffentlichenden Vertraulichkeitsbezeichnungen aus**, wählen Sie **Weiter**.

1. Wählen Sie auf der Seite **Admineinheiten zuweisen** **Weiter**

1. Wählen Sie auf der Seite **Veröffentlichen für Benutzer und Gruppen** die Option **Weiter**.

1. Wählen Sie auf der Seite **Richtlinieneinstellungen** **Weiter**.

1. Auf der Seite **Standardeinstellungen für Dokumente** wählen Sie **Weiter**.

1. Auf der Seite **Standardeinstellungen für E-Mails** wählen Sie **Weiter**.

1. Auf der Seite **Standardeinstellungen für Besprechungen und Kalenderereignisse** wählen Sie **Weiter**.

1. Auf der Seite **Standardeinstellungen für Power BI Content** wählen Sie **Weiter**.

1. Auf der Seite **Benennen Sie Ihre Richtlinie**, geben Sie ein:

   - **Name**: `Internal HR employee data`

   - **Geben Sie eine Beschreibung für Ihre Vertraulichkeitsbezeichnungsrichtlinie** ein: `This HR label is to be applied to internal HR employee data.`

1. Wählen Sie **Weiter** aus.

1. Auf der Seite **Überprüfen und beenden** wählen Sie **Absenden**.

1. Wählen Sie auf der Seite **Neue Richtlinie erstellt** die Option **Erledigt**, um die Veröffentlichung Ihrer Bezeichnungsrichtlinie zu beenden.

Sie haben die Vertraulichkeitsbezeichnungen „Intern“ und „HR“ erfolgreich veröffentlicht. Beachten Sie, dass es bis zu 24 Stunden dauern kann, bis die Änderungen auf alle Benutzende und Dienste übertragen sind.

## Aufgabe 5 - Konfigurieren der automatischen Bezeichnung

In dieser Aufgabe erstellen Sie eine Vertraulichkeitsbezeichnung für Finanzdaten und konfigurieren sie so, dass sie automatisch auf Inhalte angewendet wird, die bestimmte Finanzkennungen enthalten, z. B. Kreditkartennummern und Bankleitzahlen.

1. Sie sollten weiterhin bei Client 1 VM (SC-401-CL1) als **SC-401-cl1\admin**-Konto angemeldet sein.

1. Navigieren Sie in **Microsoft Edge** zu `https://purview.microsoft.com` und melden Sie sich im Microsoft Purview Portal als **Joni Sherman** an.

1. Wählen Sie im Microsoft Purview-Portal **Lösungen** > **Informationsschutz** > **Vertraulichkeitsbezeichnungen**.

1. Auf der Seite **Vertraulichkeitsbezeichnungen** finden Sie die Vertraulichkeitsbezeichnung **Intern**. Wählen Sie die vertikalen Auslassungspunkte (**...**), dann wählen Sie **+ Unterbezeichnung erstellen** aus dem Dropdownmenü.

1. Geben Sie auf der Seite **Basisdetails für diese Bezeichnung bereitstellen** Folgendes ein:

   |Details|Text|
   |---|---|
   |**Name**|`Financial Data`|
   |**Anzeigename**|`Financial Data`|
   |**Beschreibung für Benutzende**|`This content contains financial data that must be labeled and protected.`|
   |**Beschreibung für Admins**|`This label is used for content that includes sensitive financial identifiers.`|

1. Wählen Sie **Weiter** aus.

1. Wählen Sie auf der Seite **Definieren eines Geltungsbereichs für diese Bezeichnung** die Option **Elemente** aus und wählen Sie dann **Dateien** und **E-Mails** aus. Wenn das Kontrollkästchen für **Besprechungen** aktiviert ist, stellen Sie sicher, dass es abgewählt ist.

1. Wählen Sie **Weiter** aus.

1. Wählen Sie auf der Seite **Schutzeinstellungen für gekennzeichnete Elemente festlegen** **Weiter**.

1. Auf der Seite **Automatische Bezeichnungen für Dateien und E-Mails** legen Sie die **Automatische Bezeichnungen für Dateien und E-Mails** auf „aktiviert" fest.

1. Wählen Sie im Abschnitt **Inhalt erkennen, der diesen Bedingungen entspricht** die Option **+ Bedingung hinzufügen** > **Inhalt enthält**.

1. Wählen Sie im Abschnitt **Inhalt enthält** die Option **Hinzufügen** > **Sensible Typen vertraulicher Informationen**.

1. Suchen Sie auf der Flyout-Seite **Typen vertraulicher Informationen** nach den Typen vertraulicher Informationen und wählen Sie diese aus:

   - `Credit Card Number`
   - `ABA Routing Number`
   - `SWIFT Code`

1. Wählen Sie **Hinzufügen**.

1. Zurück auf der Seite **Automatische Bezeichnung für Dateien und E-Mails**, wählen Sie **Weiter**.

1. Wählen Sie auf der Seite **Schutzeinstellungen für Gruppen und Standorte festlegen** die Option **Weiter**.

1. Wählen Sie auf der Seite **Einstellungen überprüfen und fertig stellen** die Option **Bezeichnung erstellen** aus.

1. Wählen Sie auf der Seite **Ihre Vertraulichkeitsbezeichnung wurde erstellt** die Option **Kennzeichnung automatisch auf vertrauliche Inhalte anwenden** und dann **Erledigt**.

1. Wählen Sie auf der Flyout-Seite **Automatische Bezeichnung erstellen** die Option **Review-Richtlinie**.

1. Auf der Seite **Benennen Sie Ihre automatische Bezeichnung** belassen Sie die Voreinstellung und wählen Sie dann **Weiter**.

1. Überprüfen Sie auf der Seite **Wählen Sie eine Kennzeichnung, die automatisch angewendet werden soll**, ob die Kennzeichnung _Interne/Finanzdaten_ ausgewählt ist, und wählen Sie dann **Weiter**.

1. Wählen Sie auf der Seite **Admineinheiten zuweisen** **Weiter**.

1. Wählen Sie auf der Seite **Wählen Sie Standorte aus, an denen Sie die Kennzeichnung anwenden möchten** die Optionen für:

   - Exchange-E-Mail
   - SharePoint-Websites
   - OneDrive Konten

1. Wählen Sie **Weiter** aus.

1. Lassen Sie auf der Seite **Gemeinsame oder erweiterte Regeln einrichten** die Standardeinstellung **Gemeinsame Regeln** ausgewählt, und wählen Sie dann **Weiter**.

1. Erweitern Sie auf der Seite **Regeln für Inhalte an allen Standorten definieren** die Regeln für _Finanzdatenregel_, um sicherzustellen, dass die erwarteten Regeln definiert sind, und wählen Sie dann **Weiter**.

1. Wählen Sie auf der Seite **Zusätzliche Einstellungen für E-Mail** **Weiter**.

1. Wählen Sie auf der Seite **Entscheiden Sie, ob Sie die Richtlinie jetzt oder später testen möchten** die Option **Richtlinie im Simulationsmodus ausführen** und aktivieren Sie das Kontrollkästchen für **Richtlinie automatisch einschalten, wenn sie nach 7 Tagen in der Simulation nicht geändert wurde**.

1. Wählen Sie **Weiter** aus.

1. Auf der Seite **Überprüfen und beenden** wählen Sie **Richtlinie erstellen**.

1. Wählen Sie auf der Seite Ihre **Richtlinie für die automatische Bezeichnung wurde erstellt** die Option **Fertig**.

Sie haben erfolgreich eine Vertraulichkeitsbezeichnung für Finanzdaten erstellt und eine Richtlinie für die automatische Bezeichnung konfiguriert, um Inhalte zu erkennen und zu kennzeichnen, die vertrauliche Finanzdaten enthalten.

## Aufgabe 6 - Erstellung und Veröffentlichung einer DKE-Kennzeichnung für in hohem Maße vertrauliche Inhalte

In dieser Aufgabe erstellen Sie eine Unterbezeichnung unter der integrierten Kennzeichnung Streng vertraulich. Diese Unterbezeichnung verwendet Double Key Encryption (DKE) und dynamische Wasserzeichen, um sensible Inhalte zu schützen, auf die nur die Rechtsabteilung Zugriff hat. Sie werden auch eine Bezeichnungsrichtlinie konfigurieren, die eine Begründung für die Herabstufung der Kennzeichnung erfordert.

1. Sie sollten weiterhin bei Client 1 VM (SC-401-CL1) als **SC-401-cl1\admin**-Konto angemeldet sein.

1. Navigieren Sie in **Microsoft Edge** zu `https://purview.microsoft.com` und melden Sie sich im Microsoft Purview Portal als **Joni Sherman** an.

1. Wählen Sie im Microsoft Purview-Portal **Lösungen** > **Informationsschutz** > **Vertraulichkeitsbezeichnungen**.

1. Auf der Seite **Vertraulichkeitsbezeichnungen** finden Sie die Kennzeichnung **Streng vertraulich**. Wählen Sie die vertikalen Auslassungspunkte (**...**), dann wählen Sie **+ Unterbezeichnung erstellen** aus dem Dropdownmenü.

1. Geben Sie auf der Seite **Basisdetails für diese Bezeichnung bereitstellen** Folgendes ein:

   |Details|Text|
   |---|---|
   |**Name**|`Highly Confidential - Legal`|
   |**Anzeigename**|`Highly Confidential - Legal`|
   |**Beschreibung für Benutzende**|`Use this label for highly sensitive content that must be encrypted using Double Key Encryption.`|
   |**Beschreibung für Admins**|`Label configured with DKE and dynamic watermarking for highly sensitive content.`|

1. Wählen Sie **Weiter** aus.

1. Wählen Sie auf der Seite **Definieren Sie den Geltungsbereich für diese Kennzeichnung** **Dateien** und **E-Mails**. Wenn das Kontrollkästchen für **Besprechungen** aktiviert ist, stellen Sie sicher, dass es abgewählt ist.

1. Wählen Sie auf der Seite **Wählen Sie die Schutzeinstellungen für die von Ihnen ausgewählten Typen von Elementen**, wählen Sie **Zugriff kontrollieren** und dann **Weiter**.

1. Wählen Sie auf der Seite **Zugriffssteuerung** die Option **Konfigurieren der Einstellungen für die Zugriffssteuerung**.

1. Konfigurieren Sie die Verschlüsselungseinstellungen mit diesen Optionen:

   - **Berechtigungen jetzt zuweisen oder die Benutzenden entscheiden lassen?**: Berechtigungen jetzt zuweisen

   - **Benutzender-Zugriff auf den Inhalt läuft ab**: Eine Anzahl von Tagen nach Anwendung der Kennzeichnung

   - **Der Zugriff läuft so viele Tage nach Anwendung der Kennzeichnung ab**: 5

   - **Offlinezugriff zulassen**: Nie

   - Wählen Sie den Link **Berechtigungen zuweisen**. Wählen Sie im Flyoutbereich **Berechtigungen zuweisen** die Option **+ Benutzer oder Gruppen hinzufügen**.

   - Suchen Sie auf der Flyout-Seite **Benutzende oder Gruppen hinzufügen** nach `Legal Team` und `Joni Sherman`, und wählen Sie **Hinzufügen**.

   - Auf der Seite **Berechtigungen zuweisen** wählen Sie **Speichern**.

1. Aktivieren Sie auf der Seite **Zugriffssteuerung** das Kontrollkästchen für **Dynamisches Wasserzeichen verwenden** und wählen Sie dann **Text anpassen (optional)**.

1. Auf der Seite **Benutzerdefinierten Text zum Wasserzeichen hinzufügen (optional)** geben Sie `Confidential` ein und wählen dann die Links für **UPN** und **Zeitstempel**.

1. Wählen Sie **Speichern** am unteren Rand der Flyout-Seite.

1. Aktivieren Sie auf der Seite **Zugriffssteuerung** das Kontrollkästchen für **Doppelschlüsselverschlüsselung verwenden** und geben Sie `https://testingdke1.azurewebsites.net/Test` als URL für den Dienst Double Key Encryption ein.

1. Wählen Sie **Weiter** aus.

1. Wählen Sie auf der Seite **Automatische Bezeichnung für Dateien und E-Mails** **Weiter**.

1. Wählen Sie auf der Seite **Schutzeinstellungen für Gruppen und Standorte festlegen** die Option **Weiter**.

1. Wählen Sie auf der Seite **Einstellungen überprüfen und fertig stellen** die Option **Bezeichnung erstellen** aus.

1. Wählen Sie auf der Seite **Ihre Vertraulichkeitsbezeichnung wurde erstellt** die Option **Bezeichnung in den Apps der Benutzenden veröffentlichen** und wählen Sie dann **Erledigt**.

1. Wählen Sie auf der Flyout-Seite **Kennzeichnung veröffentlichen** die Option **Neue Bezeichnungsrichtlinie erstellen**.

1. Wählen Sie auf der Seite **Auswahl der zu veröffentlichenden Vertraulichkeitsbezeichnungen** die Option **Auswahl der zu veröffentlichenden Vertraulichkeitsbezeichnungen** und fügen Sie die Kennzeichnung **Vertraulichkeitsbezeichnung** und die Unterbezeichnung **Vertraulichkeitsbezeichnung – Rechtlich** hinzu und wählen Sie dann **Hinzufügen**.

1. Wählen Sie **Weiter** aus.

1. Wählen Sie auf der Seite **Admineinheiten zuweisen** **Weiter**.

1. Lassen Sie auf der Seite **Veröffentlichen für Benutzende und Gruppen** die Standardeinstellung ausgewählt und wählen Sie dann **Weiter**.

1. Aktivieren Sie auf der Seite **Richtlinieneinstellungen** das Kontrollkästchen für **Benutzende müssen eine Begründung bereitstellen, um eine Bezeichnung zu entfernen oder ihre Klassifizierung herabzusetzen** und wählen Sie dann **Weiter** aus.

1. Wählen Sie auf der Seite **Standardeinstellungen für Dokumente** die Option **Weiter**.

1. Wählen Sie auf der Seite **Standardeinstellungen für E-Mails** **Weiter**.

1. Wählen Sie auf der Seite **Standardeinstellungen für Besprechungen und Kalenderereignisse** die Option **Weiter**.

1. Wählen Sie auf der Seite **Standardeinstellungen für Fabric- und Power BI-Inhalte** die Option **Weiter**.

1. Auf der Seite **Benennen Sie Ihre Richtlinie**, geben Sie ein:

   - **Name**: `Highly Confidential - Legal`

   - **Beschreibung:** `Enables manual use of the DKE label for highly confidential content accessible by Legal.`

1. Wählen Sie **Weiter** aus.

1. Auf der Seite **Überprüfen und beenden** wählen Sie **Absenden**.

1. Wählen Sie auf der Seite **Neue Richtlinie erstellt** die Option **Fertig** aus.

Sie haben erfolgreich eine Unterbezeichnung mithilfe von Double Key Encryption mit dynamischem Wasserzeichen erstellt und veröffentlicht. Diese Kennzeichnung stellt einen starken Schutz für in hohem Maße vertrauliche Inhalte bereit und sorgt für eine Erzwingung des eingeschränkten Zugriffs und der Rechtfertigung von Klassifizierungsänderungen.

## Aufgabe 7 - Aktivieren der Microsoft Purview-Integration in Defender for Cloud-Apps

In dieser Aufgabe aktivieren Sie die Microsoft Purview-Integration in Microsoft Defender for Cloud-Apps. Dies ermöglicht es Defender, neue Dateien auf Microsoft Purview Vertraulichkeitsbezeichnungen zu prüfen und den Inhalt auf der Grundlage dieser Kennzeichnungen zu untersuchen.

1. Sie sollten immer noch bei Client 1 VM (SC-401-CL1) als **SC-401-CL1\admin** angemeldet sein, und Sie sollten immer noch als Joni Sherman angemeldet sein.

1. Öffnen Sie **Microsoft Edge**, und wechseln Sie dann zu **Microsoft Defender**, indem Sie zu `https://security.microsoft.com` navigieren.

1. Wählen Sie in der linken Navigation **Einstellungen** und dann **Cloud Apps**.

1. Wählen Sie unter dem Abschnitt **Informationsschutz** im linken Bereich **Microsoft Informationsschutz**.

1. Aktivieren Sie auf der Seite **Microsoft Information Protection** beide auf der Seite verfügbaren Kontrollkästchen.

    ![Screenshot mit beiden aktivierten Kontrollkästchen für den Informationsschutz im Defender-Portal.](../Media/defender-information-protection-settings.png)

   - **Scannen Sie neue Dateien automatisch auf Microsoft Information Protection Vertraulichkeitsbezeichnungen und Warnungen zur Inhaltskontrolle**

      Aktiviert Defender for Cloud-Apps, um neue oder geänderte Dateien automatisch auf Vertraulichkeitsbezeichnungen und Warnungen zur Inhaltskontrolle von Microsoft Purview zu überprüfen.

   - **Scannen Sie Dateien nur auf Vertraulichkeitsbezeichnungen und Inhaltsprüfungswarnungen von Microsoft Information Protection von diesem Mandanten**

      Begrenzt das Scannen auf Kennzeichnungen und Warnungen, die in Ihrer eigenen Organisation erstellt wurden. Kennzeichnungen, die von externen Mandanten angewendet werden, werden ignoriert.

1. Wählen Sie **Speichern** aus, um die Einstellungen zu übernehmen.

Sie haben Defender for Cloud Apps aktiviert, um Dateien auf Vertraulichkeitsbezeichnungen von Microsoft Purview zu erkennen und zu scannen.

## Aufgabe 8 - Erstellen einer Dateirichtlinie zur automatischen Kennzeichnung extern freigegebener Dateien

Da die Kennzeichnungsprüfung nun aktiviert ist, erstellen Sie eine Dateirichtlinie, die eine allgemeine Vertraulichkeitsbezeichnung auf alle neuen Dateien anwendet, die außerhalb Ihres Unternehmens freigegeben werden.

1. Navigieren Sie in **Microsoft Defender** zu **Cloud Apps** > **Richtlinien** > **Richtlinienverwaltung**.

1. Wählen Sie die Registerkarte **Informationsschutz** und wählen Sie dann **Richtlinie erstellen** > **Dateirichtlinie**.

    ![Screenshot, der zeigt, wohin Sie navigieren müssen, um eine Dateirichtlinie in Microsoft Defender zu erstellen.](../Media/file-policy-defender.png)

1. Konfigurieren Sie auf der Seite **Datei-Richtlinie erstellen**:

   - **Richtlinienname**: `Auto-label externally shared files`

   - **Schweregrad der Richtlinie**: **Niedrig**

   - **Kategorie**: **DLP**

   - Im Abschnitt **Dateien, die auf alle der folgenden Punkte zutreffen**:

      - Für den ersten Filter konfigurieren Sie die Dropdowns so: **Zugriffsstufe ist gleich extern**

      - Für den zweiten Filter konfigurieren Sie die Dropdowns zu: **Letzte Änderung nach (Datum)** und verwenden Sie das heutige Datum

          ![Screenshot zeigt die Filtereinstellungen in Defender.](../Media/configure-file-policy-filter.png)

   - Erweitern Sie unter **Governance-Aktionen** **Microsoft OneDrive for Business**:

      - Aktivieren Sie das Kontrollkästchen für **Vertraulichkeitsbezeichnung anwenden**

      - Wählen Sie in der Auswahlliste **Allgemein-Jeder (ohne Einschränkung)**

   - Wiederholen Sie den gleichen Vorgang für **Microsoft SharePoint Online**

      - Aktivieren Sie das Kontrollkästchen für **Vertraulichkeitsbezeichnung anwenden**

      - Wählen Sie **Allgemein-Jeder (ohne Einschränkung)** aus der Dropdown-Liste

1. Wählen Sie **Erstellen**, um die Erstellung der Dateirichtlinie zu beenden.

Sie haben eine Dateirichtlinie erstellt, die eine allgemeine Vertraulichkeitsbezeichnung auf extern in SharePoint und OneDrive freigegebene Dateien anwendet. Sobald eine passende Datei erkannt wird, wendet Defender for Cloud Apps die Kennzeichnung automatisch an.
