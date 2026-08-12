# Jogo da Velha Web - UNIFOR (Especificação Técnica)

## Objetivo e Escopo
O projeto consiste em uma aplicação web (Single Page Application) que permite disputas de Jogo da Velha com foco em usabilidade e identidade visual institucional.

## Funcionalidades Principais (RFs)
- **Modos de Jogo:** Suporte para dois jogadores locais (PVP) ou contra o computador (CPU).
- **Formatos de Partida:** Opção de Partida Única ou Melhor de 3 (MD3), onde o sistema controla rigorosamente o placar e as rodadas.
- **Lógica de Jogo:** Validação de 8 matrizes vitoriosas, detecção de empate (velha) e alternância automática de turnos começando pelo "Jogador X".
- **Inteligência Artificial:** No modo contra o computador, o sistema realiza jogadas automáticas escolhendo posições aleatórias após um intervalo de 400ms.

## Experiência do Usuário e Interface (UI/UX)
- **Identidade Visual:** Uso da paleta de cores da UNIFOR (Azul #003366, Laranja #d97706) e presença do subtítulo institucional.
- **Feedback Visual:** Exibição de uma linha contínua (fundo laranja sólido) sobre as células vitoriosas e disparo de confetes via CDN externo (Canvas Confetti) em caso de vitória final.
- **Feedback Sonoro:** Efeitos sonoros sintetizados via Web Audio API (sem arquivos locais). Foram utilizados osciladores com ondas *triangle* (jogadas), *square* (vitória) e *sawtooth* (empate).
- **Componentes de Tela:** Placar dinâmico, contador de rodadas, seletor de modo/formato com bloqueio durante a partida, tabuleiro 3x3 e botão de reinício.

## Especificações Técnicas (RNFs)
- **Tecnologia:** HTML, CSS e JavaScript puros em um único arquivo `index.html`. Não há dependências de arquivos de mídia locais (áudio é gerado nativamente e o script de confetes é importado via URL CDN).
- **Estado da Aplicação:** O sistema gerencia variáveis de controle do tabuleiro (`options`), turnos e pontuação (`currentPlayer`, `winsX`, `winsO`, `currentRound`), e de bloqueio e fluxo (`isRoundActive`, `isMatchOver`, `isCpuThinking`).
- **Regras de Negócio:** Bloqueio de células preenchidas, bloqueio de cliques do jogador enquanto a CPU processa a jogada, desabilitação dos seletores de formato enquanto o jogo está em andamento, e reset completo do estado ao clicar em reiniciar.

## Critérios de Aceite
Para o trabalho ser considerado concluído, a aplicação garante a fidelidade visual à UNIFOR, a autonomia do áudio sintetizado, o funcionamento correto do modo MD3 (finalizando com 2 vitórias e bloqueando o tabuleiro) e a execução fluida da jogada do computador.