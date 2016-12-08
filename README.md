### Resumo

Esta modificação foi desenvolvida no formato OCMod, e transforma todas as urls padrões de sua loja em urls amigáveis.

Uma das grandes vantagens desta modificação é que as urls amigáveis colaboram diretamente no SEO, e são visualmente melhores.

Caso deseje doar um valor para contribuir com este trabalho continuo e sempre gratuito, clique no botão abaixo:

[![alt tag](https://www.paypalobjects.com/pt_BR/BR/i/btn/btn_donateCC_LG.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=7G9TR9PXS6G5J)

### Instalação

 1. Baixe a modificação no link: https://github.com/opencartbrasil/todas-url-amigaveis/releases. Localize a versão mais atual e compatível do arquivo "todas-url-amigaveis.ocmod.zip".
 2. Na administração da loja acesse o menu Extensions->Extension Installer (Extensões->Instalador).
 3. Na página do instalador, clique no botão Upload e selecione o arquivo 'todas-urls-amigaveis.ocmod.zip' (que você baixou deste repositório), e aguarde a conclusão da instalação automática.
 5. Após a instalação, acesse o menu Extensions->Modifications (Extensões->Modificações) e clique no botão Refresh (Atualizar), para que a modificação instalada seja incrementada na loja, lembrando que não é o botão "Atualizar" do navegador, e sim o botão "Atualizar" na cor azul ao lado do botão laranja e vermelho na tela do próprio OpenCart.

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

Para desinstalar a modificação, na administração da loja, acesse o menu Extensions->Modifications (Extensões->Modificações) e selecione a modificação com o nome 'Todas as URLs amigáveis', depois clique no botão Delete (Excluir), e no botão Refresh (Atualizar).

### Atualização

Acesse a administração da loja e execute o procedimento de Desinstalação, depois execute o procedimento de Instalação.

### Dúvidas

O OCMod (OpenCart Modification) é nativo do OpenCart, ou seja, não é necessário instalar nenhum complemento no OpenCart para utilizar modificações ou extensões no formato OCMod, para mais informações sobre o OCMod, segue o link:

https://github.com/opencart/opencart/wiki/Modification-System

### O arquivo alterado virtualmente através do OCMod é:

Até a versão 2.1.0.2:

catalog/controller/common/seo_url.php

Após a versão 2.1.0.2:

catalog/controller/startup/seo_url.php

### Como contribuir

 1. Faça um Fork do projeto e edite os arquivos que desejar.
 2. Faça um Pull para que suas sugestões de melhorias sejam avaliadas e aceitas, caso aprovadas.
 3. Abra uma Inssue com sua dúvida ou sugestão.

### Licença

[GNU General Public License version 3 (GPLv3)](https://github.com/opencartbrasil/todas-urls-amigaveis/blob/master/LICENSE)
