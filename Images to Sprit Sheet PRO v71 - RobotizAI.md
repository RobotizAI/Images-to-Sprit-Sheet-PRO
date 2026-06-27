# Images to Sprit Sheet PRO - RobotizAI

O **Images to Sprit Sheet PRO** é uma ferramenta em HTML, CSS e JavaScript que transforma uma sequência de imagens em uma única **spritesheet**, com opção de exportar também um arquivo JSON com as posições dos frames.

## Abrir ou imprimir a página HTML completa

A página completa da ferramenta deve ficar no arquivo:

```text
index.html
```

> Importante: o GitHub não executa uma página HTML completa dentro do `README.md`.  
> O `README.md` serve para explicar o projeto. Para visualizar a ferramenta completa, abra o arquivo `index.html` ou publique o repositório com GitHub Pages.

### Ver localmente

1. Baixe ou clone este repositório.
2. Abra o arquivo `index.html` no navegador.
3. Para imprimir a página ou salvar como PDF, pressione `Ctrl + P` no navegador.

### Publicar com GitHub Pages

1. Envie o arquivo `index.html` para a raiz do repositório.
2. No GitHub, vá em **Settings**.
3. Entre em **Pages**.
4. Em **Build and deployment**, selecione:
   - **Source:** Deploy from a branch
   - **Branch:** `main`
   - **Folder:** `/root`
5. Clique em **Save**.
6. Depois de publicado, a página ficará em um endereço parecido com:

```text
https://RobotizAI.github.io/Images-to-Sprit-Sheet-PRO/
```

## Para que serve

Esta ferramenta serve para juntar várias imagens em uma única spritesheet. Isso é útil para animações, jogos, protótipos visuais, personagens, efeitos, frames de IA e qualquer fluxo que precise organizar imagens em uma grade única.

Ela permite configurar:

- quantidade de linhas;
- quantidade de colunas;
- número máximo de imagens;
- espaçamento entre frames;
- largura final;
- altura final;
- intervalo de seleção dos frames;
- exportação em PNG;
- exportação em JSON.

## Como usar

1. Clique em **Escolher arquivos**.
2. Selecione as imagens que deseja transformar em spritesheet.
3. Ajuste as linhas, colunas, tamanho final e espaçamento.
4. Clique em **Gerar Sprit Sheet**.
5. Confira o resultado no canvas.
6. Clique em **Download PNG** para baixar a spritesheet.
7. Clique em **Download JSON** para baixar o mapeamento dos frames.

## Arquivos principais

```text
index.html   Página completa da ferramenta
README.md    Explicação do projeto
```

## Observação sobre o README.md

Não cole todo o código HTML dentro do `README.md` esperando que o GitHub mostre a ferramenta funcionando. O GitHub remove ou bloqueia partes de HTML, CSS e JavaScript por segurança. A forma correta é manter o código completo em `index.html` e usar este `README.md` apenas como apresentação e instrução de uso.

## Direitos autorais

Copyright © 2026 RobotizAI. Todos os direitos reservados.

Este projeto é disponibilizado apenas para visualização e demonstração. Não é permitido copiar, modificar, redistribuir, vender, republicar ou criar obras derivadas sem autorização expressa por escrito da RobotizAI.
