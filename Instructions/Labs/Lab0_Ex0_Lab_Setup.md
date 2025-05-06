---
lab:
  title: Aufbau der Übung - Bereiten Sie Ihre Übungsumgebung für die Verwaltung vor
  module: Lab setup
---

## WWL-Mandanten – Nutzungsbedingungen

Wenn Ihnen im Rahmen einer Präsenzschulung ein Mandant zugewiesen worden ist, steht dieser für Praxislabs innerhalb der Präsenzschulung zur Verfügung.

Mandanten sollten nicht für Zwecke außerhalb von Praxislabs freigegeben oder verwendet werden. Der in diesem Kurs verwendete Mandant ist ein Testmandant; er kann nach Abschluss des Kurses nicht verwendet oder erreicht werden und ist nicht für Erweiterungen geeignet.

Mandanten dürfen nicht in ein kostenpflichtiges Abonnement konvertiert werden. Die im Rahmen dieses Kurses erworbenen Mandanten verbleiben im Eigentum der Microsoft Corporation, und wir behalten uns das Recht vor, jederzeit auf Mandanten zuzugreifen und diese zurückzuziehen.

# Aufbau der Übung - Bereiten Sie Ihre Übungsumgebung für die Verwaltung vor

In dieser Übung konfigurieren Sie Ihre Umgebung und bereiten sie für Verwaltungsaufgaben vor. Sie aktivieren die erforderlichen Funktionen, legen die administrativen Berechtigungen fest und sorgen für die richtige Konfiguration der wichtigsten Elemente.

**Aufgaben:**

1. Aktivieren der Überwachung im Microsoft Purview-Portal
1. Festlegen von Benutzerkennwörtern für Lab-Übungen
1. Aktivieren des Geräte-Onboardings
1. Aktivieren von Insider-Risikoanalysen

## Aufgabe 1 - Aktivieren Sie Audit im Microsoft Purview-Portal

In dieser Aufgabe aktivieren Sie die Überwachung im Microsoft Purview-Portal, um Portalaktivitäten zu überwachen.

1. Sie sollten weiterhin bei Client 1 VM (SC-401-CL1) im **SC-401-CL1\admin**-Konto angemeldet sein und bei Microsoft 365 mit dem MOD-Administrator-Konto angemeldet sein.

1. Öffnen Sie ein erweitertes Terminal-Fenster, indem Sie mit der rechten Maustaste auf die Schaltfläche Windows klicken und dann **Terminal (Admin)** wählen.

1. Führen Sie das Cmdlet **Install Module** im Terminalfenster aus, um die neueste **Exchange Online PowerShell**-Modulversion zu installieren:

    ```powershell
    Install-Module ExchangeOnlineManagement
    ```

1. Bestätigen Sie den Prompt des NuGet-Anbieters, indem Sie **Y** für Ja eingeben und **Eingabe** drücken.

1. Bestätigen Sie den Sicherheitsdialog „Nicht vertrauenswürdiges Repository" mit **Y** für Ja und drücken Sie die **Eingabetaste**.  Dieser Vorgang nimmt einige Zeit in Anspruch.

1. Führen Sie das Cmdlet **Set-ExecutionPolicy** aus, um Ihre Ausführungsrichtlinie zu ändern, und drücken Sie **Enter**.

    ```powershell
    Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
    ```

1. Schließen Sie das PowerShell-Fenster.

1. Öffnen Sie ein normales (nicht übergeordnetes) PowerShell-Fenster, indem Sie mit der rechten Maustaste auf die Schaltfläche Windows klicken und **Terminal** wählen.

1. Führen Sie das Cmdlet **Connect-ExchangeOnline** aus, um das Exchange Online PowerShell-Modul zu verwenden und eine Verbindung zu Ihrem Mandanten herzustellen:

    ```powershell
    Connect-ExchangeOnline
    ```

1. Wenn das Fenster **Anmelden** angezeigt wird, melden Sie sich als `admin@WWLxZZZZZZ.onmicrosoft.com` an (wobei ZZZZZZ Ihre eindeutige Mandanten-ID ist, die Sie von Ihrem Provider für die Übung bereitgestellt haben). Das Passwort der administrierenden Person sollte von Ihrem Lab-Hosting-Anbieter bereitgestellt werden.

1. Um zu überprüfen, ob Audit aktiviert ist, führen Sie das Cmdlet **Get-AdminAuditLogConfig** aus:

    ```powershell
    Get-AdminAuditLogConfig | FL UnifiedAuditLogIngestionEnabled
    ```

1. Wenn _UnifiedAuditLogIngestionEnabled_ den Wert false liefert, ist Audit deaktiviert.

1. Um das Überwachungsprotokoll zu aktivieren, führen Sie das Cmdlet **Set-AdminAuditLogConfig** aus und legen Sie **UnifiedAuditLogIngestionEnabled** auf _true_ fest:

    ```powershell
    Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $true
    ```

1. Um zu überprüfen, ob Audit aktiviert ist, führen Sie das Cmdlet **Get-AdminAuditLogConfig** erneut aus:

    ```powershell
    Get-AdminAuditLogConfig | FL UnifiedAuditLogIngestionEnabled
    ```

1. _UnifiedAuditLogIngestionEnabled_ sollte _true_ zurückgeben, damit man weiß, dass Audit aktiviert ist.

<!---

1. In Microsoft Edge, navigate to the Microsoft Purview portal, `https://purview.microsoft.com`, and log in.

1. A message about the new Microsoft Purview portal will appear on the screen. Select the option to agree with the terms of data flow disclosure and the privacy statement, then select **Try now**.

    ![Screenshot showing the Welcome to the new Microsoft Purview portal screen.](../Media/welcome-purview-portal.png)

1. Select **Solutions** from the left sidebar, then select **Audit**.

1. On the **Search** page, select the **Start recording user and admin activity** bar to enable audit logging.

    ![Screenshot showing the Start recording user and admin activity button.](../Media/enable-audit-button.png)

1. Once you select this option, the blue bar should disappear from this page.

-->

## Aufgabe 2 - Festlegen von Benutzerkennwörtern für Lab-Übungen

In dieser Aufgabe legen Sie die Passwörter für die Benutzenden fest, die für die Übungen benötigt werden.

1. Melden Sie sich beim virtuellen Client 1 (SC-401-CL1) im **SC-401-CL1\admin** Konto an. Das Passwort sollte von Ihrem Provider für die Übung bereitgestellt werden.

1. Öffnen Sie **Microsoft Edge** und navigieren Sie zu **`https://admin.microsoft.com`**, um sich im Microsoft 365-Administrationszentrum als MOD-Administrator anzumelden, `admin@WWLxZZZZZZ.onmicrosoft.com` (wobei ZZZZZZ Ihre eindeutige Mandanten-ID ist, die von Ihrem Anbieter des Übungs-Hostings bereitgestellt wird).

1. Erweitern Sie im linken Navigationsbereich **Benutzende** und wählen Sie dann **Aktive Benutzende**.

1. Aktiviere das Kontrollkästchen links von **Joni Sherman**, **Lynne Robbins** und **Megan Bowen**.

   Diese Konten werden während der gesamten Lab-Übungen verwendet.

   ![Screenshot der Benutzenden-Konten, die zurückgesetzt werden müssen.](../Media/user-accounts.png)

1. Wählen Sie die Schaltfläche **Passwort zurücksetzen** in der oberen Navigation, um alle drei Passwörter zurückzusetzen.

   ![Der Screenshot zeigt die Schaltfläche „Kennwort zurücksetzen“ im Microsoft 365 Admin Center.](../Media/reset-password-button.png)

1. Vergewissern Sie sich auf der rechten Flyout-Seite **Passwort zurücksetzen**, dass beide Kontrollkästchen nicht aktiviert sind.

   Dadurch wird sichergestellt, dass Sie für die drei Benutzenden, die für die Übungen verwendet werden, ein Passwort auswählen können und dass diese Passwörter bei der ersten Anmeldung nicht zurückgesetzt werden müssen.

1. Geben Sie in das Feld **Passwort** ein Passwort ein, das Sie sich merken können, um die Passwörter der Benutzenden zurückzusetzen, die in zukünftigen Übungen verwendet werden sollen.

1. Wählen Sie unten auf der Flyout-Seite **Passwort zurücksetzen** die Schaltfläche **Passwort zurücksetzen**.

1. Auf der Seite **Passwörter wurden zurückgesetzt** sollten Sie die drei Benutzenden-Konten sehen, die zurückgesetzt worden sind. Wählen Sie unten auf dieser Flyout-Seite **Schließen**.

Sie haben die Passwörter für Lab-Übungen erfolgreich zurückgesetzt.

## Aufgabe 3 - Aktivieren der Geräteeinbindung

In dieser Aufgabe aktivieren Sie die Geräteeinbindung für Ihr Unternehmen.

1. Sie sollten weiterhin bei Client 1 VM (SC-401-CL1) im **SC-401-CL1\admin**-Konto angemeldet sein und als MOD-Administrator in Microsoft 365 angemeldet sein.

1. Navigieren Sie in **Microsoft Edge** zu **`https://purview.microsoft.com`**, um sich bei Microsoft Purview anzumelden, und wählen Sie dann **Einstellungen** in der linken Seitenleiste.

1. Erweitern Sie in der linken Seitenleiste **Geräteeinbindung** und wählen Sie dann **Geräte**.

1. Wählen Sie auf der Seite **Geräte** die Option **Geräteeinbindung einschalten** und wählen Sie dann **Ok**, um die Geräteeinbindung zu aktivieren.

1. Wenn Sie dazu aufgefordert werden, wählen Sie **OK**, um zu bestätigen, dass die Überwachung des Geräts aktiviert ist.

Sie haben nun die Geräteeinbindung aktiviert und können damit beginnen, Geräte einzubinden, die mit Endpoint DLP-Richtlinien geschützt werden sollen. Die Aktivierung der Funktion kann bis zu 30 Minuten dauern.

## Aufgabe 4 - Aktivierung der Analyse von Insiderrisiken

In dieser Aufgabe aktivieren Sie die Analysen für das Insider-Risikomanagement.

1. Sie sollten weiterhin bei Client 1 VM (SC-401-CL1) im **SC-401-CL1\admin**-Konto angemeldet sein und als MOD-Administrator in Microsoft Purview angemeldet sein.

1. Navigieren Sie in Microsoft Purview zu **Einstellungen** > **Insider-Risikomanagement** > **Analysen**.

1. Schalten Sie **Analysen** auf **Ein** und wählen Sie dann **Speichern**.

Sie haben die Analysen für das Insider-Risikomanagement aktiviert.

## Aufgabe 5 - Initialisieren von Microsoft Defender XDR

Bei dieser Aufgabe öffnen Sie Microsoft Defender und warten, bis Microsoft Defender XDR die Initialisierung beendet.

1. Sie sollten weiterhin bei Client 1 VM (SC-401-CL1) im **SC-401-CL1\admin**-Konto angemeldet sein und als MOD-Administrator in Microsoft Purview angemeldet sein.

1. Navigieren Sie in **Microsoft Edge** zu **`https://security.microsoft.com/`**, um Microsoft Defender zu öffnen.

1. Wählen Sie im Navigationsbereich **Untersuchung & Reaktion** > **Incidents & Warnungen** > **Incidents**.

1. Es wird eine Meldung angezeigt, dass Microsoft Defender XDR vorbereitet wird. Dieser Vorgang läuft automatisch ab und kann einige Minuten dauern.

   ![Screenshot, der zeigt, wie Microsoft Defender XDR in das System integriert wird.](../Media/enable-defender-xdr.png)

Microsoft Defender XDR wird gerade initialisiert. Sie können mit anderen Aufgaben fortfahren, während das Einrichten beendet wird.
