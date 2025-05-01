# segundoProjetoDio
Segundo projeto do bootcamp da Dio  

Este documento contém o passo a passo para o uso do Azure para Processos de Redundância de Arquivos, destaco que haverá prints contendo informações visuais sobre o passo a passo, essas print serão organizadas de acordo com o item do passo a passo, exemplo: todas as prints que começam com 1 fazem referência direta ao passo 1. Crie o Data Factory


Pré-condições: Tenha um ambiente on-premise do sql server já configurado (acesso o vídeo para entender melhor: https://www.youtube.com/watch?v=gmj2LJo-WFw&ab_channel=RonanVico)

Passos:
1. Crie o Data Factory
2. Crie o storage account e adicione os "containers" necessários
3. Crie o sql database e o server (Cuidado com a definição de autentificação no server, tive dificuldades para conseguir acessá-lo no Data Factory usanod o linked server) ->  preferível usar a autenticação pelo sql, e libera a regra de firewall para o seu usuáiro se for necessário (Se for haverá um indicador de erro ao conectar definindo que é necessário liberar acesso ao seu ip, fornecendo-o, depois disso basta ir nas configurações do servidor, em networking e adicionar uma regra de acesso ao ip) 
4. No "Studio" Data Factory em Manage , crie um runtime environment para o seu sistema on-premise(sql server local), baixe o integration runtime e forneça a chave fornecida no Integration runtime setup quando o programa pedir, além de adiocionar outras configurações, caso necessário  
5. No "Studio" Data Factory em Manage, Crie o linked service para o seu on-premise(sql server local, acione o botão de confiar no certificado, geralmente não consiguirá se conectar sem isso  
6. No "Studio" Data Factory em Manage, Crie o linked service para a sua storage account usando o tipo azure blob storage  
7. No "Studio" Data Factory em Manage, Crie o linked service para o seu sql database geralmente não consiguirá se conectar sem isso
8. No "Studio" Data Factory em Author, crie um pipeline de "Copy data", adicione a origem e o destino de dados e execute-o (A origem será o on-premise e o destino será um arquivo csv no Azure Blob Storage)
9. Verifique se a cópia ocorreu com sucesso acessando o locaol para onde enviou-a.

Agradeço por todos que leram.
