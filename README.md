# Cross-Site-Scripting-XSS
<h2>Lab: PortSwigger</h2>

<p><strong>Laboratório 1:</strong> XSS refletido no contexto HTML sem nada codificado</p>

<p><strong>Descrição do 1º Lab:</strong> Este laboratório contém uma vulnerabilidade simples de script entre sites refletida na funcionalidade de pesquisa.
Para resolver o laboratório, execute um ataque de script entre sites que chame a função alert().</p>

<strong>Passo 1:</strong> vamos testar o sistema colocando um 'teste', pra ver como o sistema se comporta.

<img src=https://github.com/iRnx/Lab-Cross-Site-Scripting-XSS-/blob/main/imagens/Lab-1/Lab-1.PNG>


<strong>Passo 2:</strong> vímos que o "teste" vai para dentro de um `<h1></h1>`, e se tentarmos inserir uma tag ao invés de só "teste"? por exemplo: `<b>teste</b>`. será que funcionaria? vamos ver.

<img src=https://github.com/iRnx/Lab-Cross-Site-Scripting-XSS-/blob/main/imagens/Lab-1/Lab-1-part2.PNG>

<strong>Passo 3:</strong> conseguimos injetar tags HTML pelo campo de busca, agora podemos tentar injetar javascript. por exemplo: `<script>alert('teste')</script>`, vamos ver se funciona.

<img src=https://github.com/iRnx/Lab-Cross-Site-Scripting-XSS-/blob/main/imagens/Lab-1/Lab-1-part3.PNG>

Deu tudo certoooo!! disparamos um alerta e depois recebemos essa mensagem "Congratulations, you solved the lab!" dizendo que resolvemos o lab =)

-----------------------------------------------------------------------------------------------------------------------------------------------

<p><strong>Laboratório 2:</strong> XSS Stored em contexto HTML sem nada codificado</p>

<p><strong>Descrição do 2º lab:</strong> Este laboratório contém uma vulnerabilidade de script entre sites armazenada na funcionalidade de comentários.
Para resolver este laboratório, envie um comentário que chame a função alert() quando a postagem do blog for visualizada.</p>


<strong>Passo 1:</strong> Vamos até a parte que fica os comentarios de cada post. chegando lá, vamos testar um HTML injection `<b>teste</b>`, e enviar.
como podemos ver na imagem abaixo, nosso comentário ficou em negrito, e criou uma tag dentro do parágrafo como podemos ver no DevTools.

<img src=https://github.com/iRnx/Lab-Cross-Site-Scripting-XSS-/blob/main/imagens/Lab-2/Lab-2.PNG>

<strong>Passo 2:</strong> agora vamos tentar injetar javaScript, primeiro escreva algo aleatório sobre o post meu exemplo foi: "Muitooo bom esse Post !!",
em seguida injeta um script `<script>alert('Deu Certooo')</script>`, como podemos ver no DevTools, nosso comentário aparece normal, porém ele é acompanhado de um script.

<img src=https://github.com/iRnx/Lab-Cross-Site-Scripting-XSS-/blob/main/imagens/Lab-2/Lab-2-part-2.PNG>

Deu tudo certoooo!! disparamos um alerta e depois recebemos essa mensagem "Congratulations, you solved the lab!" dizendo que resolvemos o lab =)

-----------------------------------------------------------------------------------------------------------------------------------------------

<p><strong>Laboratório 3:</strong> DOM XSS no document.write coletor usando a fonte location.search</p>

<p><strong>Descrição do 3º lab:</strong> Este laboratório contém uma vulnerabilidade de script entre sites baseada em DOM na funcionalidade de rastreamento de consulta de pesquisa. Ele usa a função document.write JavaScript, que grava dados na página. A função document.write é chamada com dados de location.search, que você pode controlar usando a URL do site. Para resolver este laboratório, execute um ataque de script entre sites que chame a função alert().<p>

<strong>Passo 1:</strong> vamos escrever `teste` e ver pra onde ele vai, como podemos ver na imagem abaixo, nosso "teste" foi para uma tag `<img>`.

<img src=https://github.com/iRnx/Lab-Cross-Site-Scripting-XSS-/blob/main/imagens/Lab-3/Lab-3-part1.PNG>

<strong>Passo 2:</strong> O que devemos fazer agora, é tentar escapar o teste. e para fazer isso nós usamos aspas duplas `"` pra fechar o atributo src. e em seguida fechamos a tag img `>`. e nosso código pra poder escapar o "teste" ficou assim: `">teste`. e com isso nós conseguimos pular fora da tag img e inserir tags ou textos na página.

<img src=https://github.com/iRnx/Lab-Cross-Site-Scripting-XSS-/blob/main/imagens/Lab-3/Lab-3-part2.PNG>
  
<strong>Passo 3:</strong>Como podemos ver, pra onde nosso "teste" estava indo, ficou vazio.  vamos injetar uma tag em HTML e, dentro dessa tag HTML, vamos passar um atributo para disparar um alert(1), `"><img src=x onerror=alert(1)>`,
vamos criar essa tag de imagem que vai tentar carregar um "x" porém não existe esse caminho para imagem e vai dar erro. aí que entra o "onerror", caso não consiga carregar uma imagem, dispare um alert(1).
  
<img src=https://github.com/iRnx/Lab-Cross-Site-Scripting-XSS-/blob/main/imagens/Lab-3/Lab-3-part3.PNG>
  
Deu tudo certoooo!! disparamos um alerta e depois recebemos essa mensagem "Congratulations, you solved the lab!" dizendo que resolvemos o lab =)

-----------------------------------------------------------------------------------------------------------------------------------------------

<p><strong>Laboratório 4:</strong> DOM XSS no innerHTML coletor usando a fonte location.search</p>

<p><strong>Descrição do 4º Lab:</strong> Este laboratório contém uma vulnerabilidade de script entre sites baseada em DOM na funcionalidade de blog de pesquisa. Ele usa uma innerHTML atribuição, que altera o conteúdo HTML de um elemento div, usando dados de location.search.
Para resolver este laboratório, execute um ataque de script entre sites que chame a função alert().</p>

<strong>Passo 1:</strong> Vamos por "teste" no input e ver para onde ele vai.

<img src=https://github.com/iRnx/Lab-Cross-Site-Scripting-XSS-/blob/main/imagens/Lab-4/Lab-4-part1.PNG>

<strong>Passo 2:</strong> Sabendo que nosso teste vai para dentro de uma tag &#60;span&#62;, poderíamos tentar injetar tags ali dentro, como por exemplo `<b>teste</b>`, essa tag é apenas para deixar em negrito nosso "teste".

<img src=https://github.com/iRnx/Lab-Cross-Site-Scripting-XSS-/blob/main/imagens/Lab-4/Lab-4-part2.PNG>

<strong>Passo 3:</strong> Sabendo que dentro do &#60;span&#62; tem um HTML injection, nós podemos inserir uma tag HTML com um atributo que executa um javaScript ao carregar a página, como por exemplo: `<svg onload=alert(1)>`, quando a página carregar irá disparar um alert(1), por conta do onload.

<img src=https://github.com/iRnx/Lab-Cross-Site-Scripting-XSS-/blob/main/imagens/Lab-4/Lab-4-part3.PNG>

Deu tudo certoooo!! disparamos um alerta e depois recebemos essa mensagem "Congratulations, you solved the lab!" dizendo que resolvemos o lab =)

-----------------------------------------------------------------------------------------------------------------------------------------------

<p><strong>Laboratório 5:</strong> DOM XSS no coletor de atributo âncora do jQuery usando fonte location.search</p>

<p><strong>Descrição do 5º Lab:</strong> Este laboratório contém uma vulnerabilidade de script entre sites baseada em DOM na página de envio de comentários. Ele usa a função seletora da biblioteca jQuery $ para encontrar um elemento âncora e altera seu atributo href usando dados de arquivos location.search.
Para resolver este laboratório, faça o alerta de link "voltar" document.cookie.</p>

<img src=https://github.com/iRnx/Lab-Cross-Site-Scripting-XSS-/blob/main/imagens/Lab-5/Lab-5-part1.PNG>




























