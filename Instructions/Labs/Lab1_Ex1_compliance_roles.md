---
lab:
  title: Übung 1 - Verwalten von Konformitäts- und Sicherheitsrollen
  module: Module 1 - Implement Information Protection
---
## WWL-Mandanten – Nutzungsbedingungen

Wenn Ihnen im Rahmen einer Präsenzschulung ein Mandant zugewiesen worden ist, steht dieser für Praxislabs innerhalb der Präsenzschulung zur Verfügung.

Mandanten sollten nicht für Zwecke außerhalb von Praxislabs freigegeben oder verwendet werden. Der in diesem Kurs verwendete Mandant ist ein Testmandant; er kann nach Abschluss des Kurses nicht verwendet oder erreicht werden und ist nicht für Erweiterungen geeignet.

Mandanten dürfen nicht in ein kostenpflichtiges Abonnement konvertiert werden. Die im Rahmen dieses Kurses erworbenen Mandanten verbleiben im Eigentum der Microsoft Corporation, und wir behalten uns das Recht vor, jederzeit auf Mandanten zuzugreifen und diese zurückzuziehen.

# Übung 1 - Übung 1 - Verwalten von Konformitäts- und Sicherheitsrollen

Als kürzlich eingestellter Informationssicherheits-Administrator für Contoso Ltd. müssen Sie (Joni Sherman) sicherstellen, dass der neue Microsoft 365-Mandant verschiedene rechtliche und regulatorische Standards erfüllt. Contoso Ltd. expandiert, und Ihre Rolle ist entscheidend für die Beibehaltung der Konformität in allen Regionen des Unternehmens.

**Aufgaben:**

1. Zuweisung von Rollen für Konformität und Sicherheit
1. Erkunden des Microsoft Purview-Portals

## Aufgabe 1 - Zuweisung von Rollen zur Konformität und Sicherheit

In dieser Aufgabe weisen Sie Joni Sherman die Rolle Konformitätsadministrator zu.

1. Melden Sie sich beim virtuellen Client 1 (SC-401-CL1) mit dem **SC-401-CL1\admin** Konto an. Das Passwort sollte von Ihrem Provider für die Übung bereitgestellt werden.

1. Öffnen Sie **Microsoft Edge** und navigieren Sie zum Microsoft 365 Admin Center, `https://admin.microsoft.com`, und melden Sie sich als **MOD Administrator**, `admin@WWLxZZZZZZ.onmicrosoft.com`, an (wobei ZZZZZZ Ihre eindeutige Mandant-ID ist, die von Ihrem Anbieter für das Hosting von Übungen bereitgestellt wird). Das Passwort der administrierenden Person sollte von Ihrem Lab-Hosting-Anbieter bereitgestellt werden.

1. Erweitern Sie in der linken Seitenleiste **Benutzende** und wählen Sie dann **Aktive Benutzende**.

1. Suchen Sie auf der Seite **Aktive Benutzende** nach `Joni`, und wählen Sie dann **Joni Sherman**.

1. Die Eigenschaften von Jonis Konto werden in einem Flyoutbereich auf der rechten Seite angezeigt. Wählen Sie **Rollen verwalten** auf dem Flyoutbereich.

1. Wählen Sie im Bereich **Admin-Rollen verwalten** die Option **Zugriff auf das Admin-Center** und scrollen Sie dann nach unten, um **Alle nach Kategorie anzeigen** zu erweitern.

1. Aktivieren Sie unter der Kategorie **Sicherheit und Compliance** das Kontrollkästchen für **Complianceadministrator** und **Sicherheitsadministrator** und wählen Sie dann **Änderungen speichern** am unteren Rand des Flyoutbereichs.

1. Sie sollten eine Meldung sehen: **Admin-Rollen aktualisiert**.

1. Wählen Sie auf der Seite **Admin-Rollen verwalten** das **X** in der oberen rechten Ecke des Flyoutbereichs, um den Bereich zu schließen.

1. Melden Sie sich vom MOD-Administratorkonto ab, indem Sie das Symbol **MA** oben rechts auswählen und dann **Abmelden** wählen.

   ![Screenshot zeigt den Navigationspfad zur Abmeldung vom MOD-Administratorkonto.](../Media/sign-out.png)

Sie haben Joni Sherman erfolgreich die Rollen des Konformitäts- und Sicherheitsadministrators zugewiesen, die für die Durchführung der Aufgaben in dieser Übung erforderlich sind.

## Aufgabe 2 - Erkunden Sie das Microsoft Purview-Portal

In dieser Aufgabe melden Sie sich als Joni Sherman an, um das Microsoft Purview-Portal zu erkunden.

1. Sie sollten immer noch bei Ihrer Client 1 VM (SC-401-CL1) als **SC-401-CL1\admin** Konto angemeldet sein.

1. Navigieren Sie in **Microsoft Edge** zu **`https://purview.microsoft.com`**.

1. Wenn das Fenster **Konto auswählen** angezeigt wird, wählen Sie **Ein anderes Konto verwenden**.

1. Wenn das Fenster **Anmelden** angezeigt wird, melden Sie sich als `JoniS@WWLxZZZZZZ.onmicrosoft.com` an (wobei ZZZZZZ Ihre eindeutige Mandanten-ID ist, die Sie von Ihrem Provider für die Übung bereitgestellt haben). Das Passwort von Joni wurde in einer früheren Übung festgelegt.

1. Auf dem Bildschirm erscheint eine Meldung über das neue Microsoft Purview-Portal. Wählen Sie **Erste Schritte**, um Zugriff auf das neue Portal zu erhalten.

1. Machen Sie sich mit dem neuen Microsoft Purview-Portal vertraut. Wenn Sie fertig sind, lassen Sie das Browserfenster geöffnet.

Sie haben erfolgreich zum Konto von Joni Sherman gewechselt und können nun die Übung starten.
