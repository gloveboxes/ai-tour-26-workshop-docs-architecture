## Lab 1 : Commencer avec l'atelier

Ceci est un exemple de laboratoire montrant comment les rédacteurs de contenu peuvent créer un contenu d'atelier multilingue à l'aide des onglets collants de MkDocs.

## Ce que vous apprendrez

Dans ce laboratoire, vous allez :

- Configurer votre environnement de développement pour l'atelier
- Vous connecter à la base de données d'exemple et vérifier l'accès aux données
- Créer votre première application alimentée par l'IA
- Comprendre l'architecture de base du Protocole de Contexte Modèle (MCP)
- Tester votre configuration avec des requêtes et réponses simples

## Introduction

Le Protocole de Contexte Modèle (MCP) est une interface standardisée qui connecte les Grands Modèles de Langage (LLMs) à des outils et sources de données externes, tels que des bases de données et des API, permettant des applications d'IA plus intelligentes et extensibles.

Dans ce laboratoire introductif, vous allez :

- Configurer votre environnement de développement pour le développement Python ou C#
- Vous connecter à la base de données de vente au détail Zava DIY en utilisant MCP
- Créer un agent de base capable de requêter des données de vente
- Vérifier que votre configuration fonctionne correctement avant de passer à des sujets avancés

## Exercice de laboratoire

Dans ce laboratoire, vous configurerez votre première application compatible MCP et la connecterez à la base de données d'exemple.

=== "Python"

    ### Étape 1 : Configurer votre environnement Python

    1. Ouvrez le dossier `src/python/workshop` dans votre espace de travail.

    2. Créez un nouveau fichier appelé `mon_premier_agent.py` :

        ```python
        import asyncio
        from mcp_client import MCPClient
        
        async def main():
            """Créez votre premier agent compatible MCP."""
            client = MCPClient()
            
            # Connectez-vous au serveur MCP
            await client.connect("localhost:8000")
            
            # Testez la connectivité de base
            response = await client.query("SELECT COUNT(*) FROM products")

---

Traduit avec GitHub Copilot.
