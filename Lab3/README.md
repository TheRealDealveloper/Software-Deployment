Teil1:
1. CMD öffnen
2. Change Directory zum Folder Teil1
3. docker-compose up -d
Container laufen nun.

Teil2:
1. CMD öffnen
2. Change Directory zum Folder Teil2
3. docker-compose up -d

Die Website kann man unter localhost/8000 aufrufen. 
Die Container für Teil2 werden automatisch erstellt. In den jeweiligen Dockerfiles wird beschrieben wie Docker Images erstellt werden. Teil1 und Teil2 nicht gleichzeitig laufen lassen, da beide Port8000 verwenden.
