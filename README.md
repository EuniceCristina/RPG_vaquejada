Vaquejada RPG — O Desafio do Locutor
Um jogo de RPG em linguagem C inspirado nas vaquejadas e na cultura do sertão nordestino. Entre dados, desafios e decisões, o jogador acompanha a trajetória de um competidor em busca do título de campeão do circuito.
1. Identificação
- Estudante: Eunice Cristina de Araújo Silva
- Matrícula: 20260011578
- Projeto: Vaquejada RPG — O Desafio do Locutor
- Linguagem: C
2. História e objetivo
No coração do sertão, a poeira sobe, os portões da arena se abrem e o locutor anuncia o início de um grande circuito de vaquejada. O jogador assume o papel de um vaqueiro ou vaqueira que precisa superar provas cada vez mais difíceis, administrar sua resistência e conquistar o respeito da torcida.

A jornada é dividida em três etapas: Mirim, Aspirante e Profissional. Cada etapa apresenta bois com diferentes níveis de resistência, eventos no percurso e um desafio final contra um boi-chefe. O objetivo é completar as derrubadas exigidas, vencer o chefe de cada etapa e chegar ao fim do circuito como grande campeão.

A ambientação e os diálogos do locutor fazem parte da experiência: eles apresentam os acontecimentos da pista, as conquistas e os momentos de dificuldade.
3. Personagens jogáveis
No início da partida, o jogador escolhe um dos três competidores. Cada personagem possui atributos próprios de vida, ataque, força, defesa, agilidade, inteligência e chance de fuga, além de equipamentos e uma habilidade especial.
Personagem	Perfil	Equipamentos	Habilidade especial
Vaqueiro Nym	Equilibrado, com boa combinação de ataque e mobilidade	Cavalo Ventania e gibão de couro	Laço Certeiro: fortalece uma puxada contra o boi
Vaqueira Marta	Voltada à força e à resistência	Cavalo Trovão, perneira reforçada e laço pesado	Puxada de Ferro: reduz a dificuldade do boi
Zé Relâmpago	Ágil, com foco em velocidade e evasão	Cavalo Seta, esporas e chapéu de couro	Corrida Relâmpago: aumenta a chance de fuga


A escolha influencia a maneira de enfrentar os desafios. Os atributos e as recompensas conquistadas são mantidos ao longo das etapas; as condições de uso das habilidades seguem o controle implementado no código.
4. Fases e desafios
Etapa	Bois comuns	Chefe	Objetivo
1 — Mirim	Pintado e Malhado	Boi Caboclo	Realizar 2 derrubadas comuns e vencer o chefe
2 — Aspirante	Corrente e Ventania	Boi Ferradura	Realizar 3 derrubadas comuns e vencer o chefe
3 — Profissional	Tempestade e Aço	Boi Lendário Corone	Realizar 4 derrubadas comuns e vencer o chefe final


Os bois não são monstros fantásticos: são os desafios da arena, adaptados à mecânica de RPG. Cada um tem resistência, reação, dificuldade e uma recompensa em experiência (XP). Conforme o jogador avança, os adversários se tornam mais exigentes.
5. Como jogar
Escolha e movimentação
1. Execute o jogo e leia a introdução apresentada pelo locutor.
2. Escolha um dos três personagens digitando o número correspondente.
3. Pressione Enter quando solicitado para acompanhar a narrativa.
4. A cada rodada, o jogo sorteia o avanço pelo tabuleiro e apresenta o evento da casa alcançada.
5. Conclua as derrubadas necessárias e enfrente o chefe para avançar à próxima etapa.
O tabuleiro possui 12 casas, com eventos como trechos vazios, combates, tesouros, recuperação de vida, armadilhas e o desafio do chefe. O avanço é determinado por sorteio no programa, sem que o jogador precise digitar o resultado de um dado.
Ações durante o combate
Quando um boi entra na pista, o jogador escolhe uma ação pelo número mostrado no menu:
Opção	Ação	Efeito
1	Derrubar boi	Faz uma puxada para reduzir a resistência do adversário
2	Segurar o boi	Aumenta temporariamente a defesa do vaqueiro
3	Usar habilidade especial	Ativa a habilidade própria do personagem, quando disponível
4	Pular vez / tentar fuga	Faz uma tentativa de escapar do confronto


Depois da ação, se o boi ainda tiver resistência e não houver fuga, ele reage. O jogador deve acompanhar sua vida e a resistência do boi antes de decidir o próximo movimento.
Dados, cálculos e recompensas
O combate usa um dado virtual de 20 faces (d20). Na puxada comum, os cálculos principais são:
Força da puxada = d20 + ataque do vaqueiro + bônus
Dano ao boi = máximo(1, força da puxada − dificuldade do boi)

Reação do boi = d20 + reação do boi
Perda de vida = máximo(1, reação do boi − defesa do vaqueiro)
A habilidade especial pode modificar esses efeitos. Ao vencer um boi, o jogador recebe XP; casas de tesouro podem melhorar atributos, enquanto casas de cura recuperam vida e armadilhas a reduzem. A fuga encerra a tentativa sem contar uma derrubada.

Vitória: completar as derrubadas e vencer o chefe de cada uma das três etapas. Derrota: ficar com a vida zerada, encerrando a partida.
6. Organização e construção do projeto
O projeto foi desenvolvido em C, com uma estrutura baseada em funções para separar as responsabilidades do jogo:
- Dados do jogo: struct Personagem guarda atributos, equipamentos e habilidade; struct Boi reúne as características de cada adversário.
- Ações: o enum AcaoCombate identifica as opções do menu por nomes como DERRUBAR_BOI, SEGURAR_BOI, USAR_HABILIDADE e PULAR_VEZ.
- Combate: puxadaVaqueiro(), resistenciaBoi(), useHabilidade() e pularVez() processam as ações e seus resultados.
- Progressão: combate() organiza os confrontos comuns; missao() apresenta os chefes; avancaCasa() controla a movimentação e os eventos; iniciarFase() prepara cada etapa.
- Interface: funções como abertura(), apresentarFase(), titulo(), locutor() e esperarEnter() conduzem a narrativa no terminal.
- Execução: main() inicializa o jogo, permite escolher o personagem e conduz as três fases.
A divisão em funções facilita a leitura, a manutenção e a evolução do código. O projeto utiliza bibliotecas padrão como stdio.h, stdlib.h, string.h e time.h, incluindo sorteios com rand() e inicialização da sequência aleatória com srand().
Ferramentas e recursos
- Linguagem C: implementação das regras, estruturas de dados e lógica de jogo.
- GCC: compilação do código-fonte.
- Terminal: interação com menus, mensagens e comandos de entrada.
- Git/GitHub: organização e disponibilização do projeto.
- ChatGPT / OpenAI ImageGen: apoio à criação de ilustrações opcionais dos personagens e bois, quando incluídas no repositório.
7. Compilação e execução
Pré-requisito: ter o compilador GCC instalado e acessível pelo terminal. Abra o terminal na pasta em que está o arquivo main.c.

Windows (Prompt de Comando ou PowerShell):
gcc main.c -o main.exe
.\main.exe
Linux:
gcc main.c -o main
./main
macOS (com GCC ou compilador C compatível):
cc main.c -o main
./main
Observação de compatibilidade: o código utiliza system("cls") para limpar a tela no Windows. Em Linux e macOS, adapte limparTela() para usar um comando compatível, como system("clear"), antes de executar.

8. Arquivos e ilustrações
projeto/
├── main.c
├── README.md
└── personagens/
# ilustrações opcionais

As imagens, quando presentes, representam os personagens e os bois das três etapas. Foram produzidas com auxílio do OpenAI ImageGen, a partir de um prompt de ilustração de RPG ambientado em uma arena de vaquejada nordestina, com vestimentas de couro, paisagem do sertão e atmosfera cinematográfica. Elas enriquecem a apresentação do projeto, mas não são necessárias para jogar no terminal.
10. Vídeo de demonstração
Demonstração da execução e das principais mecânicas: [inserir link do vídeo]
Projeto acadêmico desenvolvido para aplicar estruturas de dados, enumerações, funções, estruturas de decisão, repetição e geração de números aleatórios na linguagem C.
