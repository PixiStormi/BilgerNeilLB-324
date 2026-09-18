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
