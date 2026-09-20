# LB 324

## Aufgabe 2
Erklären Sie hier, wie man `pre-commit` installiert.

Damit die pre-commit Hooks (automatische Formatierung beim Commit und Tests beim Push) funktionieren, muss jeder Programmierer einmalig Folgendes ausführen:

1. pre-commit installieren:
   pip install pre-commit

2. Die Hooks im Repository registrieren – sowohl den commit- als auch den push-Hook:

pre-commit install --hook-type pre-commit --hook-type pre-push

Ab jetzt wird bei jedem `git commit` der Code automatisch mit `black` formatiert, und bei jedem `git push` werden die Tests mit `pytest` ausgeführt. Nur wenn die Tests bestehen, wird der Push zugelassen.

## Aufgabe 4
Erklären Sie hier, wie Sie das Passwort aus Ihrer lokalen `.env` auf Azure übertragen.

# URL der laufenden Applikation

https://bilgerneil-tagebbbuch-dwamgpfzfpamgza9.germanywestcentral-01.azurewebsites.net

# Passwort aus der .env auf Azure übertragen

Das geheime Passwort steht lokal in der `.env`-Datei (`PASSWORD="..."`) und darf über die `.gitignore` nicht auf GitHub gelangen. Damit das Einschreiben (Login) auf Azure funktioniert, muss dieser Wert manuell als Umgebungsvariable in Azure hinterlegt werden:

1. Im Azure-Portal die Web App `bilgerneil-tagebbbuch` öffnen.
2. Links unter **Einstellungen** auf **Umgebungsvariablen** klicken.
3. Im Reiter **App-Einstellungen** auf **➕ Hinzufügen**.
4. Als **Name** `PASSWORD` und als **Wert** dasselbe Passwort wie in der lokalen `.env` eintragen (ohne Anführungszeichen).
5. Mit **Anwenden** speichern; die App startet neu und liest den Wert über `os.getenv("PASSWORD")` aus.

So bleibt das Geheimnis aus dem Quellcode heraus und wird nur sicher in der Azure-Konfiguration gespeichert.