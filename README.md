# Cross-Site-Scripting-XSS
<h2>Lab: PortSwigger</h2>

<p><strong>Laboratório 1:</strong> XSS refletido no contexto HTML sem nada codificado</p>
<strong>Descrição do primeiro Lab:</strong> Este laboratório contém uma vulnerabilidade simples de script entre sites refletida na funcionalidade de pesquisa.
Para resolver o laboratório, execute um ataque de script entre sites que chame a função alert().

-----------------------------------------------------------------------------------------------------------------------------------------------

<strong>Passo 1:</strong> vamos testar o sistema colocando um 'teste', pra ver como o sistema se comporta.

<img src=https://github.com/iRnx/Lab-Cross-Site-Scripting-XSS-/blob/main/imagens/Lab-1/Lab-1.PNG>

-----------------------------------------------------------------------------------------------------------------------------------------------

<strong>Passo 2:</strong> vímos que o "teste" vai para dentro de um `<h1></h1>`, e se tentarmos inserir uma tag ao invés de só "teste"? por exemplo: `<b>teste</b>`. será que funcionaria? vamos ver.

<img src=https://github.com/iRnx/Lab-Cross-Site-Scripting-XSS-/blob/main/imagens/Lab-1/Lab-1-part2.PNG>

<strong>Passo 3:</strong> conseguimos injetar tags HTML pelo campo de busca, agora podemos tentar injetar javascript. por exemplo: `<script>alert('teste')</script>`, vamos ver se funciona.

<img src=https://github.com/iRnx/Lab-Cross-Site-Scripting-XSS-/blob/main/imagens/Lab-1/Lab-1-part3.PNG>

Deu tudo certoooo!! disparamos um alerta e depois recebemos essa mensagem "Congratulations, you solved the lab!" dizendo que resolvemos o lab =)

-----------------------------------------------------------------------------------------------------------------------------------------------

<p><strong>Laboratório 2:</strong> XSS Stored em contexto HTML sem nada codificado</p>
<strong>Descrição do segundo lab:</strong> Este laboratório contém uma vulnerabilidade de script entre sites armazenada na funcionalidade de comentários.
Para resolver este laboratório, envie um comentário que chame a função alert() quando a postagem do blog for visualizada.

-----------------------------------------------------------------------------------------------------------------------------------------------

<strong>Passo 1:</strong> Vamos até a parte que fica os comentarios de cada post. chegando lá, vamos testar um HTML injection `<b>teste</b>`, e enviar.
como podemos ver na imagem abaixo, nosso comentário ficou em negrito, e criou uma tag dentro do parágrafo como podemos ver no DevTools.

<img src=https://github.com/iRnx/Lab-Cross-Site-Scripting-XSS-/blob/main/imagens/Lab-2/Lab-2.PNG>

<strong>Passo 2:</strong> agora vamos tentar injetar javaScript, primeiro escreve algo aleatório sobre o post meu exemplo foi: "Muitooo bom esse Post !!",
em seguida injeta um script `<script>alert('Deu Certooo')</script>`, como podemos ver no DevTools, nosso comentário aparece normal, porém ele é acompanhado de um script.

<img src=https://github.com/iRnx/Lab-Cross-Site-Scripting-XSS-/blob/main/imagens/Lab-2/Lab-2-part-2.PNG>

Deu tudo certoooo!! disparamos um alerta e depois recebemos essa mensagem "Congratulations, you solved the lab!" dizendo que resolvemos o lab =)









