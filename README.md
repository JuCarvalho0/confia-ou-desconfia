Confia ou Desconfia?
Projeto final da disciplina de Introdução a Algoritmos (PUC Minas), desenvolvido com Python e Pygame.
Tema: Inteligência Artificial no Cotidiano: Aplicações e Uso Responsável.
> Situação: **Entrega 1 — proposta e definições iniciais.** A proposta completa está em [`docs/proposta.md`](docs/proposta.md).
Integrantes do grupo
Júlia Carvalho Silva
Estrutura do projeto
`main.py`: ponto de entrada da aplicação (será criado na Entrega 2).
`src/`: código-fonte principal do jogo.
`assets/`: imagens, fontes e sons.
`data/`: arquivos persistentes (afirmações e recorde).
`tests/`: testes unitários com `pytest`.
`docs/`: documentação do projeto, incluindo `proposta.md`.
Descrição do jogo
Cartas com afirmações sobre IA caem na tela. Algumas são confiáveis e outras duvidosas. O jogador controla um "Revisor" que deve coletar as confiáveis e desviar das duvidosas, podendo usar um número limitado de verificações. Depois de cada coleta, o jogo explica por que a afirmação era confiável ou duvidosa.
Objetivo do jogador
Chegar a 100 pontos sem perder as 3 vidas.
Regras e controles
Veja as seções 7 a 10 de `docs/proposta.md`.
Como executar (a partir da Entrega 2)
```
pip install -r requirements.txt
python main.py
```
Como executar os testes
```
python -m pytest
```