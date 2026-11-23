Proposta do Projeto — Confia ou Desconfia?
Disciplina: Introdução a Algoritmos — PUC Minas
Tema obrigatório: Inteligência Artificial no Cotidiano: Aplicações e Uso Responsável
Entrega: Ponto de controle 01 — Definição do jogo
1. Integrantes do grupo
Júlia Carvalho Silva
2. Tema específico relacionado à IA
Confiabilidade das respostas de sistemas inteligentes, com apoio de dois subtemas: privacidade de dados e vieses em decisões automatizadas.
Assistentes virtuais, chatbots e sistemas de recomendação respondem com segurança e fluência, mas podem errar, inventar informações ou refletir dados enviesados. No dia a dia, muita gente aceita essas respostas sem conferir. O jogo trabalha exatamente essa situação: o jogador recebe "respostas da IA" e precisa decidir quais merecem confiança.
3. Aspecto de uso responsável abordado
Confiabilidade e análise crítica dos resultados: conferir antes de aceitar ou compartilhar.
Privacidade e segurança: não entregar dados pessoais (CPF, senhas) a aplicações inteligentes sem necessidade.
Inclusão e justiça: dados desequilibrados geram decisões injustas.
Transparência: sistemas devem explicar por que recomendam algo; por isso o jogo explica cada decisão do jogador.
4. Integração do tema com a jogabilidade
O tema é a mecânica, não só o cenário:
Cada carta que cai contém uma afirmação sobre IA, que pode ser confiável ou duvidosa.
O jogador deve coletar as confiáveis (compartilhar) e desviar das duvidosas; coletar uma duvidosa custa uma vida.
O jogador tem um número limitado de verificações (tecla ESPAÇO), que revelam se a carta mais próxima do chão é confiável. Isso representa o hábito de conferir em fontes antes de aceitar uma resposta.
Depois de cada carta coletada, o jogo mostra uma explicação curta do porquê a afirmação era confiável ou duvidosa (transparência e aprendizado).
Se o jogador deixa passar uma afirmação confiável, perde pontos: ignorar informação boa também tem custo.
5. Estilo do jogo
Jogo 2D de coleta e desvio de itens (estilo "catch the falling items") com elementos de perguntas e respostas. Visual simples, com formas geométricas e texto. O foco é a lógica e a jogabilidade, não os gráficos.
6. Objetivos do jogador
Alcançar a pontuação-meta coletando afirmações confiáveis e evitando as duvidosas, usando as verificações com sabedoria.
7. Regras previstas
O jogador começa com 3 vidas, 0 pontos e 2 verificações.
Cartas com afirmações caem do topo da tela em posições aleatórias.
Coletar carta confiável: +10 pontos.
Coletar carta duvidosa: -1 vida.
Deixar uma carta confiável cair sem coletar: -3 pontos (nunca abaixo de zero).
Deixar uma carta duvidosa cair: sem efeito (desvio correto).
ESPAÇO usa uma verificação e revela a carta mais baixa ainda não verificada (se houver verificações).
A velocidade de queda aumenta conforme a pontuação.
A cada carta coletada, aparece na tela uma explicação sobre a afirmação.
8. Condições de vitória e derrota
Vitória: atingir 100 pontos.
Derrota: perder as 3 vidas.
Ao final, o jogo mostra o resultado, a pontuação e o recorde salvo em arquivo, com opção de jogar de novo.
9. Elementos previstos
Jogador: barra ("Revisor") que se move na horizontal.
Cartas: retângulos com texto da afirmação; ao serem verificadas, ganham borda verde (confiável) ou vermelha (duvidosa).
HUD: pontos, vidas, verificações restantes e recorde.
Painel de explicação na parte inferior.
Telas: menu inicial, jogo e tela final (vitória/derrota).
Categorias das afirmações: confiabilidade, privacidade, vieses, conteúdo gerado por IA, saúde e recomendações.
10. Controles
Tecla	Ação
Seta esquerda / A	Mover para a esquerda
Seta direita / D	Mover para a direita
ESPAÇO	Usar uma verificação
ENTER	Iniciar partida / jogar de novo
ESC	Sair do jogo
11. Organização inicial do código
Seguindo o template da disciplina:
```
main.py              # ponto de entrada
src/config.py        # constantes (tamanhos, cores, regras)
src/dados.py         # leitura/validação das afirmações e do recorde (arquivos)
src/regras.py        # lógica do jogo, sem Pygame (testável)
src/jogo.py          # loop principal, eventos e desenho (Pygame)
data/itens.json      # banco de afirmações
data/recorde.txt     # maior pontuação
tests/               # testes com pytest
docs/proposta.md     # esta proposta
```
A lógica fica separada do Pygame para que as regras possam ser testadas sem abrir janela. Tudo é organizado em funções pequenas.
12. Estruturas de dados e conceitos da disciplina
Listas: cartas na tela, banco de afirmações.
Dicionários: cada afirmação (`texto`, `tipo`, `categoria`, `explicacao`), cada carta e o estado do jogo.
Tuplas: retângulos `(x, y, largura, altura)` e cores RGB.
Condicionais e laços: regras de coleta, colisão, loop principal.
Funções e modularização: módulos `config`, `dados`, `regras` e `jogo`.
Arquivos: leitura de `itens.json` e leitura/escrita de `recorde.txt`.
Documentação e testes: docstrings nas funções e testes com pytest.
13. Uso de arquivos
`data/itens.json`: afirmações, tipos e explicações, que podem ser ampliadas sem mexer no código.
`data/recorde.txt`: guarda a maior pontuação entre partidas.
Tratamento de erros: arquivo ausente ou inválido não deve derrubar o jogo (recorde assume 0; itens inválidos são descartados).
14. Testes planejados
Testes com `pytest` para as funções de lógica:
Pontuação ao coletar item confiável e perda de vida ao coletar duvidoso.
Penalidade ao perder item confiável (sem pontuação negativa).
Uso de verificação (com e sem verificações restantes).
Condições de vitória, derrota e jogo em andamento.
Velocidade de queda crescente e com limite máximo.
Colisão entre retângulos e limites de movimento do jogador.
Sorteio de itens e quebra de texto em linhas.
Validação e carregamento do arquivo de afirmações; leitura e gravação do recorde.
15. Recursos necessários
Python 3 e biblioteca Pygame.
pytest para testes.
Fonte padrão do Pygame (sem arquivos externos de imagem ou som previstos).
Conteúdo das afirmações escrito pelo próprio grupo.
16. Principais dificuldades esperadas
Quebrar texto longo para caber nas cartas.
Balancear a dificuldade (velocidade, frequência de cartas, quantidade de verificações).
Escrever afirmações claras, sem ambiguidade sobre ser confiável ou duvidosa.
Manter a lógica separada do Pygame para facilitar os testes.
Dividir as tarefas entre os integrantes e integrar o código no repositório.
17. Escopo mínimo da versão final
Menu, tela de jogo e tela final funcionando.
Movimento do jogador, cartas caindo, colisão, pontuação, vidas e verificações.
Pelo menos 12 afirmações em 4 categorias, carregadas de arquivo.
Vitória, derrota e recorde salvo em arquivo.
Explicação exibida após cada coleta.
README completo e testes passando.
18. Melhorias possíveis
Sons e imagens simples.
Mais afirmações e níveis de dificuldade.
Ranking com os cinco melhores resultados.
Tela de resumo com acertos e erros por categoria.
Itens especiais (por exemplo, "fonte oficial" que dá vida extra).
19. Declaração de originalidade
Declaramos que a ideia, as regras e o código deste projeto são de autoria do grupo, desenvolvidos para esta disciplina. Não reutilizamos jogos de semestres anteriores nem copiamos projetos de tutoriais ou repositórios. Qualquer recurso externo (imagem, som, fonte ou trecho de código) será identificado no README.md, com origem e licença.
20. Histórico de atualizações
Entrega 1 (15/11/2026): proposta inicial.