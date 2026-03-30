# Plano de Testes – Shortz-App

**Versão:** 1.0  
**Data:** 31/03/2026  
**Autor(es):** Athos Diniz, Gustavo Necal, Lucas Scheibe e Ruan Martins.  
**Projeto:** Shortz-App

## 1\. Introdução

Este documento descreve o planejamento dos testes para o projeto Shortz-App, definindo a estratégia, o escopo e os casos de teste para garantir a qualidade do software.

## 2\. Escopo dos Testes

Esta seção detalha as funcionalidades do Shortz-App que serão abrangidas pelos testes neste Plano e aquelas que, por decisão estratégica ou fase de desenvolvimento, não serão testadas nesta entrega .

### 2.1. Funcionalidades em Escopo

As seguintes funcionalidades serão testadas nesta fase, com foco em garantir sua qualidade e conformidade com os requisitos:

* **Validação de Força de Senha:** A função **SenhaehForte** será testada para garantir que senhas atendam aos critérios de segurança (mínimo 8 caracteres, maiúscula, número, caractere especial).  
* **Upload de Vídeos:** O processo de upload de vídeos será testado, incluindo a validação de tamanho (até 100MB) e formato de arquivo.  
* **Interação de Curtir/Descurtir Vídeos:** A funcionalidade de usuários logados curtirem e descurtirem vídeos, e a atualização da contagem de likes, será verificada.  
* **Atualização de Biografia do Perfil:** A capacidade de um usuário atualizar sua biografia no perfil será testada.

### 2.2. Funcionalidades Fora de Escopo

As seguintes funcionalidades não serão testadas nesta entrega, mas poderão ser incluídas:

* **Busca de Conteúdo:** A funcionalidade de busca de vídeos ou usuários não será testada.  
* **Notificações:** O sistema de notificações não será incluso.  
* **Streaming de Vídeos:** A performance e a qualidade do streaming de vídeos não serão o foco principal desta fase de testes.  
* **Testes de Carga e Performance:** Testes focados em volume de usuários ou desempenho sob estresse não serão realizados.  
* **Painel Administrativo:** Qualquer funcionalidade de administração do sistema não será testada.  
* **Testes E2E Completos no Browser:** Testes de ponta a ponta que simulam o fluxo completo do usuário através da interface gráfica não serão o foco principal, embora cenários específicos possam ser abordados em testes manuais.  
* **Integrações com APIs de Terceiros:** Integrações com serviços externos não serão testadas nesta fase.  
* **Feed Personalizado:** A lógica de personalização do feed de vídeos para o usuário não será testada.

## 3\. Estratégia de Testes

### 3.1. Filosofia de Testes

Nossa equipe adota a mentalidade de qualidade desde o início do ciclo de desenvolvimento, seguindo o princípio do **Shift-Left Testing**. Isso significa que as atividades de teste são iniciadas o mais cedo possível, desde o planejamento e a concepção, para prevenir a introdução de defeitos e reduzir o custo de correção, que é exponencialmente maior quanto mais tarde um defeito é descoberto. Acreditamos que a qualidade é uma responsabilidade compartilhada por toda a equipe, e não apenas uma etapa final.

### 3.2. Pirâmide de Testes

A estratégia de testes para o Shortz-App será guiada pela **Pirâmide de Testes**, um modelo que preconiza a priorização de testes em diferentes níveis, conforme ilustrado abaixo:

* **Base (Testes Unitários):** Constituem a maior parte dos nossos testes. São rápidos, baratos e testam funções e métodos isolados do código. Serão aplicados para validar a lógica de negócios fundamental, como a função SenhaehForte e a validação de tamanho de arquivos de vídeo.  
* **Meio (Testes de Integração):** Em quantidade moderada, verificam a comunicação e a interação entre diferentes componentes do sistema, como a integração da API com o banco de dados para o recurso de "curtir" vídeos.  
* **Topo (Testes End-to-End / E2E):** Em menor quantidade, são mais lentos e caros. Simulam o fluxo completo do usuário na interface, garantindo que o sistema funcione como um todo do ponto de vista do usuário final.

### 3.3. Test-Driven Development (TDD)

Para funcionalidades críticas e complexas, como a validação de força de senha (SenhaehForte), aplicaremos a abordagem de **Test-Driven Development (TDD)**. Este ciclo de desenvolvimento (Red-Green-Refactor) nos permite escrever testes antes do código de produção, garantindo que a funcionalidade atenda aos requisitos desde o início e que o código seja robusto e de fácil manutenção.

## 4\. Riscos e Mitigação

### 4.1. Matriz de Riscos

Com base na análise das especificações do Shortz-App e nos conceitos de planejamento baseado em risco, identificamos os seguintes riscos de qualidade, suas probabilidades, impactos e as estratégias de mitigação através dos testes:

| Risco | Probabilidade | Impacto | Mitigação |
| :---- | :---- | :---- | :---- |
| Falha no upload de vídeos | Média/Alta | Crítico (Usuários não postam conteúdo, afeta o core business) | Priorizar testes rigorosos (unitários, integração e E2E) no módulo de upload, incluindo validação de tamanho e formato de arquivo. |
| Erro na contagem de visualizações | Média | Alto (Afeta a credibilidade e engajamento do usuário) | Cobertura moderada de testes de integração para garantir a correta atualização e exibição das contagens. |
| Falha na atualização da biografia do perfil | Baixa | Médio (Pode gerar frustração, mas não impede o uso principal) | Cobertura básica com testes unitários para a função de atualização e testes de interface para a persistência da informação. |
| Vulnerabilidade na validação de senha | Alta | Crítico (Comprometimento de segurança e dados do usuário) | Implementação de TDD para a função SenhaehForte, com testes unitários abrangentes cobrindo todos os requisitos (tamanho, caracteres especiais, maiúsculas/minúsculas, números). |
| Falha na funcionalidade de "curtir"/"descurtir" | Média | Alto (Afeta a interação e engajamento social) | Testes de integração para garantir a comunicação correta entre a API e o banco de dados, e testes de interface para a atualização visual do contador. |

## 5\. Casos de Teste Planejados (Caixa Preta)

### 5.1. Classes de Equivalência e Valores-Limite

#### Validação de Senha (SenhaehForte)

| Critério | Partições Válidas | Partições Inválidas | Valores-Limite |
| :---- | :---- | :---- | :---- |
| **Comprimento** | 8 a 64 caracteres | \< 8 caracteres, \> 64 caracteres | 7, 8, 64, 65 |
| **Maiúscula** | Pelo menos 1 maiúscula | Nenhuma maiúscula | N/A |
| **Número** | Pelo menos 1 número | Nenhum número | N/A |
| **Caractere Especial** | Pelo menos 1 especial | Nenhum especial | N/A |

#### Upload de Vídeo

| Critério | Partições Válidas | Partições Inválidas | Valores-Limite |
| :---- | :---- | :---- | :---- |
| **Tamanho do Arquivo** | 0.01 MB a 100 MB | 0 MB, \> 100 MB | 0, 0.01, 100, 100.01 |
| **Formato do Arquivo** | MP4, MOV, AVI | JPG, PNG, DOCX | N/A |

### 5.2. Tabelas de Decisão

#### Validação de Senha (SenhaehForte)

| Condição / Ação | C1: Comprimento \>= 8 | C2: Tem Maiúscula | C3: Tem Número | C4: Tem Especial | A1: Senha Válida |
| :---- | :---- | :---- | :---- | :---- | :---- |
| **Regra 1** | V | V | V | V | X |
| **Regra 2** | F | \- | \- | \- |  |
| **Regra 3** | V | F | V | V |  |
| **Regra 4** | V | V | F | V |  |
| **Regra 5** | V | V | V | F |  |

### 5.3. Detalhamento dos Casos de Teste

| ID | Título | Pré-condições | Passos | Resultado Esperado | Prioridade |
| :---- | :---- | :---- | :---- | :---- | :---- |
| CT-01 | Senha Válida \- Todos os critérios (EP) | Função SenhaehForte disponível. | Chamar SenhaehForte ("MinhaSenha123\!") | Retornar VERDADEIRO | Alta |
| CT-02 | Senha Inválida \- Menos de 8 caracteres (BVA) | Função SenhaehForte disponível. | Chamar SenhaehForte ("Curta\!1") | Retornar FALSO | Alta |
| CT-03 | Senha Inválida \- Sem maiúscula (EP) | Função SenhaehForte disponível. | Chamar SenhaehForte ("minhasenha123\!") | Retornar FALSO | Média |
| CT-04 | Senha Inválida \- Sem número (EP) | Função SenhaehForte disponível. | Chamar SenhaehForte ("MinhaSenha\!\!") | Retornar FALSO | Média |
| CT-05 | Senha Inválida \- Sem especial (EP) | Função SenhaehForte disponível. | Chamar SenhaehForte ("MinhaSenha123") | Retornar FALSO | Média |
| CT-06 | Senha Inválida \- Exatamente 8 caracteres, incompleta (BVA) | Função SenhaehForte disponível. | Chamar SenhaehForte ("abcdefg1") | Retornar FALSO | Média |
| CT-07 | Senha Válida \- Exatamente 8 caracteres, completa (BVA) | Função SenhaehForte disponível. | Chamar SenhaehForte ("A1b\!cDeF") | Retornar VERDADEIRO | Alta |
| CT-08 | Upload de Vídeo \- Arquivo válido (EP) | Usuário logado. | Tentar fazer upload de um arquivo MP4 de 50MB. | Upload realizado com sucesso. | Alta |
| CT-09 | Upload de Vídeo \- Arquivo 0 MB (BVA) | Usuário logado. | Tentar fazer upload de um arquivo MP4 de 0 MB. | Mensagem de erro: "Arquivo vazio." | Alta |
| CT-10 | Upload de Vídeo \- Arquivo 100 MB (BVA) | Usuário logado. | Tentar fazer upload de um arquivo MP4 de 100 MB. | Upload realizado com sucesso. | Alta |
| CT-11 | Upload de Vídeo \- Arquivo 100.01 MB (BVA) | Usuário logado. | Tentar fazer upload de um arquivo MP4 de 100.01 MB. | Mensagem de erro: "Tamanho máximo excedido." | Alta |
| CT-12 | Upload de Vídeo \- Formato inválido (EP) | Usuário logado. | Tentar fazer upload de um arquivo JPG de 5 MB. | Mensagem de erro: "Formato de arquivo inválido." | Média |
| CT-13 | Curtir Vídeo \- Usuário logado, primeira vez (Exemplo da aula) | Usuário logado, vídeo existe, usuário não curtiu. | Clicar no botão "Curtir" no vídeo. | Like registrado, contador atualizado (+1). | Alta |
| CT-14 | Curtir Vídeo \- Usuário não logado (Exemplo da aula) | Vídeo existe, usuário não logado. | Clicar no botão "Curtir" no vídeo. | Redirecionar para tela de login ou mensagem de erro. | Alta |
| CT-15 | Curtir Vídeo \- Usuário logado, já curtiu (Cenário adicional) | Usuário logado, vídeo existe, usuário já curtiu. | Clicar no botão "Curtir" (que deve ser "Descurtir"). | Like removido, contador atualizado (-1). | Média |

## 6\. Critérios de Entrada, Saída e Suspensão

Estes critérios definem as condições para iniciar, concluir e, se necessário, pausar as atividades de teste, garantindo um processo controlado e eficiente.

### 6.1. Critérios de Entrada

Os testes serão iniciados somente quando as seguintes condições forem satisfeitas:

* **Ambiente de Testes Configurado:** Todas as ferramentas e dependências (Node.js, MySQL/SQLite, Vitest, Supertest) devem estar instaladas e configuradas.  
* **Código-Fonte Estável:** O código-fonte das funcionalidades a serem testadas deve estar no repositório, com o build passando e sem erros críticos conhecidos que impeçam a execução dos testes.  
* **Especificações Claras:** Os requisitos e especificações das funcionalidades a serem testadas devem estar claros e acessíveis.  
* **Dados de Teste Preparados:** Os dados de teste necessários para a execução dos casos de teste devem estar disponíveis e carregados no ambiente.

### 6.2. Critérios de Saída

Os testes serão considerados concluídos quando os seguintes critérios forem atendidos:

* **Cobertura de Testes:** A cobertura de código para as funcionalidades testadas deve atingir um mínimo de 70% (para testes unitários e de integração).  
* **Zero Defeitos Críticos/Altos:** Todos os defeitos classificados como "Críticos" ou "Altos" na Matriz de Riscos devem ter sido corrigidos e verificados.  
* **Casos de Teste Executados:** Pelo menos 90% dos casos de teste planejados devem ter sido executados.  
* **Revisão de Código (PR):** O Pull Request contendo as implementações e os testes deve ter sido aprovado em code review.

### 6.3. Critérios de Suspensão

As atividades de teste serão temporariamente suspensas se alguma das seguintes condições ocorrer:

* **Bloqueadores Críticos:** Identificação de um defeito que impede a execução de um grande número de testes ou a validação de uma funcionalidade central (ex: falha na migração que impede a criação do banco de dados de testes).  
* **Instabilidade do Ambiente:** O ambiente de testes se torna instável ou indisponível, impedindo a execução confiável dos testes.  
* **Mudanças de Requisitos:** Alterações significativas nos requisitos de uma funcionalidade que invalidam os casos de teste existentes, exigindo uma revisão substancial do plano.

## 7\. Referências

-  **01 \- Resumo das Aulas 01 a 04.pdf** \- Fundamentos de Testes no Shortz-App, Cultura de Qualidade, Pirâmide de Testes, Shift-Left, Planejamento Baseado em Risco.  
    
-  **Exemplos de Testes .pdf** \- Exemplos de Testes em Portugol para o Shortz-App (Validação de Senha, Curtir Vídeo).  
    
-  **Apostila Aula 04 Planejamento de Testes.pdf** \- Planejamento de Testes, Riscos,   
  Estratégia e Estrutura do Plano de Teste, Critérios de Entrada, Saída e Suspensão.  
    
-  **02 \- Apostila da Aula 05 \- Técnicas de Teste Black-Box.pdf** \- Técnicas de Teste Black-Box (Particionamento de Equivalência, Análise de Valores-Limite, Tabela de Decisão).