Docker Getting started
Vorab
git clone git@github.com:tomschiffmann-teaching/03-dido-quiz-app-draft.git von diesem Repository
Den .git Ordner löschen, um mein repository von der Projektmappe zu trennen
Docker Images bauen
./Dockerfile muss vorhanden sein, da es die "Anleitung" für das bauen der finalen App ist
docker build -t tomteaching/draft-quiz-app ./ --> Der Pfad muss auf das Verzeichnis verweisen, wo das Dockerfile liegt
docker build -t <docker-hub-username>/<image-name> <Verzecihnis-mit-Dockerfile> 
docker run -p 3010:3000  tomteaching/draft-quiz-app Allgemein: docker run -p : /
Host-Port: Der Port auf eurem lokalen Betriebssystem (z.B. Windows, Mac, etc.)
Docker-Port : Der Port auf dem eure App innerhalb von Docker läuft /: Der Image Name, welcher gestartet werden soll (siehe Screenshot oben als Beispiel)
Docker Image auf Docker Hub deployen
Authentifizierung auf Docker Hub über docker login
https://hub.docker.com/repository/ aufrufen und neues Repository erstellen
Nennt das repository zunächst erstmal genauso wie euer image (den Teil von <app-name>: Das was hinter dem slash steht von <docker-hub-username>/<app-name>)
docker tag  tomteaching/draft-quiz-app  tomteaching/draft-quiz-app:latest
docker tag <unser-lokales-image> <remote-image>:<version>
docker push tomteaching/draft-quiz-app:latest
docker push <remote-image>:<version>
Unter https://hub.docker.com/repository/ überprüfen ob die hochgeladene Version auch vorhanden
Über Docker Desktop alle Container löschen und auch alle Images löschen
Einmal überprüfen, dass app nicht mehr läuft
docker pull tomteaching/draft-quiz-app:latest
docker pull <image>
docker run -p 3010:3000 tomteaching/draft-quiz-app
docker run -p <Host-Port>:<Docker-Port> <docker-hub-username>/<app-name>
Docker Compose
Docker Compose ermöglicht die Definition mehrerer services
Erleichtert Entwicklungen und ihre abhängigkeiten
Fährt alle dort definierten services hoch und auch wieder herunter
Guckt euch in Docker Desktop eure Volumes an
Kopiert euch aus diesem repo die ./docker-compose.yml und zusätzlich das gesamte ./monitoring/ Verzeichnis
Danach einfach docker compose up -d
Volumes Reiter in Docker Desktop nochmal angucken
Gucken, dass die apps auf http://localhost:3000 und http://localhost:3001
Danach die apps wieder herunterfahren mit docker compose down
Überprüfen, dass die services nicht mehr laufen
Volumes Reiter in Docker Desktop nochmal angucken
In der Entwicklung wird auch häufig die Option docker compose down -v verwendet, um die lokalen Volumes mit zu löschen. Also einmal docker compose down -v ausführen
Volumes Reiter in Docker Desktop nochmal angucken