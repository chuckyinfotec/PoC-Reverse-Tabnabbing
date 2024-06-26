# Esta é uma PoC simples da vulneravilidade de Reverse Tabnabbing

![Alt text](poc-exemplo.gif)

## Sobre a vulnerabiliade
O Reverse Tabnabbing é uma técnica maliciosa na qual uma página da web maliciosa, aberta em uma aba, explora a confiança dos usuários em links de confiança abertos em novas abas. Aqui está como funciona:

*Nota:* Isso foi corrigido em navegadores modernos e perenes. Os links usados target="_blank" ​​​​agora estão implícitos rel="noopener" nos navegadores modernos, portanto, essa vulnerabilidade não é tão difundida e crítica como antes. Esta regra implícita também faz parte do padrão HTML. De acordo com caniuse.com, os navegadores perenes suportam implícito rel="noopener" desde cerca de 2018.'

1. Um usuário abre uma página da web confiável (como um serviço de email, rede social, etc.) em uma aba do navegador.
2. Enquanto a página confiável está aberta em uma aba, o usuário clica em um link que leva a uma página maliciosa em outra aba. Este link não possui as devidas medidas de segurança para evitar o Reverse Tabnabbing.
3. A página maliciosa, assim que carregada na nova aba, redireciona a aba anterior (onde a página confiável está aberta) para um site falso, muitas vezes uma página de phishing que se parece com a página original. Isso é feito através do acesso ao objeto window.opener e manipulação do histórico de navegação.
4. O usuário, que agora está na nova aba e vê a página falsa, pode não perceber que a aba anterior foi redirecionada e, portanto, acredita estar interagindo com a página confiável.
5. Se o usuário for induzido a inserir informações confidenciais, como senhas ou dados financeiros, na página falsa, essas informações podem ser capturadas pelo atacante.

## Mitigação
Para mitigar essa vulnerabilidade, é importante garantir que todos os links que abrem em novas abas tenham o atributo rel="noopener noreferrer" para evitar que a página recém-aberta acesse o objeto window.opener. Isso impede que a página maliciosa manipule a página anterior e ajuda a proteger os usuários contra ataques de Reverse Tabnabbing.

## Referência
https://owasp.org/www-community/attacks/Reverse_Tabnabbing
