### QUANTUM RANDOM WALLK - Da Nanociência à Música Quântica

#### INTRODUÇÃO

Este projeto foi desenvolvido como um Trabalho Didático para as disciplinas de Introdução à Nanociência e Nanotecnologia e Modelagem Matemática na UFABC. O objetivo é demonstrar como partículas em nanoescala não seguem trajetórias clássicas, mas sim probabilísticas, utilizando a computação quântica como ponte. 

###  Conceitos Explorados

Superposição Quântica: Utilizada para permitir que o "caminhante" (walker) explore múltiplos caminhos simultaneamente.
Random Walks Quânticos: Modelagem de distribuições de probabilidade não triviais que geram padrões caóticos e fractais.Sonificação de Dados: Conversão de intensidades de pixels da simulação em notas musicais (MIDI).

### Tecnologias UtilizadasPython (Linguagem principal).Qiskit / AerSimulator: 

Para a criação e simulação do circuito quântico.PIL (Pillow) & Matplotlib: Para processamento e visualização da matriz de probabilidades em imagem.Mido: Para a geração do arquivo MIDI a partir dos dados visuais.Guitar Pro: Utilizado para a transcrição e geração da partitura final.

### O Fluxo do Projeto Simulação: Um circuito quântico de $n$ qubits cria uma superposição total.

Mapeamento: Os resultados das medições são organizados em uma matriz de probabilidade $4 \times 4$ (para 2 qubits por eixo).

Imagem: A matriz é normalizada e redimensionada para criar uma visualização "fractal-like".Música: A média da intensidade dos pixels é mapeada para uma escala musical (C4 a C6), gerando uma composição aleatória.

### Como ExecutarInstale as dependências: pip install qiskit qiskit-aer numpy matplotlib pillow mido.Execute o script de simulação para gerar o arquivo quantum_random_walks.png.
Execute o script de sonificação para gerar o arquivo quantum_music.mid.
