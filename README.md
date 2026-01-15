
# Jogo 2048 (C + Allegro 5)

Recriação do clássico **2048** desenvolvida em **C** usando a biblioteca **Allegro 5**.  
Projeto acadêmico com foco em lógica de movimentação/combinação de blocos, gerenciamento de sprites, sons e loop de jogo.  

> **Stack principal:** C, Allegro 5  
> **Resolução padrão:** 700×700 px (janela fixa)  
> **Plataforma alvo:** Windows (binário `jogo.exe` incluso)

https://github.com/JoyFigueiredo/Jogo2048

---

## 🎮 Gameplay (como jogar)

- Use as **setas do teclado** (↑ ↓ ← →) para mover todos os blocos na grade.
- Blocos com o **mesmo valor** que colidem se **fundem**, somando os valores.
- O objetivo é alcançar o bloco **2048** — continue jogando para superar sua própria pontuação!

---

## ✨ Funcionalidades

- Janela gráfica (700×700) renderizada com **Allegro 5**.
- Sprites e fontes customizadas (pastas `imagens/` e `fontes/`).
- Efeitos sonoros em eventos (pasta `Sons/`).
- Lógica de bloqueio/combinação para evitar múltiplas fusões no mesmo passo.
- Binário Windows (`jogo.exe`) para execução rápida.

> A resolução e a inicialização do Allegro são configuradas no código-fonte (vide `inicio.c`). [2](https://github.com/JoyFigueiredo/Jogo2048/blob/main/inicio.c)

---

## 🗂️ Estrutura do repositório
```
Jogo2048/
       ├─ .vscode/           # Tarefas de build (VS Code)
       ├─ Sons/              # Efeitos sonoros do jogo
       ├─ allegro/           # Recursos/headers/libs Allegro (apoio)
       ├─ fontes/            # Arquivos de fontes
       ├─ imagens/           # Sprites, plano de fundo e peças
       ├─ README.md          # (este arquivo)
       ├─ inicio.c           # Inicialização do Allegro e recursos
       ├─ main.c             # Loop principal / lógica do jogo
       ├─ jogo.exe           # Executável para Windows
       └─ tasks.json         # Tarefa de compilação (VS Code)
```
> A estrutura e os arquivos foram obtidos diretamente do repositório. [1](https://github.com/JoyFigueiredo/Jogo2048)

---

## ▶️ Executar (Windows)

### Opção 1 — Executável pronto
1. Baixe/clique duas vezes em **`jogo.exe`** na raiz do repositório.
2. Garanta que as **pastas de recursos** (`imagens/`, `fontes/`, `Sons/`) estejam no **mesmo diretório** do executável.

> O repositório já inclui `jogo.exe` na raiz. [1](https://github.com/JoyFigueiredo/Jogo2048)

### Opção 2 — Compilar do zero (MinGW + Allegro 5)
> Recomendado para quem deseja ver/alterar o código.

**Pré‑requisitos**
- **MinGW-w64** (gcc) e **pkg-config** no PATH
- **Allegro 5** (headers e libs) instalados ou disponíveis localmente  
  *(o projeto inclui uma pasta `allegro/` com materiais de apoio; ajuste os caminhos conforme sua instalação).*

**Comandos exemplo (ajuste conforme seu ambiente):**
```bash
# No diretório do projeto
gcc -O2 -Wall -Iallegro/include ^
  main.c inicio.c -o jogo.exe ^
  -Lallegro/lib -lallegro-5 -lallegro_main-5 -lallegro_image-5 -lallegro_font-5 -lallegro_ttf-5 -lallegro_primitives-5 -lallegro_audio-5 -lallegro_acodec-5
```
> O código inicializa subsistemas `image`, `font`, `audio` e cria a tela **700×700** via Allegro.

---

## ⌨️ Controles

- **← → ↑ ↓**: movimenta as peças.
- **ESC**: (se implementado pelo seu build) sair do jogo.

---

## 🧩 Lógica em alto nível

1. **Input**: leitura das setas; define direção do movimento.
2. **Compactação/Movimento**: desloca peças até colisão ou borda.
3. **Combinação**: funde pares iguais (com “bloqueio” para evitar dupla fusão no mesmo passo).
4. **Spawning**: cria uma nova peça (2/4) em célula vazia após um movimento válido.
5. **Game Over**: ocorre quando não há movimentos válidos.

> A estrutura de dados para peças/estados e vetores de imagens/sons é visível em `inicio.c` (e no `main.c`).
> 
---

## 🛠️ Desenvolvimento

- Recomendado usar **VS Code** (tarefa `tasks.json` já no projeto).
- Estrutura compatível com Windows; para Linux/macOS, ajuste links do Allegro (via `pkg-config allegro-5 allegro_image-5 ...`).

---

## 📚 Referências & Créditos

- Trabalho realizado em dupla com **@sarahxwaves**.  
- Biblioteca **Allegro 5** (renderização, imagem, fonte, áudio) — inicialização e uso podem ser vistos no arquivo `inicio.c`.

---

## ✅ Status do projeto

Concluído para fins acadêmicos, com espaço para melhorias (animações, placar persistente, UI responsiva).

---

## 🗺 Roadmap (sugestões)

- [ ] Animações suaves nas fusões (interpolação/frames).
- [ ] Persistência de **high score** em arquivo.
- [ ] Tela de **Game Over** com opção de Reiniciar.
- [ ] Modo **4×4 / 5×5** configurável.
- [ ] Suporte multiplataforma (Linux/macOS com `pkg-config`).



