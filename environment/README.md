# Environnement local (Docker)

ParaBank est un projet open-source de Parasoft, non versionné dans ce dépôt (dépôt distinct, non modifié : [github.com/parasoft/parabank](https://github.com/parasoft/parabank)).

## Lancer l'application en local

```bash
git clone https://github.com/parasoft/parabank.git
cp environment/docker-compose.yml environment/Dockerfile.compose parabank/
cd parabank
docker compose up --build
```

L'application est ensuite accessible sur **http://localhost:8081/parabank**.

Cette configuration Docker construit le `.war` avec Maven puis le déploie sur Tomcat — aucune installation locale de Java/Maven n'est nécessaire.
