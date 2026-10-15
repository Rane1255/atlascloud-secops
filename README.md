# atlascloud-secops
# AtlasCloud — Refonte de la sécurité périmétrique

Projet de refonte de la sécurité périmétrique pour AtlasCloud (SaaS B2B, 250 salariés) : architecture cible, plan de migration sur 6 phases et preuve de concept reproductible sur un poste de travail.

## Contenu du dépôt

| Dossier | Contenu |
|---|---|
| `docs/` | Note de cadrage, dossier d'architecture, roadmap, présentation COMEX |
| `docs/adr/` | Architecture Decision Records (une décision = un fichier) |
| `diagrams/` | Diagrammes C4 (contexte, conteneur, composant) en PlantUML ou draw.io |
| `lab/` | Configuration du PoC (Ansible, Terraform/OpenTofu, fichiers de config) |
| `tests/` | Scénarios d'attaque, résultats attendus et obtenus |

## Périmètre du PoC

| Brique | Technologie | Rôle |
|---|---|---|
| NGFW | OPNsense | NAT, règles par zone, WireGuard |
| IDS/IPS | Suricata (jeu ET Open) | Détection d'intrusion, flux eve vers Wazuh |
| WAF | Nginx + ModSecurity + OWASP CRS v4 | Protection de l'application cible |
| ZTNA | Headscale + clients Tailscale officiels | Accès réseau par identité |
| Identité | Authelia (OIDC) | Fournisseur d'identité pour Headscale |
| Audit trail | Wazuh mono-nœud | Centralisation et conservation des journaux (NIS2) |
| Cible | OWASP Juice Shop | Application vulnérable de test |

## Prérequis

- Poste hôte : 16 Go de RAM minimum (32 Go recommandés)
- VirtualBox (ou autre hyperviseur)
- Docker (ou Podman) dans une VM Linux ou WSL2
- Ansible, OpenTofu (ou Terraform)

## Reproduire le PoC

> Section à compléter au fil du projet : ordre d'installation, commandes exactes, versions figées.

1. Cadrage et décisions : voir `docs/adr/`
2. Déploiement : `lab/README.md` (à venir)
3. Scénarios de test : `tests/README.md` (à venir)

## Décisions d'architecture

Les décisions sont tracées dans [`docs/adr/`](docs/adr/). Points clés :

- [ADR 0001 — Licence Apache 2.0](docs/adr/0001-licence.md)
- [ADR 0002 — Répartition du lab](docs/adr/0002-repartition-lab.md)

## Licence

Apache License 2.0, voir (LICENSE).
