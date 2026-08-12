# Relatório de Uso de Inteligência Artificial

**Ferramenta de IA Utilizada:** Google Gemini

## 1. Histórico de Prompts e Interações

Durante o desenvolvimento deste projeto, a IA foi utilizada para gerar a base do código (HTML/CSS/JS) e para auxiliar na configuração do repositório Git/GitHub. 

**Principais Prompts enviados:**
1. *Contextualização e Estrutura:* "Irei mandar um conjunto de instruções para que me ajude a concluir... [Envio da estrutura obrigatória de pastas e regras de entrega]."
2. *Geração de Código:* "[Envio do Resumo Técnico/CDU do projeto] contendo os Modos de Jogo, UI/UX, paleta da UNIFOR e Inteligência Artificial."
3. *Comando de Correção:* "O código está com erros, o som está errado e o jogo está incompleto, eu irei mandar a pasta para que reveja e corrija."

## 2. Erros da IA em relação ao CDU e Correções Ordenadas

Após a geração da primeira versão do código, realizei testes e identifiquei que a IA não havia cumprido alguns pontos do Caso de Uso (CDU). Ordenei a correção através de prompt, e as seguintes falhas foram ajustadas:

*   **Erro 1 - Áudio Sintetizado Inadequado:** A primeira versão do áudio via Web Audio API estava genérica e pouco agradável.
    *   **Correção:** Ordenei a revisão do som. A IA ajustou as frequências e os tipos de onda (triangle, square e sawtooth) para diferenciar as jogadas de X e O, e criar sons específicos para vitória e empate.
*   **Erro 2 - Falhas na Lógica de Estado (Jogo Incompleto):** O jogo estava permitindo cliques enquanto a CPU processava sua jogada e a transição de rodadas no modo MD3 (Melhor de 3) apresentava falhas no bloqueio do tabuleiro.
    *   **Correção:** Ordenei a revisão da lógica. A IA implementou flags de bloqueio estritas (`isCpuThinking`, `isMatchOver`, `isRoundActive`), garantindo que o delay de 400ms da CPU funcionasse com fluidez sem que o jogador pudesse trapacear, além de garantir o fim do jogo exatamente nas 2 vitórias do MD3.

## 3. Autoavaliação dos Critérios de Aceite

| Critério | Descrição | Status | Justificativa |
| :--- | :--- | :--- | :--- |
| **CA-01** | Fidelidade Visual (Paleta UNIFOR) | ✅ Atendido | O CSS utiliza exatamente as cores institucionais e o feedback de linha contínua exigido. |
| **CA-02** | Autonomia de Áudio (Web Audio API) | ✅ Atendido | Todos os sons são gerados nativamente pelo navegador, sem dependência de arquivos `.mp3`. |
| **CA-03** | Modo Melhor de 3 (MD3) | ✅ Atendido | O sistema controla as rodadas e encerra o torneio assim que um jogador alcança 2 vitórias. |
| **CA-04** | Inteligência Artificial (CPU) | ✅ Atendido | A CPU realiza jogadas com delay de 400ms e a interface é bloqueada enquanto ela "pensa". |
| **CA-05** | Estrutura SPA / Arquivo Único | ✅ Atendido | Todo o código está contido no arquivo `src/index.html`. |
| **CA-06** | Sem Dependências Locais de Mídia | ✅ Atendido | O áudio é sintetizado e o script de confetes vem de uma CDN externa. |
| **CA-07** | Estrutura de Repositório | ✅ Atendido | As pastas `docs` e `src`, junto aos arquivos `.md`, seguem a árvore exigida. |