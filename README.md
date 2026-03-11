# Teste de Software

https://catolicasc.sharepoint.com/:b:/r/sites/118833_121_teams/Material%20de%20Aula/Aula%2004%20-%2010-03%20-%20Plano%20de%20testes/Apostil%20Aula04%20Planejamento%20de%20Testes.pdf?csf=1&web=1&e=LTZqzK


Riscos identificados no sistema (Shortz-App)
1. Upload aceitar arquivos não permitidos
Tipo de risco: Segurança / Funcional
Se o sistema permitir o envio de arquivos com extensões perigosas (como .exe ou scripts), usuários mal-intencionados podem enviar arquivos maliciosos.
Impacto: Alto
Consequência: possibilidade de malware no servidor ou nos dispositivos dos usuários.
2. Senhas armazenadas sem criptografia
Tipo de risco: Segurança
Se as senhas forem armazenadas em texto simples no banco de dados, qualquer pessoa que tenha acesso ao banco poderá visualizar as senhas.
Impacto: Crítico
Consequência: roubo de contas e vazamento de informações pessoais.
3. Pagamento processado duas vezes
Tipo de risco: Funcional
Caso o sistema permita múltiplos cliques no botão de pagamento, pode ocorrer cobrança duplicada.
Impacto: Alto
Consequência: prejuízo financeiro para o usuário e necessidade de reembolso.
4. Exposição de dados privados na busca
Tipo de risco: Segurança / Privacidade
A funcionalidade de busca pode exibir dados que deveriam ser privados ou restritos.
Impacto: Crítico
Consequência: violação da privacidade dos usuários.
5. Comentários vulneráveis a XSS
Tipo de risco: Segurança
Se o sistema permitir a inserção de scripts ou HTML nos comentários, atacantes podem realizar ataques Cross-Site Scripting (XSS).
Impacto: Crítico
Consequência: roubo de sessão, redirecionamento para sites maliciosos ou execução de scripts.
6. Acesso à área administrativa sem autenticação
Tipo de risco: Segurança / Autorização
Se a área administrativa não exigir login ou verificação de permissão, qualquer usuário pode acessar funções restritas.
Impacto: Crítico
Consequência: alteração ou exclusão de dados importantes do sistema.
7. Upload de imagens muito grandes
Tipo de risco: Desempenho / Funcional
Permitir envio de arquivos muito grandes pode consumir recursos excessivos do servidor.
Impacto: Médio
Consequência: lentidão do sistema ou falta de armazenamento.
8. Falta de validação de dados no cadastro
Tipo de risco: Funcional
Se o sistema não validar corretamente as informações inseridas pelos usuários, dados incorretos podem ser armazenados.
Impacto: Médio
Consequência: inconsistência no banco de dados e falhas em funcionalidades do sistema.
9. Sistema não suportar muitos acessos simultâneos
Tipo de risco: Desempenho
Caso o sistema não seja preparado para muitos usuários ao mesmo tempo, pode ocorrer lentidão ou indisponibilidade.
Impacto: Alto
Consequência: queda do sistema e insatisfação dos usuários.
10. Falha no gerenciamento de sessão
Tipo de risco: Segurança
Se o sistema não controlar corretamente as sessões de login, pode ocorrer acesso indevido às contas.
Impacto: Alto
Consequência: invasão de contas e exposição de dados pessoais.
