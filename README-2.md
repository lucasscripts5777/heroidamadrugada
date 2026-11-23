# Herói da Madrugada

Jogo 3D mobile (HTML + Three.js). Téo tem os poderes da Sombra, e toda noite à 01:13 ela quer o corpo de volta. Durma antes disso.

## Arquivos

| Arquivo | O que é |
|---|---|
| `index.html` | O jogo inteiro |
| `manifest.json` | Config do app (nome, ícones, tela cheia, paisagem) |
| `sw.js` | Service worker (deixa o jogo funcionar offline) |
| `icon-192.png` / `icon-512.png` | O logo (losango roxo com os olhos da Sombra) nas duas resoluções |
| `icon-512-maskable.png` | O mesmo logo com margem de segurança, usado pelo Android quando recorta o ícone em círculo |
| `three.min.js` | **Recomendado**: Three.js r128 local, pro app funcionar 100% offline |

Sem o `three.min.js` o jogo baixa da internet (cdnjs) e funciona, mas só com conexão na primeira vez.
Para baixar: abra https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js, salve a página como `three.min.js` e coloque na raiz do repositório.

## Controles (teclado)

WASD mover · E falar/dormir · F consertar · X apagar (objetos, pessoas e construções) · R restaurar (até 20 s depois) · V voar · M moto · C criar poder · Shift acelerar

No celular: joystick na esquerda e os botões na direita.

## Menu inicial

- **Continuar**: retoma o jogo salvo (fica apagado se ainda não há save).
- **Novo jogo**: começa do zero (pede confirmação se já existe um save).
- **Opções**: áudio (volume geral e vento), gráficos (resolução, sombras, distância de visão, partículas, nuvens) e jogabilidade (sensibilidade e inversão da câmera, tamanho dos botões, tremor de câmera, velocidade do tempo). Fica salvo no aparelho.
- **Modo teste**: nada ali mexe no seu save.
  - **Modo corrida**: 3 voltas de moto do vazio contra Beto, Rita, Dora e Sandro numa pista pelas ruas do bairro, com nitro limitado.
  - **Treino de voo**: você nasce no céu e passa pelos 16 aros dourados em ordem. Cada aro dá pontos (mais perto do centro, mais pontos), combo e tempo extra.
  - **Modo livre**: poderes infinitos, sem a Sombra, com escolha de horário pelo menu de pausa.
  - **Cutscenes**: Téo acorda, Despertar da Sombra, Travessuras da Sombra, Sair da Terra, Mergulho em chamas, Final (a bolha do vazio) e Final só a explosão.

Durante o jogo, o botão de menu (três linhas, no canto esquerdo) ou a tecla Esc abre a pausa, com opções e saída.

## A Sombra

Às 01:13 ela acorda: o Téo treme, sobe no ar e se transforma numa silhueta preta de olhos brancos, mais alta que ele. Depois voa pela cidade fazendo 6 travessuras aleatórias. Em cada uma ela voa até o local, aponta, mexe as mãos para conjurar o poder e arremessa. A câmera acompanha como num filme. Ao fim, o Téo cai desacordado e acorda às 07:00.

## O final (7ª insônia)

Na virada da 6ª para a 7ª noite, a Sombra assume o corpo do mesmo jeito das outras (o Téo treme, sobe e se transforma), mas em vez de fazer travessuras ela voa para cima da cidade carregando um poder enorme. Uma esfera de vazio cresce entre as mãos dela, ela a arremessa e a bolha explode: primeiro vemos o vazio engolindo uma galáxia inteira, depois a bolha crescendo ao redor da Sombra e apagando a cidade. A cada metro que a bolha cresce, tudo que ela encosta é apagado com um clarão branco seguido de preto. Quando não sobra nada, aparece "A SOMBRA DESPERTOU" e o jogo volta ao começo com um novo jogo.

## Criador de poderes

Escreva na caixa de baixo ou toque nas palavras do cardápio (formas, elementos e modos). O botão **?** no topo mostra as instruções e some quando você toca de novo.

## Medo, colisão e sons

- Acertar pessoas ou construções com poder, ou apagá-las, faz os moradores gritarem e fugirem de você. Objetos comuns (carros, postes, árvores) não causam medo.
- Pessoas são sólidas: você esbarra e elas desviam. De moto ou voando rápido, você derruba quem estiver na frente.
- Tudo tem som: vidros e carros quebrando, alarmes, postes estourando, árvores estalando, desabamentos, gritos, pichação, fantasmas, chuva, e o "sugar" do vazio ao apagar e restaurar.

## Cutscene do espaço

Voe para cima, além das nuvens (altitude acima de ~185). O Téo atravessa as nuvens e aparece sobre a Terra, ouve um som distante vindo da cidade e mergulha de volta a 14.000 km/h em chamas. Ele cai na cidade, apaga o fogo e se levanta; a câmera e os controles voltam sozinhos, sem corte. Não acontece entre 01:10 e 07:00, quando a Sombra pode aparecer.

## Do GitHub até o APK, passo a passo

### 1. Subir no GitHub
1. Crie uma conta em github.com (se ainda não tiver) e clique em **New repository**.
2. Nome: `heroi-da-madrugada`, deixe **Public**, clique em **Create repository**.
3. Clique em **uploading an existing file** e arraste TODOS os arquivos da tabela acima (index, manifest, sw, os dois ícones e o three.min.js).
4. Clique em **Commit changes**. Os arquivos precisam ficar na raiz, não dentro de uma pasta.

### 2. Ligar o site (GitHub Pages)
1. No repositório: **Settings → Pages**.
2. Em **Source** escolha **Deploy from a branch**, branch **main**, pasta **/ (root)**, e **Save**.
3. Espere 1 a 2 minutos. O link aparece no topo da página: `https://SEU-USUARIO.github.io/heroi-da-madrugada/`
4. Abra o link no celular e confira se o jogo carrega.

### 3. Gerar o APK (PWABuilder)
1. Entre em https://www.pwabuilder.com
2. Cole o link do seu site e clique em **Start**.
3. Ele analisa o manifesto e o service worker. Os dois devem aparecer como válidos.
4. Clique em **Package for stores → Android**.
5. Preencha o nome do app e o Package ID (algo como `com.seunome.heroi`). Mantenha o modo de exibição em tela cheia e paisagem.
6. Em **Signing key** escolha **New** (ele cria uma chave pra você). **Baixe e guarde o arquivo da chave e a senha**, porque você precisa deles pra atualizar o app depois.
7. Clique em **Generate** e baixe o `.zip`. Dentro vem o `.apk` (para instalar direto) e o `.aab` (para a Play Store).
8. Mande o `.apk` pro celular e instale (permita "instalar apps de fontes desconhecidas" quando o Android pedir).

### 4. Atualizar o jogo depois
Suba os arquivos novos no GitHub (**Add file → Upload files**, mesmo nome sobrescreve) e dê commit. Se o app instalado continuar com a versão antiga, aumente o número em `const V='heroi-v7'` no `sw.js` (para `v5`, `v6`...), assim o cache antigo é descartado. Para o APK do PWABuilder normalmente não precisa gerar outro: o app carrega o site e se atualiza sozinho. Só gere um APK novo se mudar o nome, o ícone ou o manifesto.

## Ícones
Quando você mandar o logo, é só gerar uma versão 512×512 (`icon-512.png`) e outra 192×192 (`icon-192.png`) com esses nomes exatos.
