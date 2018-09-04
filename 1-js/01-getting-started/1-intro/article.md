# Uma Introdução ao JavaScript

Vejamos o que há de tão especial no JavaScript, o que podemos alcançar com ele e quais outras tecnologias são compatíveis com ele.

## O que é JavaScript?

_JavaScript_ foi originalmente criado para _"tornar as páginas da Web mais dinâmicas"_.

Os programas nesta linguagem são chamados _scripts_. Eles podem ser escritos diretamente no HTML e executados automaticamente conforme a página é carregada.

Os scripts são fornecidos e executados como texto simples. Eles não precisam de uma preparação especial ou de uma compilação para serem executados.

Neste aspecto, o JavaScript é muito diferente de outra linguagem chamada [Java](<https://pt.wikipedia.org/wiki/Java_(linguagem_de_programa%C3%A7%C3%A3o)>).

```smart header="Por quê <u>Java</u>Script?"
Quando o JavaScript foi criado, inicialmente tinha outro nome: "LiveScript". Mas a linguagem Java era muito popular na época, então foi decidido que o posicionamento de uma nova linguagem como um "irmão mais novo" de Java ajudaria no crescimento de JavaScript.

Mas à medida que evoluiu, o JavaScript tornou-se uma linguagem totalmente independente, com sua própria especificação chamada [ECMAScript] (http://pt.wikipedia.org/wiki/ECMAScript), e agora não tem nenhuma relação com Java.
```

Atualmente, o JavaScript pode executar não apenas no navegador, mas também no servidor ou, na verdade, em qualquer dispositivo em que exista um programa especial chamado [JavaScript engine](https://pt.wikipedia.org/wiki/Interpretador_de_JavaScript) .

O navegador tem um mecanismo incorporado, às vezes também é chamado de "máquina virtual JavaScript".

Motores diferentes têm diferentes "codinomes", por exemplo:

- [V8](<https://pt.wikipedia.org/wiki/V8_(JavaScript)>) -- no Chrome e Opera.
- [SpiderMonkey](https://en.wikipedia.org/wiki/SpiderMonkey) -- no Firefox.
- ...Existem outros codinomes como "Trident", "Chakra" para diferentes versões do IE, "ChakraCore" para Microsoft Edge, "Nitro" e "SquirrelFish" para Safari, etc.

Os termos acima são bons para lembrar, porque eles são usados ​​em artigos do desenvolvedor na internet. Nós vamos usá-los também. Por exemplo, se "um recurso X é suportado pela V8", provavelmente funcionará no Chrome e no Opera.

```smart header="Como funcionam os mecanismos?"
Motores são complicados. Mas o básico é fácil.

1. O mecanismo (incorporado se for um navegador) lê ("analisa") o script.
2. Em seguida, ele converte ("compila") o script para o idioma da máquina.
3. E então o código da máquina é executado bem rápido.

O mecanismo aplica otimizações em todos os estágios do processo. Ele ainda assiste ao script compilado enquanto é executado, analisa os dados que fluem através dele e aplica otimizações ao código da máquina com base nesse conhecimento. No final, os scripts são bem rápidos.
```

## O que o JavaScript do navegador pode fazer?

O que o JavaScript do navegador pode fazer

O JavaScript moderno é uma linguagem de programação "segura". Ele não fornece acesso de baixo nível à memória ou à CPU, porque foi criado inicialmente para navegadores que não exigem isso.

The capabilities greatly depend on the environment that runs JavaScript. For instance, [Node.JS](https://pt.wikipedia.org/wiki/Node.js) supports functions that allow JavaScript to read/write arbitrary files, perform network requests etc.

Os recursos dependem muito do ambiente que executa o JavaScript. Por exemplo, o [Node.JS](https://pt.wikipedia.org/wiki/Node.js) suporta funções que permitem JavaScript para ler / gravar arquivos arbitrários, executar solicitações de rede etc.

O JavaScript no navegador pode fazer tudo relacionado à manipulação de páginas da Web, interação com o usuário e o servidor da web.

Por exemplo, o JavaScript no navegador é capaz de:

- Adicionar novo HTML à página, alterar o conteúdo existente, modificar estilos.

- Reagir às ações do usuário, executar em cliques do mouse, movimentos de ponteiro, pressionamentos de tecla.

- Enviar solicitações pela rede para servidores remotos, baixar e fazer upload de arquivos (os chamados[AJAX](<https://en.wikipedia.org/wiki/Ajax_(programming)>) e [COMET](<https://en.wikipedia.org/wiki/Comet_(programming)>) tecnologias).
- Obter e definir cookies, fazer perguntas para o visitante, mostrar mensagens.

- Lembre-se dos dados no lado do cliente ("armazenamento local").

## O que o JavaScript no navegador NÃO FAZ?

As habilidades do JavaScript no navegador são limitadas em prol da segurança do usuário. O objetivo é impedir que uma página de web com má intenções acesse informações privadas ou prejudique os dados do usuário.

Os exemplos de tais restrições são:

- O JavaScript em uma página da Web pode não ler / gravar arquivos arbitrários no disco rígido, copiá-los ou executar programas. Não tem acesso direto às funções do sistema operacional.

Os navegadores modernos permitem que ele trabalhe com arquivos, mas o acesso é limitado e fornecido apenas se o usuário fizer determinadas ações, como "descartar" um arquivo em uma janela do navegador ou selecioná-lo por meio de uma tag `<input>`.

Existem maneiras de interagir com a câmera / microfone e outros dispositivos, mas eles exigem permissão explícita do usuário. Portanto, uma página habilitada para JavaScript não pode habilmente habilitar uma câmera web, observar os arredores e enviar as informações para o
[NSA](https://pt.wikipedia.org/wiki/Ag%C3%AAncia_de_Seguran%C3%A7a_Nacional).

- Diferentes guias / janelas geralmente não se conhecem. Às vezes, por exemplo, quando uma janela usa JavaScript para abrir a outra. Mas mesmo neste caso, o JavaScript de uma página não pode acessar o outro se eles vierem de sites diferentes (de um domínio, protocolo ou porta diferente).

Isso é chamado de "Política de mesma origem". Para contornar isso, _both pages_ deve conter um código JavaScript especial que manipule a troca de dados.

A limitação é novamente para a segurança do usuário. Uma página de `http://anysite.com` que um usuário abriu não deve conseguir acessar outra guia do navegador com o URL `http://gmail.com` e roubar informações de lá.

- O JavaScript pode se comunicar facilmente pela rede com o servidor de onde a página atual veio. Mas sua capacidade de receber dados de outros sites / domínios é prejudicada. Embora seja possível, requer acordo explícito (expresso em cabeçalhos HTTP) do lado remoto. Mais uma vez, isso é limitações de segurança.

![](limitations.png)

Esses limites não existem se o JavaScript for usado fora do navegador, por exemplo, em um servidor. Os navegadores modernos também permitem a instalação de plug-ins / extensões que podem receber permissões estendidas.

## O que faz JavaScript único?

Há pelo menos _três_ grandes coisas sobre o JavaScript:

```compare
+ Integração total com HTML / CSS.
+ Coisas simples feitas simplesmente.
+ Suportado por todos os principais navegadores e ativado por padrão.
```

Combinados, essas três coisas existem apenas em JavaScript e nenhuma outra tecnologia de navegador.

Isso é o que torna o JavaScript único. É por isso que é a ferramenta mais difundida para criar interfaces de navegador.

Enquanto planeja aprender uma nova tecnologia, é benéfico verificar suas perspectivas. Então, vamos seguir para as tendências modernas que incluem novas linguagens e habilidades de navegador.

## Languages "over" JavaScript

A sintaxe do JavaScript não atende às necessidades de todos. Pessoas diferentes querem recursos diferentes.

Isso é esperado, porque os projetos e requisitos são diferentes para todos.

Então, recentemente, uma infinidade de novas linguagens apareceu, que são convertidas para JavaScript antes de serem executadas no navegador.

Ferramentas modernas tornam a transpilação muito rápida e transparente, permitindo que os desenvolvedores codifiquem em outra linguagem e a autoconvertam "sob o capô".

Exemplos de tais idiomas:

- [CoffeeScript](http://coffeescript.org/) é um "açúcar sintático" para JavaScript, introduz uma sintaxe mais curta, permitindo escrever código mais preciso e claro. Normalmente, o Ruby faz o mesmo.

- [TypeScript](http://www.typescriptlang.org/) concentra-se na adição de "digitação estrita de dados", para simplificar o desenvolvimento e o suporte de sistemas complexos. É desenvolvido pela Microsoft.

- [Dart](https://www.dartlang.org/) é uma linguagem independente que possui seu próprio mecanismo que é executado em ambientes sem navegador (como aplicativos móveis). Ele foi inicialmente oferecido pelo Google como um substituto para o JavaScript, mas, a partir de agora, os navegadores exigem que ele seja transferido para o JavaScript como os acima.

Há mais. É claro que, mesmo se usarmos uma dessas linguagens, devemos também conhecer o JavaScript para entender realmente o que estamos fazendo.

## Sumário

- JavaScript foi inicialmente criado como uma linguagem somente de navegador, mas agora é usado em muitos outros ambientes também.
- Neste momento, o JavaScript tem uma posição única como a linguagem de navegador mais adotada com total integração com HTML / CSS.
- Existem muitos idiomas que são "transpilados" para JavaScript e fornecem determinados recursos. Recomenda-se dar uma olhada neles, pelo menos brevemente, depois de dominar o JavaScript.
