# Recriando-o-Famoso-Jogo-do-Dinossauro-sem-Internet

[1]: https://www.techtudo.com.br/dicas-e-tutoriais/2019/11/como-jogar-o-jogo-do-dinossauro-do-google-online-no-navegador-chrome.ghtml ""
[2]: https://www.youtube.com/watch?v=M22tbRcVm7k ""
[3]: https://www.youtube.com/watch?v=Cj7_1HEc8-Y ""
[4]: https://maisgeek.com/como-hackear-o-jogo-de-dinossauro-oculto-do-google-chrome/ ""
[5]: https://www.youtube.com/watch?v=t4AJQ6LwSVo ""
[6]: https://bing.com/search?q=como+criar+o+jogo+do+dinossauro+do+Chrome ""
[7]: https://github.com/rdeconti/Projeto-DIO-HTML-Jogo-Dinossauro ""
[8]: https://www.dio.me/projects/recriando-o-famoso-jogo-do-dinossauro-sem-internet ""
[9]: https://go.hotmart.com/B85475801M ""
[10]: https://github.com/ProgramandoGames ""
[11]: https://drive.google.com/file/d/1exKk ""
[12]: https://github.com/FabricaDeSinapse/U ""
[13]: https://fabricadesinapse.github.io/Un ""
[14]: https://github.com/paulosalvatore/Jog ""
[15]: https://paulosalvatore.github.io/Jogo ""
[16]: https://github.com/FabricaDeSinapse/ ""
[17]: https://github.com/paulosalvatore ""

Vamos dividir o projeto em módulos e detalhar cada um deles:

### Módulo 1: Estrutura Básica com HTML
Começaremos criando a estrutura básica do jogo usando HTML. Isso incluirá a criação de um arquivo `index.html` que conterá elementos como a `div` do jogo, onde o dinossauro e os obstáculos serão exibidos.

```html
<!DOCTYPE html>
<html lang="pt">
<head>
    <meta charset="UTF-8">
    <title>Jogo do Dinossauro</title>
</head>
<body>
    <div id="jogo"></div>
</body>
</html>
```

### Módulo 2: Estilização com CSS
Em seguida, adicionaremos estilos básicos com CSS. Criaremos um arquivo `styles.css` para definir como o jogo deve parecer visualmente, incluindo o tamanho e a cor do fundo do jogo, bem como o estilo do dinossauro e dos obstáculos.

```css
#jogo {
    width: 600px;
    height: 150px;
    background-color: #f7f7f7;
    overflow: hidden;
    position: relative;
}
```

### Módulo 3: Lógica do Jogo com JavaScript
A parte mais importante é a lógica do jogo, que será escrita em JavaScript. Criaremos um arquivo `script.js` para lidar com a inicialização do jogo, os controles do dinossauro (como pular), a criação de obstáculos e a lógica de pontuação.

```javascript
const jogo = document.getElementById('jogo');
let isJumping = false;

function handleKeyUp(event) {
    if (event.keyCode === 32) {
        if (!isJumping) {
            jump();
        }
    }
}

function jump() {
    isJumping = true;
    // Lógica para fazer o dinossauro pular
    // ...
    isJumping = false;
}

document.addEventListener('keyup', handleKeyUp);
```

### Módulo 4: Animações com CSS e JavaScript
Por fim, usaremos CSS para criar animações básicas, como o dinossauro pulando e os obstáculos se movendo. Combinaremos isso com JavaScript para atualizar a posição dos elementos e criar a sensação de movimento no jogo.

```css
.dinossauro {
    animation: jump 0.5s;
}

@keyframes jump {
    /* Definir quadros-chave para a animação de pulo */
}
```

```javascript
// Atualizar a posição dos obstáculos
```

Esses são os módulos básicos para criar uma versão simplificada do jogo do dinossauro. Você pode expandir cada módulo com mais funcionalidades, como aumentar a dificuldade com o tempo, adicionar pontuação e vidas, ou até mesmo incluir sons e gráficos mais avançados.

[1]: https://maisgeek.com/como-hackear-o-jogo-de-dinossauro-oculto-do-google-chrome/ ""
[2]: https://dino-chrome.com/pt ""
[3]: https://github.com/MarcosAllysson/jogo-dinossauro-javascript-html-css ""
[4]: https://techbit.pt/troque-personagem-jogo-dinossauro-chrome-sonic/ ""
[5]: https://navhow.com/pt/how-to-unlock-the-google-chrome-dinosaur-game/ ""

Aqui está um exemplo de código completo para um jogo do dinossauro semelhante ao do Chrome, utilizando HTML, CSS e JavaScript. Este exemplo é simplificado e serve como um ponto de partida que você pode expandir e personalizar.

### HTML (index.html)
```html
<!DOCTYPE html>
<html lang="pt">
<head>
    <meta charset="UTF-8">
    <title>Jogo do Dinossauro</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div id="jogo">
        <div id="dinossauro"></div>
        <div id="obstaculo"></div>
    </div>
    <script src="script.js"></script>
</body>
</html>
```

### CSS (styles.css)
```css
#jogo {
    width: 600px;
    height: 200px;
    background-color: #f7f7f7;
    overflow: hidden;
    position: relative;
}

#dinossauro {
    width: 40px;
    height: 40px;
    background-color: #000;
    position: absolute;
    bottom: 0;
    left: 50px;
}

#obstaculo {
    width: 20px;
    height: 20px;
    background-color: red;
    position: absolute;
    bottom: 0;
    right: 0;
}
```

### JavaScript (script.js)
```javascript
const dino = document.getElementById('dinossauro');
const obstaculo = document.getElementById('obstaculo');
let isJumping = false;
let gravity = 0.9;
let position = 0;

function handleKeyUp(event) {
    if (event.keyCode === 32) {
        if (!isJumping) {
            jump();
        }
    }
}

function jump() {
    isJumping = true;
    let upTimerId = setInterval(() => {
        if (position >= 150) {
            clearInterval(upTimerId);
            let downTimerId = setInterval(() => {
                if (position <= 0) {
                    clearInterval(downTimerId);
                    isJumping = false;
                }
                position -= 5;
                position *= gravity;
                dino.style.bottom = position + 'px';
            }, 20);
        }
        position += 30;
        position *= gravity;
        dino.style.bottom = position + 'px';
    }, 20);
}

function startGame() {
    obstaculo.classList.add('obstaculo-move');
}

document.addEventListener('keyup', handleKeyUp);
startGame();
```

### Animação do Obstáculo (styles.css)
```css
.obstaculo-move {
    animation: move 1s infinite linear;
}

@keyframes move {
    0% {
        right: -20px;
    }
    100% {
        right: 600px;
    }
}
```

Este código cria um jogo básico onde o dinossauro pode pular com a barra de espaço, e um obstáculo se move continuamente da direita para a esquerda. Você pode adicionar mais funcionalidades, como detecção de colisão, pontuação e níveis de dificuldade para tornar o jogo mais complexo e divertido.

Para ver exemplos de códigos completos e projetos já desenvolvidos, você pode visitar repositórios no GitHub que contêm implementações do jogo do dinossauro¹[3]. Lá, você encontrará diversos exemplos que podem servir de inspiração para o seu projeto.
