## Lab 1: Pagsisimula sa Workshop

Ito ay isang halimbawa ng lab na nagpapakita kung paano maaaring lumikha ang mga manunulat ng nilalaman ng multi-language workshop gamit ang MkDocs sticky tabs.

## Ano ang Matututuhan Mo

Sa lab na ito, ikaw ay:

- Magse-set up ng iyong development environment para sa workshop
- Kokonekta sa sample database at i-verify ang data access
- Lilikha ng iyong unang AI-powered na aplikasyon
- Mauunawaan ang pangunahing arkitektura ng Model Context Protocol (MCP)
- Susubukan ang iyong setup gamit ang simpleng mga query at tugon

## Panimula

Ang Model Context Protocol (MCP) ay isang standardized na interface na nagkokonekta sa Large Language Models (LLMs) sa mga external na tool at data sources—tulad ng mga database at APIs—na nagbibigay-daan sa mas matalinong at mas extensible na AI applications.

Sa introductory lab na ito, ikaw ay:

- Magko-configure ng iyong development environment para sa Python o C# development
- Kokonekta sa Zava DIY retail database gamit ang MCP
- Lilikha ng isang basic na agent na maaaring mag-query ng sales data
- I-verify na gumagana nang tama ang iyong setup bago lumipat sa advanced na mga paksa

## Lab Exercise

Sa lab na ito, magse-set up ka ng iyong unang MCP-enabled na aplikasyon at ikokonekta ito sa sample database.

=== "Python"

    ### Hakbang 1: I-configure ang Iyong Python Environment

    1. Buksan ang `src/python/workshop` folder sa iyong workspace.

    2. Gumawa ng bagong file na tinatawag na `my_first_agent.py`:

        ```python
        import asyncio
        from mcp_client import MCPClient
        
        async def main():
            """Gumawa ng iyong unang MCP-enabled na agent."""
            client = MCPClient()
            
            # Kumonekta sa MCP server
            await client.connect("localhost:8000")
            
            # Subukan ang basic connectivity
            response = await client.query("SELECT COUNT(*) FROM products")
        ```

*Isinalin gamit ang GitHub Copilot at GPT-4o.*
