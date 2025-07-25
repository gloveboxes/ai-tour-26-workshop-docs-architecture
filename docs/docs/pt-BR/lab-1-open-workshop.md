## Laboratório 1: Começando com o Workshop

Este é um exemplo de laboratório mostrando como os criadores de conteúdo podem criar conteúdo de workshop multilíngue usando abas fixas do MkDocs.

## O que Você Aprenderá

Neste laboratório, você irá:

- Configurar seu ambiente de desenvolvimento para o workshop
- Conectar-se ao banco de dados de exemplo e verificar o acesso aos dados
- Criar sua primeira aplicação com inteligência artificial
- Entender a arquitetura básica do Protocolo de Contexto de Modelo (MCP)
- Testar sua configuração com consultas e respostas simples

## Introdução

O Protocolo de Contexto de Modelo (MCP) é uma interface padronizada que conecta Modelos de Linguagem de Grande Escala (LLMs) a ferramentas e fontes de dados externas—como bancos de dados e APIs—permitindo aplicativos de IA mais inteligentes e extensíveis.

Neste laboratório introdutório, você irá:

- Configurar seu ambiente de desenvolvimento para desenvolvimento em Python ou C#
- Conectar-se ao banco de dados de varejo Zava DIY usando MCP
- Criar um agente básico que pode consultar dados de vendas
- Verificar se sua configuração está funcionando corretamente antes de avançar para tópicos avançados

## Exercício de Laboratório

Neste laboratório, você configurará sua primeira aplicação habilitada para MCP e a conectará ao banco de dados de exemplo.

=== "Python"

    ### Etapa 1: Configure Seu Ambiente Python

    1. Abra a pasta `src/python/workshop` no seu espaço de trabalho.

    2. Crie um novo arquivo chamado `meu_primeiro_agente.py`:

        ```python
        import asyncio
        from mcp_client import MCPClient
        
        async def main():
            """Crie seu primeiro agente habilitado para MCP."""
            client = MCPClient()
            
            # Conecte-se ao servidor MCP
            await client.connect("localhost:8000")
            
            # Teste a conectividade básica
            response = await client.query("SELECT COUNT(*) FROM products")
