## Step 1: Configurando MCP

O time de design desenhou uma bela página no [Figma](https://www.figma.com/community/file/1545138026079592828), e recebemos a tarefa de criar esta landing page. Mas como de costume, nosso time comercial tem pressa, visto que precisa apresentar ainda hoje para o cliente. Ciente disto, decidimos utiliza Github Copilot para nos auxiliar. Neste step, vamos configurar o Github Copilot para "conversar" com o [Figma através do protocolo MCP](https://help.figma.com/hc/en-us/articles/32132100833559-Guide-to-the-Dev-Mode-MCP-Server).

**Atenção:**

O Figma oficial requer uma licença paga, conforme a documentação acima. Vamos utilizar um servidor MCP da comunidade chamado [Framelink](https://www.framelink.ai/docs/quickstart).

### O que é Model Context Protocol (MCP)?

[Model Context Protocol (MCP)](https://modelcontextprotocol.io/introduction) é frequentemente chamado de "USB-C para IA" - um conector universal que permite ao GitHub Copilot (e outras ferramentas de IA) interagir perfeitamente com outros serviços.

Essencialmente, é uma forma de descrever as capacidades e requisitos de um serviço, para que ferramentas de IA possam facilmente determinar quais métodos usar e fornecer os parâmetros com precisão. Um servidor MCP está fornecendo essa interface.

### :keyboard: Atividade: Conheça seu ambiente

Antes de mergulharmos no MCP, vamos iniciar nosso ambiente de desenvolvimento e nos refamiliarizar com a aplicação.

1. Clique com o botão direito no botão abaixo para abrir a página **Criar Codespace** em uma nova aba. Use a configuração padrão.

   [![Abrir no GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/{{full_repo_name}}?quickstart=1)

1. Valide se a extensão **Copilot** está instalada e habilitada.

   <img width="300" alt="copilot extension for VS Code" src="https://github.com/user-attachments/assets/ef1ef984-17fc-4b20-a9a6-65a866def468" /><br/>

1. Verifique se nossa aplicação roda antes da modificação. Abra um novo Terminal e digite `npm run dev` para inicializar o servidor de desenvolvimento.

   <details>
   <summary>🤷 Tendo problemas?</summary><br/>

   Caso tenha problemas com falta de dependências, rode um comando `npm install` para instalar as dependências.

   </details>

1. Use a aba **Portas** para encontrar o endereço da página web, abra-a e verifique se está funcionando.

   <details>
   <summary>📸 Mostrar captura de tela</summary><br/>

   <img width="350" alt="ports tab" src="https://github.com/user-attachments/assets/8d24d6b5-202d-4109-8174-2f0d1e4d8d44" />

   </details>


### :keyboard: Atividade: Adicionar o servidor GitHub MCP

1. Dentro do seu codespace, abra o painel **Copilot Chat** e verifique se o modo **Agente** está selecionado.

   <img width="200" alt="image" src="https://github.com/user-attachments/assets/201e08ab-14a0-48bf-824e-ba4f8f43f8ab" />

   <details>
   <summary>Modo Agente ausente?</summary><br/>

   - Verifique se o VS Code está pelo menos na versão `v1.99.0`.
   - Verifique se a extensão Copilot está pelo menos na versão `v1.296.0`.
   - Verifique se o modo Agente está habilitado nas suas [configurações de usuário ou workspace](https://code.visualstudio.com/docs/configure/settings#_workspace-settings).

      <img width="300" alt="image" src="https://github.com/user-attachments/assets/407a79dd-707e-471b-b56b-1938aece4ad8" />

   </details>

1. Dentro do seu codespace, navegue até a pasta `.vscode` e crie um novo arquivo chamado `mcp.json`. Cole o seguinte conteúdo:

   📄 **.vscode/mcp.json**

   ```json
   {
        "servers": {
            "Framelink Figma MCP": {
                "command": "npx",
                "args": [
                    "-y",
                    "figma-developer-mcp",
                    "--figma-api-key=SEU_TOKEN",
                    "--stdio"
                ]
            }
        }
    }
   ```

Você precisa criar um token de acesso ao Figma, veja como criar o mesmo [clicando aqui](https://help.figma.com/hc/en-us/articles/8085703771159-Manage-personal-access-tokens).

1. No arquivo `.vscode/mcp.json`, clique no botão **Iniciar** e aceite o prompt para autenticar com o GitHub. Isso acabou de informar o GitHub Copilot sobre as capacidades do servidor MCP.

1. No painel lateral do Copilot, clique no **ícone 🛠️** para mostrar as capacidades adicionais.

   <img width="350" alt="image" src="https://github.com/user-attachments/assets/b1be8b80-c69c-4da5-9aea-4bbaa1c6de10" />

   <img width="350" alt="image" src="https://github.com/user-attachments/assets/99178d1b-adbe-4cf4-ab9c-3a4d29918a13" />

1. **Faça commit** e **push** do arquivo `.vscode/mcp.json` para a branch `main`.

   > 🪧 **Nota:** Fazer push diretamente para `main` não é uma prática recomendada. É apenas para simplificar este exercício.

1. Agora que sua configuração do servidor MCP foi enviada para o GitHub, a Mona já deve estar ocupada verificando seu trabalho. Dê um momento para ela e fique de olho nos comentários. Você verá ela responder com informações de progresso e a próxima lição.

> [!NOTE]
> Os próximos passos envolverão criar issues do GitHub. Se você quiser evitar emails de notificação, pode parar de acompanhar o repositório.

<details>
<summary>Tendo problemas?</summary><br/>

Certifique-se de que:

- Seu arquivo `.vscode/mcp.json` é similar ao exemplo fornecido.
- Você fez push das mudanças para a branch `main`.

</details>