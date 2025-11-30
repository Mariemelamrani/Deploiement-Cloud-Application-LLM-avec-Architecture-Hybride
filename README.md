**DÉPLOIEMENT D'UNE APPLICATION IA CONVERSATIONNELLE AVEC RAG SUR AWS CLOUD**

***DESCRIPTION DU PROJET***
Ce projet démontre le déploiement d'une application IA conversationnelle intelligente combinant la puissance des LLMs avec la scalabilité du cloud AWS. Le système utilise l'architecture RAG (Retrieval-Augmented Generation) pour fournir des réponses contextuelles basées sur une base de connaissances de critiques de restaurants.

***ARCHITECTURE TECHNIQUE***
- Frontend : Streamlit
- Backend : Python, LangChain  
- Base de données vectorielle : ChromaDB
- Modèles LLM : Ollama (llama3.2, mxbai-embed-large)
- Infrastructure : AWS EC2, Docker, Ngrok
- Sécurité : IAM, Security Groups, SSH Keys
![Architecture du Projet](./Files/Architecture1.png)


***ARCHITECTURE HYBRIDE***
L'application suit une architecture hybride innovante :
- Frontend Cloud : Application Streamlit containerisée sur AWS EC2
- Backend IA Local : Modèles Ollama exécutés localement
- Connectivité : Tunnel sécurisé Ngrok pour la connectivité cloud-local
- Stack technique : Streamlit, LangChain, ChromaDB, Docker
![Architecture du Projet](./Files/Architecture2.png)


***PROCESSUS DE DÉPLOIEMENT***

Configuration AWS
- Création du compte AWS avec localisation Maroc
- Type de compte : Personnel
- Région principale : eu-west-3 (Paris)

Configuration IAM et Sécurité
- Utilisateur IAM : admin-user
- Politique : AdministratorAccess  
- Accès : Console AWS et accès programmatique
- Authentification : Clés d'accès sécurisées

Instance EC2
- Type d'instance : t3.micro (éligible Free Tier)
- AMI : Amazon Linux 2023
- Région : eu-north-1 (Stockholm)
- Stockage : 8 GiB EBS gp3
- Sécurité : Clé SSH app-key.pem

Containerisation avec Docker
- Image de base : python:3.11-slim
- Port d'exposition : 8501 (Streamlit)
- Optimisation : Installation sans cache
- Dépendances : Gérées via requirements.txt

Configuration Ollama Locale
- Modèle de génération : llama3.2:latest
- Modèle d'embedding : mxbai-embed-large:latest  
- Configuration réseau : OLLAMA_HOST=0.0.0.0
- Sécurité : Ouverture du firewall Windows sur port 11434

Tunnel Sécurisé Ngrok
- Compte Ngrok avec authentification MFA
- Tunnel HTTPS sécurisé sur port 11434
- URL publique persistante pour accès distant
- Monitoring en temps réel via interface web

***FONCTIONNALITÉS VALIDÉES***

Interface Utilisateur
- Interface Streamlit intuitive avec champ de saisie
- Historique des conversations
- Indicateur de traitement en temps réel
- Design responsive et professionnel

Système RAG Opérationnel  
- Recherche sémantique dans la base de connaissances
- Récupération contextuelle des critiques restaurants
- Génération de réponses pertinentes et naturelles
- Intégration transparente des modèles locaux

Performance et Stabilité
- Latence acceptable malgré l'architecture distribuée
- Gestion efficace de la mémoire sur instance t3.micro
- Connexion stable entre cloud et ressources locales
- Optimisation des coûts dans le cadre Free Tier

***DÉFIS ET SOLUTIONS***

Défi Mémoire
Problème : Instance EC2 t3.micro (1 Go RAM) insuffisante pour les modèles LLM
Solution : Architecture hybride externalisant le traitement IA vers ressources locales avec tunnel Ngrok sécurisé

Défi Réseau  
Problème : Restrictions NAT des FAI et firewalls bloquant la connectivité directe
Solution : Implémentation d'un tunnel HTTPS Ngrok contournant les restrictions réseau

Défi Docker
Problème : Complexité de la configuration réseau des conteneurs
Solution : Optimisation des paramètres réseau et gestion dynamique des variables d'environnement

***RÉSULTATS ET IMPACTS***

Performance Technique
- Application pleinement opérationnelle sur infrastructure Free Tier
- Temps de réponse de quelques secondes seulement
- Gestion efficace des ressources limitées
- Architecture scalable et reproductible

Avantages Économiques
- Coût total : Respect strict du cadre Free Tier AWS
- Aucun investissement en hardware requis
- Solution reproductible pour d'autres projets
- Modèle économique viable pour petites structures

Compétences Développées
- Déploiement cloud AWS (EC2, IAM, VPC)
- Containerisation Docker avancée
- Configuration et optimisation de modèles LLM
- Réseaux et tunneling sécurisé
- Architecture d'applications IA distribuées


