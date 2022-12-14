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
Para resolver este laboratório, execute um ataque de script entre sites que chame a função alert.</p>

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

<strong>Passo 1:</strong> vamos colocar um "teste" em "returnPath" para ver o que acontece.

<img src=https://github.com/iRnx/Lab-Cross-Site-Scripting-XSS-/blob/main/imagens/Lab-5/Lab-5-part1.PNG>

<strong>Passo 2:</strong> Vamos começar pela url injetando `javascript:alert(document.cookie)` e aperte enter, depois disso podemos ver que agora o link do "back" esta sendo redirecionado para "javascript:alert(document.cookie)", agora abra o devtools e vamos dar uma olhada no codigo jquery, se você notar ele esta pegando tudo que vem do parâmetro "returnPath" e não tem tratamento nenhum, possibilitando a injeção de scripts, neste caso conseguimos um xss dentro de um href, quando clicarmos no "back", irá disparar um alerta contendo o cookie.

<img src=https://github.com/iRnx/Lab-Cross-Site-Scripting-XSS-/blob/main/imagens/Lab-5/Lab-5-part2.PNG>

Deu tudo certoooo!! disparamos um alerta e depois recebemos essa mensagem "Congratulations, you solved the lab!" dizendo que resolvemos o lab =)

-----------------------------------------------------------------------------------------------------------------------------------------------

<p><strong>Laboratório 6:</strong> DOM XSS no coletor seletor do jQuery usando um evento hashchange</p>

<p><strong>Descrição do 6º Lab:</strong> Este laboratório contém uma vulnerabilidade de script entre sites baseada em DOM na página inicial. Ele usa a $()função seletora do jQuery para rolar automaticamente para um determinado post, cujo título é passado através da location.hashpropriedade.
Para resolver o laboratório, entregue um exploit para a vítima que chama a print()função em seu navegador.</p>

<strong>Passo 1:</strong> Esse lab tem uma funcionalidade que quando nós digitamos na url o título de algum Post a página vai direto para esse post.

<img src=https://github.com/iRnx/Lab-Cross-Site-Scripting-XSS-/blob/main/imagens/Lab-6/Lab-6-part1.PNG>

<strong>Passo 2:</strong> agora vamos digitar algo na frente da hash (que seria aquele jogo da velha), no meu exemplo eu digitei `#1533` e não aconteceu nada, analisando o código nós conseguimos ver que existe um evento chamado "hashchange", ou seja, sempre que a hash(#) mudar o valor dela, uma funçao anônima será chamada.

                         <pre>$(window).on('hashchange', function(){ 
                            var post = $('section.blog-list h2:contains(' + decodeURIComponent(window.location.hash.slice(1)) + ')');
                            if (post) post.get(0).scrollIntoView();
                        });</pre>
                        
"section.blog-list h2:contains" essa parte do código irá pegar todos os h2 que contém o título dos posts do blog, "decodeURIComponent(window.location.hash.slice(1))" ja essa parte do código, é para pegar o que nós escrevemos na url. agora nós temos uma pequena verificação: "if (post) post.get(0).scrollIntoView();" se o que digitamos na url for exatamente igual a essa parte: "section.blog-list h2:contains" (que seria os títulos do blog), a verificação se torna verdadeira e o scroll é executado para rolar onde o existir o nome do titulo. 
                    

<img src=https://github.com/iRnx/Lab-Cross-Site-Scripting-XSS-/blob/main/imagens/Lab-6/Lab-6part2.PNG>

<strong>Passo 3:</strong> Como podemos ver na imagem anterior, digitamos "1533" e nada aconteceu!! e se colocarmos uma tag html ??? será que da bom? até porque como vimos no código não existe filtragem nenhuma do que esta vindo da url. Digite na url `<img src=x onerror=print()>`, e como você pode ver deu certo!! porém ainda não resolvemos este lab.

<img src=https://github.com/iRnx/Lab-Cross-Site-Scripting-XSS-/blob/main/imagens/Lab-6/Lab-6-part3.PNG>

<strong>Passo 4:</strong> Agora vamos supor que nós queremos mandar este link malicioso para alguma vítima, infelizmente não irá funcionar!! sabe porque? pois não houve uma mudança de hash e consequentemente não executou a função anônima. 

                         <pre>$(window).on('hashchange', function(){ 
                            var post = $('section.blog-list h2:contains(' + decodeURIComponent(window.location.hash.slice(1)) + ')');
                            if (post) post.get(0).scrollIntoView();
                        });</pre>
  

nesta parte: "$(window).on('hashchange', function(){" esta falando que quando houver uma mudança de "hashchange" a função irá executar. porém se enviarmos para a vítima não vai haver uma mudança de hash, e pra isso vamos ter que escrever um exploit que vai fazer exatamente essa mudança de hash que nós queremos quando a vítima acessar o link malicioso.

<strong>Passo 5:</strong> Basta copiar o seu id de sessão e depois ir em "go to exploit server"

<img src=https://github.com/iRnx/Lab-Cross-Site-Scripting-XSS-/blob/main/imagens/Lab-6/Lab-6-part-5.PNG>

<strong>Passo 6:</strong> Agora basta inserir o exploit no body e entregar para vitima.

<img src=https://github.com/iRnx/Lab-Cross-Site-Scripting-XSS-/blob/main/imagens/Lab-6/Lab-6-part6.PNG>


`<iframe src="https://0ad000b204a278efc084b29d003500fb.web-security-academy.net/#1533" onload="this.src+='<img src=x onerror=print()>'"/>`

calma que vou explicar cada pedacinho desse exploit.

<h3>Explicação sobre o exploit</h3>

vamos começar pelo: `<iframe></iframe>`, O elemento HTML <iframe> (ou elemento HTML inline frame) representa um contexto de navegação aninhado, efetivamente incorporando outra página HTML para a página atual. Em HTML 4.01, um documento pode conter uma cabeça e um corpo ou uma cabeça e um conjunto de quadros, mas não tanto um corpo e um conjunto de quadros.

ou seja, o <iframe> tem o poder de incorporar outras coisas, por exemplo, um video do youtube, só copiar e colar na sua pagina html e pronto!! você terá o video.
  
exemplo:
  
<img src=https://github.com/iRnx/Lab-Cross-Site-Scripting-XSS-/blob/main/imagens/Lab-6/Lab-6-part4.png>
   
Código copiado do iframe do youtube: <iframe width="545" height="409" src="https://www.youtube.com/embed/nmjdaBaZe8Y" title="Chris Brown - With You (Official Video)" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
  
<br>
  
Agora vocês já sabem como funciona o iframe, `<iframe src="link" ></iframe>` o src é para carregar alguma pagina que voce queira, geralmente seria o link da pagina que a vitíma iria acessar.

`<iframe src="https://www.link.com/#1533">` o jogo da velha seria a nossa hash e o numero é a nossa pesquisa como fizemos antes.

<br>
  
`<iframe src="https://www.link.com/#1533" onload="this.src+=<'img src=x onerror=print()>'"></iframe>` quando carregar a pagina, executará o evento onload, que está falando, que quando ele carregar o src da pagina irá receber o nosso código malicioso, e ficaria assim para a vitima: `<iframe src="https://0a4400f603e92417c05480600063003a.web-security-academy.net/#1533onload="this.src+='<img src=x onerror=print()>'"/>`



  































