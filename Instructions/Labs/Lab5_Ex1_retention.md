---
lab:
  title: Übung 1 - Konfigurieren von Richtlinien zur Aufbewahrung
  module: Module 5 - Implement and manage retention
---

## WWL-Mandanten – Nutzungsbedingungen

Wenn Ihnen im Rahmen einer Präsenzschulung ein Mandant zugewiesen worden ist, steht dieser für Praxislabs innerhalb der Präsenzschulung zur Verfügung.

Mandanten sollten nicht für Zwecke außerhalb von Praxislabs freigegeben oder verwendet werden. Der in diesem Kurs verwendete Mandant ist ein Testmandant; er kann nach Abschluss des Kurses nicht verwendet oder erreicht werden und ist nicht für Erweiterungen geeignet.

Mandanten dürfen nicht in ein kostenpflichtiges Abonnement konvertiert werden. Die im Rahmen dieses Kurses erworbenen Mandanten verbleiben im Eigentum der Microsoft Corporation, und wir behalten uns das Recht vor, jederzeit auf Mandanten zuzugreifen und diese zurückzuziehen.

# Labor 5 - Übung 1 - Implementieren und Verwalten der Aufbewahrung

Sie sind Joni Sherman, ein Complianceadministrator bei Contoso Ltd. Das Unternehmen verschärft seine Datensicherheitsstrategie, um die Risiken im Zusammenhang mit Finanzdaten und privilegierter Kommunikation zu verringern. Sie wurden aufgefordert, Microsoft Purview-Aufbewahrungslösungen zu konfigurieren, die die Überwachungsbereitschaft unterstützen, unnötige Datenaufbewahrung einschränken und eine ordnungsgemäße Aufsicht für vertrauliche Kommunikationen gewährleisten.

**Aufgaben:**

1. Erstellen einer Kennzeichnung für die Aufbewahrung
1. Veröffentlichen einer Kennzeichnung für die Aufbewahrung
1. Erstellen einer Richtlinie zur automatischen Anwendung von Bezeichnungsrichtlinien für die Aufbewahrung
1. Erstellen Sie eine statische Richtlinie zur Aufbewahrung
1. Erstellen eines adaptiven Bereichs
1. Erstellen einer adaptiven Richtlinie zur Aufbewahrung
1. Wiedererstellen von SharePoint-Inhalten

## Aufgabe 1 - Erstellen einer Kennzeichnung für die Aufbewahrung

In dieser Aufgabe erstellen Sie eine Kennzeichnung für sensible Finanzdaten, die zu Prüfungs- und Untersuchungszwecken aufbewahrt werden müssen.

1. Melden Sie sich bei Client 1 VM (SC-401-CL1) im **SC-401-cl1\admin** Konto an.

1. Navigieren Sie in Microsoft Edge zu `https://purview.microsoft.com` und melden Sie sich beim Microsoft Purview-Portal als **Joni Sherman**`JoniS@WWLxZZZZZZ.onmicrosoft.com` an (wobei ZZZZZZ Ihre eindeutige Mandanten-ID ist, die Sie von Ihrem Anbieter für das Hosting von Übungen bereitgestellt haben). Das Passwort von Joni wurde in einer früheren Übung festgelegt.

1. Navigieren Sie zu **Lösungen** > **Verwaltung des Datenlebenszyklus** > **Kennzeichnungen für die Aufbewahrung**.

1. Auf der Seite **Kennzeichnungen** wählen Sie **Kennzeichnung erstellen**.

1. Geben Sie auf der Seite **Benennen Sie Ihre Kennzeichnung für die Speicherung** ein:

   - **Name**: `Sensitive Financial Records`
   - **Beschreibung für Benutzende**: `Use for financial files with sensitive data that must be retained for audit or security purposes.`
   - **Beschreibung für Administratoren**: `Retains high-impact financial data for 5 years to support audits and security investigations.`

1. Wählen Sie **Weiter** aus.

1. Wählen Sie auf der Seite **Einstellungen für Kennzeichnungen festlegen** die Option **Elemente für immer oder für einen bestimmten Zeitraum aufbewahren**, und wählen Sie dann **Weiter**.

1. Stellen Sie auf der Seite **Zeitraum definieren** sicher, dass diese Werte für die Eingabe der Aufbewahrungsfrist konfiguriert sind:

    - **Wie lange ist der Zeitraum?**: 5 Jahre
    - **Wann soll der Zeitraum beginnen?**: Wann wurden die Elemente geändert?

1. Wählen Sie **Weiter** aus.

1. Wählen Sie auf der Seite **Was geschieht nach der Aufbewahrungsfrist** die Option **Elemente automatisch löschen** und wählen Sie dann **Weiter**.

1. Wählen Sie auf der Seite **Prüfen und beenden** die Option **Bezeichnung erstellen** aus.

1. Wählen Sie auf der Seite **Ihre Kennzeichnung für die Vorratsspeicherung ist erstellt** die Option **Nichts tun** und dann **Fertig**.

Sie haben eine Kennzeichnung für die Aufbewahrung erstellt, die Finanzinhalte fünf Jahre lang aufbewahrt und danach löscht, um das Datenrisiko zu verringern.

## Aufgabe 2 - Veröffentlichen einer Kennzeichnung für die Aufbewahrung

In dieser Aufgabe veröffentlichen Sie die Kennzeichnung für die Aufbewahrung, damit die Benutzenden sie in Microsoft 365-Diensten wie Exchange, SharePoint und OneDrive anwenden können.

1. Navigieren Sie in Microsoft Purview zu **Lösungen** > **Verwaltung des Datenlebenszyklus** > **Aufbewahrungskennzeichnungen**.

1. Aktivieren Sie das Kontrollkästchen neben der Kennzeichnung **Sensitive Financial Records** und wählen Sie dann das Symbol **Etiketten veröffentlichen** (![Etiketten veröffentlichen Symbol](../Media/publish-labels-icon.png)), um diese Kennzeichnung für die Aufbewahrung zu veröffentlichen.

1. Überprüfen Sie auf der Seite **Wählen Sie die zu veröffentlichenden Kennzeichnungen**, ob die Kennzeichnung **Vertraulichkeitsbezeichnung** ausgewählt ist, und wählen Sie dann **Weiter**.

1. Wählen Sie auf der Seite **Richtlinienbereich** **Weiter** aus.

1. Wählen Sie auf der Seite **Den Typ der zu erstellenden Aufbewahrungsrichtlinie auswählen** die Option **Statisch** und wählen Sie dann **Weiter**.

1. Auf der Seite **Wählen Sie, wo die Kennzeichnungen veröffentlicht werden sollen** wählen Sie **Lassen Sie mich bestimmte Standorte auswählen** und wählen Sie:

    - Exchange-Postfächer
    - Klassische SharePoint- und Kommunikationswebsites
    - OneDrive Konten
    - Wählen Sie alle anderen Standorte ab

1. Wählen Sie **Weiter** aus.

1. Auf der Seite **Benennen Sie Ihre Richtlinie** eingeben:

    - **Name**: `Sensitive Financial Data Retention`
    - **Beschreibung:** `Makes the 'Sensitive Financial Records' label available to users in Exchange, SharePoint, and OneDrive.`

1. Wählen Sie **Weiter** aus.

1. Wählen Sie auf der Seite **Beenden** die Option **Absenden**.  

1. Wählen Sie auf der Seite **Ihre Kennzeichnung für die Vorratsspeicherung wurde veröffentlicht** die Option **Fertig**.

Sie haben die Kennzeichnung für die Datenaufbewahrung veröffentlicht und sie für die Anwendung durch die Benutzenden in wichtigen Microsoft 365-Diensten verfügbar gemacht.

## Aufgabe 3 - Erstellen einer Richtlinie zur automatischen Anwendung von Bezeichnungsrichtlinien für die Aufbewahrung

In dieser Aufgabe konfigurieren Sie eine Richtlinie, die automatisch eine Kennzeichnung für die Aufbewahrung von Inhalten anwendet, die persönliche Finanzdaten enthalten.

1. Navigieren Sie in Microsoft Purview zu **Lösungen** > **Datenlebenszyklus-Verwaltung** > **Richtlinien** > **Bezeichnungsrichtlinien**.

1. Wählen Sie auf der Seite **Bezeichnungsrichtlinien** die Option **Automatisches Anwenden einer Kennzeichnung**, um die Konfiguration der Kennzeichnung zu starten.

1. Auf der Seite **Erste Schritte**, geben Sie ein:

   - **Name**: `Auto-apply Personal Financial PII`
   - **Beschreibung:** `Applies this label to personal financial data to help meet audit and investigation requirements. Retains content for 3 years.`

1. Wählen Sie **Weiter** aus.

1. Wählen Sie auf der Seite **Wählen Sie den Typ des Inhalts, auf den Sie diese Kennzeichnung anwenden möchten** die Option **Kennzeichnung auf Inhalte anwenden, die vertrauliche Informationen enthalten**, und wählen Sie dann **Weiter**.

1. Wählen Sie auf der Seite **Inhalt, der sensible Daten enthält** die Kategorie **Finanzen**, dann die Verordnung **U.S. Gramm-Leach-Bliley Act (GLBA)** und anschließend **Weiter**.

1. Wählen Sie auf der Seite **Definieren Sie Inhalte, die sensible Informationen enthalten**, **Weiter**.

1. Wählen Sie auf der Seite **Richtlinienbereich** **Weiter** aus.

1. Auf der Seite **Wählen Sie den Typ der zu erstellenden Aufbewahrungsrichtlinie** wählen Sie **Statisch**.

1. Auf der Seite **Wählen Sie, wo die Kennzeichnungen veröffentlicht werden sollen** wählen Sie **Lassen Sie mich bestimmte Standorte auswählen** und wählen Sie:

    - Exchange-Postfächer
    - Klassische SharePoint- und Kommunikationswebsites
    - OneDrive Konten
    - Wählen Sie alle anderen Standorte ab

1. Auf der Seite **Bezeichnung für automatische Anwendung auswählen** wählen Sie **Bezeichnung hinzufügen**.

1. Wählen Sie im Flyout **Wählen Sie eine Kennzeichnung** die Option **Persönliche finanzielle PII** und dann **Hinzufügen** aus.

1. Zurück auf der Seite **Wählen Sie eine Kennzeichnung, die automatisch angewendet werden soll**, wählen Sie **Weiter**.

1. Wählen Sie auf der Seite **Entscheiden Sie, ob Sie Ihre Richtlinie testen oder ausführen möchten** die Option **Testen Sie die Richtlinie, bevor Sie sie ausführen**, und wählen Sie dann **Weiter**.

1. Wählen Sie auf der Seite **Überprüfen und beenden** die Option **Senden** und dann **Erledigt** auf der Seite **Ihre Richtlinie zur automatischen Bezeichnung wurde erstellt**.

Sie haben eine Richtlinie zur automatischen Anwendung erstellt, die personenbezogene Finanzdaten identifiziert und automatisch eine Kennzeichnung zur Aufbewahrung anwendet.

## Aufgabe 4 - Erstellen einer statischen Richtlinie zur Aufbewahrung

In dieser Aufgabe erstellen Sie eine statische Richtlinie für die Aufbewahrung von Microsoft Teams-Inhalten, um langfristige Datenrisiken zu reduzieren.

1. Navigieren Sie in Microsoft Purview zu **Lösungen** > **Verwaltung des Datenlebenszyklus** > **Richtlinien** > **Richtlinien zur Aufbewahrung**.

1. Wählen Sie auf der Seite **Aufbewahrungsrichtlinien** die Option **Neue Aufbewahrungsrichtlinie**.

1. Auf der Seite **Adaptiven Richtlinienbereich benennen**, geben Sie Folgendes ein:

   - **Name**: `Teams Retention`
   - **Beschreibung:** `Retains Teams chats and channel messages for 3 years, then deletes them to reduce long-term data risk.`

1. Wählen Sie **Weiter** aus.

1. Wählen Sie auf der Seite **Richtlinienbereich** **Weiter** aus.

1. Wählen Sie auf der Seite **Typ der zu erstellenden Richtlinie auswählen**, wählen Sie **Statisch** und wählen Sie dann **Weiter**.

1. Aktivieren Sie auf der Seite **Wählen Sie Standorte, um die Richtlinie anzuwenden**:

   - Teams-Kanalnachrichten
   - Teams-Chats
   - Lassen Sie alle anderen Standorte deaktiviert.

1. Wählen Sie **Weiter** aus.

1. Stellen Sie auf der Seite **Entscheiden Sie, ob Sie Inhalte behalten, löschen oder beides** möchten, sicher, dass diese Werte für die Konfiguration der Speicherung festgelegt sind:

   - Wählen Sie **Elemente für einen bestimmten Zeitraum aufbewahren**.
   - Wählen Sie unter **Artikel für einen bestimmten Zeitraum aufbewahren** aus der Dropdownliste **Kunden**.
   - Ändern Sie das Feld Jahre in `3`
   - **Beginnen Sie die Aufbewahrungsfrist basierend auf**: Wann die Elemente zuletzt geändert wurden.
   - **Am Ende des Aufbewahrungszeitraums**: Elemente automatisch löschen.

1. Wählen Sie **Weiter** aus.

1. Wählen Sie auf der Seite **Überprüfen und beenden** die Option **Senden** und dann **Erledigt** auf der Seite **Sie haben erfolgreich eine Richtlinie zur Aufbewahrung erstellt**.

Sie haben eine statische Richtlinie zu konfiguriert, die Meldungen von Teams drei Jahre lang aufbewahrt, bevor sie automatisch gelöscht werden.

<!------ Commenting out until tenant bug issues are resolved
## Task 5 – Create an adaptive scope

In this task, you'll define an adaptive scope that targets Microsoft 365 groups associated with leadership and operations roles.

1. In Microsoft Purview, **Settings** > **Roles and scopes** > **Adaptive scopes**.

1. On the **Adaptive scopes** page select **+ Create scope**.

1. On the **Name your adaptive policy scope** page enter:

    - **Name**: `Leadership and Ops Groups`
    - **Description**: `Targets Leadership and Operations M365 groups with privileged access to sensitive data.`

1. Select **Next**.

1. On the **Assign admin unit** page select **Next**.

1. On the **What type of scope do you want to create?** page select **Users**, then select **Next**.

1. On the **Create the query to define users** page, in the **User attributes** section, ensure these values are selected for the user attribute configuration:

   - Select the **Attribute** dropdown then select **Department**
   - Leave the default **is equal to** value in the next field
   - Enter `Leadership` as the **Value**

1. Add a second attribute by selecting **+ Add attribute** on the **Create the query to define users** page. In the new field under the one we just configured, configure these values:

   - Select the dropdown for the query operator and update it from And to **Or**
   - Select the **Attribute** dropdown then select **Department**
   - Leave the default **is equal to** value in the next field
   - Enter `Operations` as the **Value**

1. Select **Next**.

1. On the **Review and finish** page select **Submit**.

1. Once your adaptive scope is created select **Done** on the **Your scope was created** page.

You've created an adaptive scope to support targeted retention for privileged groups in the organization.

## Task 6 – Create an adaptive retention policy

In this task, you'll use the adaptive scope you created to configure a retention policy for Microsoft 365 groups with sensitive responsibilities.

1. In Microsoft Purview, navigate to **Solutions** > **Data Lifecycle Management** > **Policies** >  **Retention policies**.

1. On the **Retention policies** page, select **+ New retention policy**.

1. On the **Name your retention policy** page enter:

    - **Name**: `Privileged Group Retention`
    - **Description**: `Retains content from Leadership and Operations groups for 5 years to support audit and investigation.`

1. Select **Next**.

1. On the **Policy Scope** page select **Next**.

1. On the **Choose the type of retention policy to create** page select **Adaptive** then select **Next**.

1. On the **Choose adaptive policy scopes and locations** page select **+ Add scopes**.

1. On the **Choose adaptive policy scopes** flyout panel select the checkbox for **Leadership and Ops Groups** then select **Add** at the bottom of the panel.

1. Back on the **Choose locations to apply the policy** enable:

    - Microsoft 365 Group mailboxes & sites
    - Leave all other locations disabled.

1. Select **Next**.

1. On the **Decide if you want to retain content, delete it, or both** page, ensure these values are set for the retention configuration:

   - Select **Retain items for a specific period**.
   - Under **Retain items for a specific period**, select **5 years** from the dropdown list
   - **Start the retention period based on**: When items were last modified
   - **At the end of the retention period**: Delete items automatically

1. Select **Next**.

1. On the **Review and finish** page select **Submit**.

1. Select **Done** once the policy is created.

You've created a retention policy that applies to content owned by privileged groups, retaining it for five years before deletion.
-->

## Aufgabe 5 – Wiederherstellen von SharePoint-Inhalten

In dieser Aufgabe simulieren Sie die Wiederherstellung eines gelöschten Dokuments von einer SharePoint-Website, um Ihre Wiederherstellungsoptionen zu überprüfen.

1. Melden Sie sich bei Client 1 VM (SC-401-CL1) im **SC-401-cl1\admin** Konto an.

1. Navigieren Sie in **Microsoft Edge** zu **`https://www.office.com`** und melden Sie sich bei Microsoft 365 als **Joni Sherman** an.

1. Wählen Sie auf der Zielseite von Microsoft Office 365 das App-Startfeld (das Symbol mit dem Gitter) in der oberen linken Ecke und wählen Sie dann **SharePoint** aus dem Untermenü.

   ![Der Screenshot zeigt, wo die Auslassungspunkte sind, um das Aktionsmenü anzuzeigen.](../Media/show-more-actions-sharepoint.png)

1. Suchen Sie auf der SharePoint Zielseite nach `Benefits` und wählen Sie dann **Vorteile @ Contoso** aus den Suchergebnissen.

1. Wählen Sie in der linken Seitenleiste **Dokumente**.

1. Aktivieren Sie auf der Seite **Dokumente** das Kontrollkästchen für **Vacation Policies.pptx** und wählen Sie dann **Löschen** in der Aktionsleiste.

1. Wählen Sie im Dialog **Löschen?** die Option **Löschen**.

1. Wählen Sie in der linken Seitenleiste **Papierkorb**.

1. Klicken Sie auf der Seite **Papierkorb** mit der rechten Maustaste auf **Vacation Policies.pptx** und wählen Sie dann **Wiederherstellen**.

1. Wählen Sie in der linken Seitenleiste **Dokumente** und beachten Sie, dass die Datei wiederhergestellt worden ist.

Sie haben erfolgreich ein gelöschtes Dokument von einer SharePoint- Website befreit.
