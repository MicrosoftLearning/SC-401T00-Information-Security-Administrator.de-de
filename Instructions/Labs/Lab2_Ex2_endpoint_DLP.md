---
lab:
  title: Übung 2 - Implementieren und Verwalten von Endpunkt-DLP
  module: Module 2 - Implement Data Loss Prevention
---

# Übung 2 - Übung 2 - Implementieren und Verwalten von Endpunkt-DLP

Joni Sherman, der neu eingestellte Informationssicherheitsadministrator bei Contoso Ltd., wurde gebeten, die DLP- Kontrollen auf den Geräten des Unternehmens zu verstärken. Einige mitarbeitende Personen haben sensible Kundschaftsinformationen auf USB-Laufwerke kopiert, was das Risiko der Datenpreisgabe erhöht. In dieser Übung wird Joni eine DLP-Richtlinie für Endpunkte konfigurieren, um diese Übertragungen zu blockieren.

**Aufgaben:**

1. Einbinden eines Geräts für Endpunkt-DLP
1. Erstellen einer Endpunkt-DLP-Richtlinie
1. Konfigurieren von DLP-Einstellungen für Endpunkte
1. Konfigurieren der Microsoft Purview-Erweiterung

## Aufgabe 1 - Einbinden eines Geräts für Endpunkt-DLP

In dieser Aufgabe werden Sie ein Windows 11-Gerät einbinden, damit es für den Schutz durch Endpunkt-DLP-Richtlinien bereit ist.

1. Melden Sie sich bei **Client 2 VM (SC-401-CL2)** im **SC-401-cl1\admin** Konto an.

1. Öffnen Sie Microsoft Edge, navigieren Sie zu **`https://purview.microsoft.com`** und melden Sie sich beim Microsoft Purview-Portal als **Joni Sherman** an. Melden Sie sich als `JoniS@WWLxZZZZZZ.onmicrosoft.com` an (wobei ZZZZZZ Ihre eindeutige Mandanten-ID ist, die Sie von Ihrem Hosting-Anbieter für die Übung bereitgestellt haben). Das Passwort von Joni wurde in einer früheren Übung festgelegt.

1. Wählen Sie **Einstellungen** in der linken Seitenleiste.

1. Erweitern Sie in der linken Seitenleiste **Geräteeinbindung**, und wählen Sie dann **Einbindung**.

1. Wählen Sie auf der Seite **Einbindung** im Dropdownmenü **Methode für die Bereitstellung** die Option **Lokales Skript (für bis zu 10 Geräte)** und wählen Sie **Paket herunterladen**.

1. Bewegen Sie den Mauszeiger im Dialog **Downloads** über den Download und wählen Sie dann das Symbol des Ordners aus, um **Im Ordner anzeigen**.

1. Entpacken Sie die Zip-Datei auf den **Desktop** des SC-401-CL1. Sie sollten ein Skript mit dem Namen **DeviceComplianceLocalOnboardingScript.cmd** sehen.

1. Klicken Sie auf dem Desktop mit der rechten Maustaste auf die Datei **DeviceComplianceLocalOnboardingScript.cmd**, die Sie gerade extrahiert haben, und wählen Sie **Weitere Optionen anzeigen**, dann **Eigenschaften**.

1. Wählen Sie unten auf der Registerkarte **Allgemein** des Fensters Eigenschaften im Abschnitt **Sicherheit** die Option **Entsperren** und dann **OK**, um diese Einstellung zu speichern.

1. Klicken Sie auf dem Desktop mit der rechten Maustaste auf **DeviceComplianceLocalOnboardingScript.cmd** und wählen Sie dann **Als Administrator ausführen**. Wählen Sie im Dialog **Benutzerkontensteuerung** die Option **Ja**.

1. Im **Command Prompt** Bildschirm geben Sie **Y** ein, um zu bestätigen, und drücken Sie dann Enter.

1. Wenn das Skript abgeschlossen ist, erhalten Sie eine Erfolgsmeldung und die Aufforderung, **eine beliebige Taste zu drücken, um fortzufahren**. Drücken Sie eine beliebige Taste, um das Befehlszeilenfenster zu schließen. Es kann eine Minute dauern, bis das Einbinden abgeschlossen ist.

1. Öffnen Sie das Startmenü und suchen Sie nach `Access work or school`. Wählen Sie **Zugriff auf Arbeit oder Schule** unter **Beste Übereinstimmung**.

1. Im Fenster **Zugang Arbeit oder Schule** für **Arbeits- oder Schulkonto hinzufügen** wählen Sie **Verbinden**.

1. Wählen Sie im Dialogfeld **Arbeits- oder Schulkonto einrichten** den Link **Dieses Gerät mit Microsoft Entra ID verknüpfen** und melden Sie sich als **Joni Sherman**`JoniS@WWLxZZZZZZ.onmicrosoft.com` an (wobei ZZZZZZ Ihre eindeutige Mandanten-ID ist, die von Ihrem Anbieter für das Hosting von Übungen bereitgestellt wird). Das Passwort von Joni wurde in einer früheren Übung festgelegt.

1. Im Dialogfeld **Sicherstellen, dass dies Ihre Organisation ist** überprüfen Sie die URL des Mandanten und wählen Sie **Beitreten**.  

1. Sobald dein Gerät verbunden ist, wähle **Fertig** auf der Seite **Du bist fertig!** Bildschirm.

1. Starten Sie Client 2 VM (SC-401-CL2) neu.

1. Melden Sie sich wieder bei Client 1 VM (SC-401-CL1) an.

1. Das Microsoft Purview-Fenster sollte noch auf der Seite **Geräte** geöffnet sein. Aktualisieren Sie diese Seite und überprüfen Sie, ob das Gerät erfolgreich eingebunden wurde.

Sie haben das Gerät erfolgreich eingebunden und mit Microsoft Entra ID verbunden. Sie kann nun durch DLP-Richtlinien für Endpunkte geschützt werden.

## Aufgabe 2 - Erstellen einer Endpunkt-DLP-Richtlinie

In dieser Aufgabe erstellen Sie eine DLP-Richtlinie, die die Übertragung sensibler Daten auf USB-Laufwerke blockiert. Dadurch wird das Risiko verringert, dass Daten ohne Berechtigung außer Haus gebracht werden.

1. Melden Sie sich bei Client 1 VM (SC-401-CL1) im SC-401-cl1\admin-Konto an.

1. Sie sollten sich immer noch auf der Seite **Geräte** im Microsoft Purview-Portal befinden und als Joni Sherman angemeldet sein.

1. Wählen Sie im Microsoft Purview-Portal **Lösungen** > **Vermeidung von Datenverlusten**.

1. Wählen Sie im linken Bereich **Richtlinien** und wählen Sie dann **+ Richtlinie erstellen**.

1. Wählen Sie auf der Seite **Starten Sie mit einer Vorlage oder erstellen Sie eine benutzerdefinierte Richtlinie** die Optionen **Benutzerdefiniert** und **Benutzerdefinierte Richtlinie**, und wählen Sie dann **Weiter**.

1. Geben Sie auf der Seite **Benennen Sie Ihre Richtlinie** ein:

    - **Name**: `Block USB transfers`
    - **Beschreibung:** `Prevent transferring sensitive data to USB devices.`

1. Wählen Sie auf der Seite **Admineinheiten zuweisen** **Weiter**.

1. Vergewissern Sie sich, dass auf der Seite **Standorte auswählen, um die Richtlinie anzuwenden** nur der Standort **Geräte** ausgewählt ist. Wenn ein anderer Standort ausgewählt ist, stellen Sie sicher, dass er abgewählt ist, und wählen Sie dann **Weiter**.

1. Wählen Sie auf der Seite **Richtlinieneinstellungen festlegen** die Option **Erstellte oder angepasste erweiterte DLP-Regeln** und wählen Sie dann **Weiter**.

1. Wählen Sie auf der Seite **Erweiterte DLP-Regeln anpassen** die Option **+ Regel erstellen**.

1. Geben Sie auf der Seite **Regel erstellen** ein:

    - **Name**: `USB transfer rule`
    - **Beschreibung:** `Block USB transfers of sensitive data.`

1. Unter **Bedingungen** wählen Sie **+ Bedingung hinzufügen** und dann **Inhalt enthält**.

1. In dem neuen Abschnitt **Inhalt enthält**:
    - Wählen Sie **Hinzufügen** > **Typen vertraulicher Informationen**.
    - Suchen Sie auf der Seite **Typen vertraulicher Informationen** nach diesen Typen vertraulicher Informationen:
       - `Credit Card Number`
       - `U.S. Social Security Number (SSN)`
       - `U.S. Driver's License Number`
       - `Contoso Employee IDs`

1. Wählen Sie unter **Aktionen** die Option **+ Eine Aktion hinzufügen** > **Aktivitäten auf Geräten überprüfen oder einschränken**.

1. Im neuen Abschnitt **Aktivitäten auf Geräten überwachen oder einschränken**:
    - Stellen Sie sicher, dass im Abschnitt **Datei-Aktivitäten für alle Apps** die Option **Kopieren auf einen USB-Wechseldatenträger** ausgewählt ist.
    - Wählen Sie das Dropdown-Menü links neben **Kopieren auf ein entfernbares USB-Gerät**, um die Aktion von **Nur prüfen** auf **Sperren** zu ändern.

1. Unter **Benutzerbenachrichtigungen**:
    - Schalten Sie **Ein** für **Benutzen Sie Benachrichtigungen, um Ihre Benutzenden zu informieren und sie über die richtige Verwendung sensibler Daten aufzuklären.**.
    - Aktivieren Sie das Kontrollkästchen, um **Benutzenden eine Benachrichtigung über Richtlinien-Tipps anzuzeigen, wenn eine Aktivität eingeschränkt ist**.

1. Wählen Sie **Speichern** am unteren Rand des Flyouts **Regel erstellen**.

1. Wählen Sie auf der Seite **Erweiterte DLP-Regeln anpassen** die Option **Weiter**.

1. Wählen Sie auf der Seite **Richtlinienmodus** die Option **Richtlinie im Simulationsmodus ausführen**.
   - Aktivieren Sie das Kontrollkästchen, um **Tipps zu Richtlinien im Simulationsmodus anzuzeigen**.
   - Aktivieren Sie auch das Kontrollkästchen **Die Richtlinie einschalten, wenn sie nicht innerhalb von fünfzehn Tagen nach der Simulation bearbeitet wird**.

1. Wählen Sie **Weiter** aus.

1. Auf der Seite **Überprüfen und beenden** überprüfen Sie Ihre Richtlinieneinstellungen und wählen Sie dann **Senden**, um die Richtlinie zu erstellen.

1. Sobald die Richtlinie erstellt ist, wählen Sie **Erledigt** auf der Seite **Neue Richtlinie erstellt**.

Sie haben erfolgreich eine DLP-Richtlinie im Simulationsmodus erstellt, die USB-Übertragungen von sensiblen Daten blockiert. Wenn die Richtlinie nicht bearbeitet wird, wird sie nach 15 Tagen automatisch aktiviert.

## Aufgabe 3 - Konfigurieren der Endpunkt-DLP-Einstellungen

In dieser Aufgabe nehmen Sie eine Feinabstimmung der Endpunkt-DLP-Einstellungen vor, indem Sie einen lokalen Ordner ausschließen, Browser-Einschränkungen festlegen und eine Cloud-Domäne blockieren.

1. Sie sollten weiterhin bei Client 1 VM (SC-401-CL1) im **SC-401-cl1\admin**-Konto angemeldet sein, und Sie sollten bei Microsoft 365 als **Joni Sherman** angemeldet sein.

1. Wählen Sie in Microsoft Purview im linken Navigationsbereich **Einstellungen** > **Verhinderung von Datenverlusten**.

1. Die Seite **Einstellungen zur Verhinderung von Datenverlusten** sollte sich zu den **Endpunkt-DLP-Einstellungen** öffnen.

1. Erweitern Sie auf der Seite **Endpunkt-DLP-Einstellungen** die Option **Dateipfadausschlüsse für Windows** und wählen Sie dann **+ Dateipfadausschluss hinzufügen**.

1. Geben Sie auf der Flyout-Seite **Diese Dateipfade von Windows-Geräten ausschließen** im Feld **Dateipfadausschluss** `C:\FilePathExclusionTest` ein und wählen Sie dann die Schaltfläche **+** auf der rechten Seite. Wählen Sie **Speichern**, um diesen Eintrag zu speichern.

1. Erweitern Sie auf der Seite **Endpunkt-DLP-Einstellungen** die Option **Browser- und Domäneneinschränkungen für sensible Daten** und wählen Sie **+ Unerlaubte Browser hinzufügen oder bearbeiten**.

1. Auf der Flyout-Seite **Unerlaubte Browser hinzufügen** aktivieren Sie das Kontrollkästchen für **Google Chrome** und wählen Sie **Speichern**.

1. Wählen Sie auf der Seite **Endpunkt-DLP-Einstellungen** das Dropdown-Menü für **Domänen der Dienste** und ändern Sie es von **Aus** auf **Blockieren**.

1. Im Dialog **Update Cloud App Modus** wählen Sie **Ja**, um den Blockmodus zu aktivieren.

1. Wählen Sie unter **Service-Domänen** die Option **+ Clouddienst-Domäne hinzufügen**.

1. Auf der Flyout-Seite **Clouddienst-Domäne hinzufügen** im Feld **Domäne** geben Sie `dropbox.com` ein und wählen dann das Symbol **+** (Plus), um den Pfad hinzuzufügen. Wählen Sie **Speichern**, um diese Einstellung zu speichern.

Sie haben benutzerdefinierte Endpunkt-DLP-Einstellungen angewendet, die das Verhalten Ihrer Richtlinie verfeinern, einschließlich Ausschlüssen, Browser-Einschränkungen und Blockierung des Zugriffs auf bestimmte Domänen.

## Aufgabe 4 - Konfigurieren der Microsoft Purview-Erweiterung

In dieser Aufgabe installieren Sie die Microsoft Purview-Erweiterung in Google Chrome, um das Verhalten der Endpunkt-DLP-Richtlinie in unterstützten Browsern zu testen.

1. Öffnen Sie den Edge-Browser über die Taskleiste.

1. Navigieren Sie zum Google Chrome-Download unter **`https://chrome.google.com`**.

1. Wählen Sie **Chrome herunterladen** und wählen Sie **Datei öffnen** aus der **Downloads** Benachrichtigung für **ChromeSetup.exe**.

1. Wählen Sie **Ja** im Dialog **Benutzerkontensteuerung**, um den Chrome-Browser zu installieren.

1. Wenn die Installation beendet ist, wählen Sie auf dem Bildschirm **In Chrome anmelden** **Nein danke** oder **Nicht anmelden**.

1. Wählen Sie **Überspringen** auf der Seite **Standardbrowser festlegen**.

1. Wenn sich das neu installierte Chrome-Browserfenster öffnet, navigieren Sie zur **Microsoft Purview-Erweiterung** im **Chrome-Webspeicher** unter:

   `https://chrome.google.com/webstore/detail/microsoft-purview-extensi/echcggldkblhodogklpincgchnpgcdco`

1. Vergewissern Sie sich, dass Sie sich auf der richtigen Erweiterungsseite befinden, und wählen Sie dann **Zu Chrome hinzufügen**.

1. Auf der Seite **Microsoft Purview-Erweiterung" hinzufügen?** Wählen Sie im Fenster **Erweiterung hinzufügen**.

1. Schließen Sie die Benachrichtigung, dass die Erweiterung zu Chrome hinzugefügt wird, und navigieren Sie dann zu **`chrome://extensions`**.

1. Überprüfen Sie, ob die **Microsoft Purview-Erweiterung** sichtbar und aktiviert ist.

1. Schließen Sie das Chrome-Browserfenster.

Sie haben Chrome erfolgreich installiert und die Microsoft Purview-Erweiterung hinzugefügt. Das Gerät unterstützt jetzt die Erzwingung von DLP-Richtlinien sowohl in Edge als auch in Chrome.
