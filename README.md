[![license][licenca-badge]][LICENSE]

### Apresentação

Esta modificação foi desenvolvida no formato OCMOD, e transforma todas as URLs padrões de sua loja em URLs amigáveis.

Uma das grandes vantagens desta modificação é que as URLs amigáveis colaboram diretamente no SEO, e são visualmente melhores.

### Instalação

 1. Acesse o link: https://www.opencart.com/index.php?route=marketplace/extension/info&extension_id=22038.
 2. Localize a versão mais atual e compatível com sua versão do OpenCart e faça o download.
 3. Na administração da loja acesse o menu Extensões→Instalador (Extensions→Installer).
 4. Na página do instalador, clique no botão Upload e selecione o arquivo 'todas-urls-amigaveis.ocmod.zip' (que você baixou deste repositório), e aguarde a conclusão da instalação automática.
 5. Após a instalação, acesse o menu Extensões→Modificações (Extensions→Modifications) e clique no botão Refresh (Atualizar), para que a modificação instalada seja incrementada na loja, lembrando que não é o botão "Atualizar" do navegador, e sim o botão "Atualizar" na cor azul ao lado do botão laranja e vermelho na tela do próprio OpenCart.

### Configuração

Após a instalação nenhuma configuração é necessária.
 
#### Corrigindo erro no carrinho e na busca

Assumindo que seu tema utiliza a mesma base do tema padrão do OpenCart, você precisa fazer uma modificação no arquivo catalog/view/javascript/common.js

No arquivo common.js, localize as linhas de código abaixo:

```js
if (getURLVar('route') == 'checkout/cart' || getURLVar('route') == 'checkout/checkout') {
 location = 'index.php?route=checkout/cart';
} else {
 $('#cart > ul').load('index.php?route=common/cart/info ul li');
}
```

E substitua todas as ocorrências delas pelas linhas de código abaixo:

```js
var getURlRewrite = $(location).attr('href').split('/').pop();

if (getURLVar('route') == 'checkout/cart' || getURLVar('route') == 'checkout/checkout') {
 location = 'index.php?route=checkout/cart';
} else if (getURlRewrite == 'carrinho' || getURlRewrite == 'finalizar') {
 location = 'carrinho';
} else {
 $('#cart > ul').load('index.php?route=common/cart/info ul li');
}
```

Localize a linha de código abaixo:

```js
url = $('base').attr('href') + 'index.php?route=product/search';
```

E substitua todas as ocorrências dela pela linha de código abaixo:

```js
url = $('base').attr('href') + 'busca';
```

Salve as alterações no arquivo e limpe o cache do seu navegador para remover a versão em cache do arquivo common.js.

### Desinstalação

Para desinstalar a modificação, na administração da loja, acesse o menu Extensões→Modificações (Extensions→Modifications) e selecione a modificação com o nome 'Todas as URLs amigáveis', depois clique no botão Excluir (Delete), e no botão Atualizar (Refresh).

### Atualização

Acesse a administração da loja e execute o procedimento de Desinstalação, depois execute o procedimento de Instalação.

### Dúvidas

O OCMOD (OpenCart Modification) é nativo do OpenCart, ou seja, não é necessário instalar nenhum complemento no OpenCart para utilizar modificações ou extensões no formato OCMOD, para mais informações sobre o OCMOD, segue o link para mais informações:

https://github.com/opencart/opencart/wiki/Modification-System

[licenca-badge]: https://img.shields.io/badge/licença-GPLv3-blue.svg
[LICENSE]: ./LICENSE
