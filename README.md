🛡️ Honeypot Project

Un honeypot éducatif en Python conçu pour observer, enregistrer et analyser les connexions suspectes sur différents ports (HTTP, SSH, TCP).
Ce projet a pour objectif d’apprendre les mécanismes de collecte d’indicateurs de compromission (IoC) et d’illustrer la mise en place d’un environnement de surveillance réseau sécurisé.

⚠️ Usage strictement pédagogique.
N’utilise jamais ce honeypot sur un réseau tiers sans autorisation.

 Fonctionnalités

Écoute configurable sur plusieurs ports (HTTP, SSH, TCP)

 Capture des IP, bannières, ports et payloads

 Enregistrement automatique au format JSON

 API REST pour consulter les événements en direct

Déploiement simple via Docker

 Support de la rotation des logs quotidienne

 Structure du projet
honeypot-project/
├── src/
│   ├── honeypot/
│   │   ├── server.py       # cœur du honeypot
│   │   ├── handlers.py     # gestion des protocoles
│   │   ├── logger.py       # gestion des logs JSON
│   │   ├── api.py          # API REST (FastAPI)
│   │   └── config.py
│   └── cli.py              # interface en ligne de commande
├── tests/                  # tests unitaires (pytest)
├── data/                   # logs collectés
├── config.example.yaml      # modèle de configuration
├── Dockerfile
├── requirements.txt
└── README.md

⚙️ Installation locale

Cloner le projet

git clone https://github.com/ton-pseudo/honeypot-project.git
cd honeypot-project


Créer un environnement virtuel

python -m venv .venv
source .venv/bin/activate


Installer les dépendances

pip install -r requirements.txt


Configurer

cp config.example.yaml config.yaml


Lancer

python -m src.cli run --config config.yaml

 Déploiement avec Docker
docker build -t honeypot .
docker run -v "$(pwd)/data:/app/data" -p 8080:8080 -p 2222:2222 -p 8000:8000 honeypot


L’API sera disponible sur :
 http://localhost:8000/events

 Exemple de log collecté
{
  "src_ip": "203.0.113.42",
  "src_port": 54789,
  "protocol": "ssh",
  "payload": "SSH-2.0-OpenSSH_8.2",
  "received_at": "2025-10-24T13:45:21Z"
}

Éthique & Sécurité

 N’active pas ce honeypot sur un réseau non isolé.

 Ne redirige jamais le trafic entrant vers d’autres cibles.

Supprime ou anonymise les adresses IP avant tout partage public.

 Ce projet est à visée éducative uniquement.

 Technologies utilisées

Langage : Python 3.11

Framework API : FastAPI

Asynchrone : asyncio

Conteneurisation : Docker

Tests : pytest

Format de config : YAML

 Licence

Ce projet est distribué sous licence MIT.
Tu peux l’utiliser, le modifier et le partager librement à des fins éducatives.

 Contribuer

Les contributions sont les bienvenues !
Merci de :

Suivre le style PEP8

Ajouter des tests pour toute nouvelle fonctionnalité

Expliquer clairement ta PR

🧠 Auteur

yahya boutahlil
Développeur passionné de cybersécurité, d’analyse de menaces et d’outils open-source.

💼 Projet destiné à démontrer mes compétences en sécurité réseau, Python et automatisation.
