<img src="title.PNG">

### <img src="flask.gif" alt="Icone de física" width="50" height="50">  QUANTUM RANDOM WALLK - Da Nanociência à Música Quântica

### INTRODUÇÃO

Este projeto foi desenvolvido como um Trabalho Didático para as disciplinas de Introdução à Nanociência e Nanotecnologia e Modelagem Matemática na UFABC. O objetivo é demonstrar como partículas em nanoescala não seguem trajetórias clássicas, mas sim probabilísticas, utilizando a computação quântica como ponte. 


### Conceitos a serem desenvolvidos:

Caminhadas quânticas: uma ponte entre a nanociência, modelagem matemática e música.

#### Público-alvo: 

Estudantes do ensino médio com interesse em ciência, computação, matemática e música.

#### Fio condutor: 

Explorar como partículas em nanoescala não seguem trajetórias clássicas, mas sim probabilísticas, e como isso pode ser modelado matematicamente por meio de random walks quânticos. O resultado é visualizado em padrões caóticos, aproximando o estudante de fenômenos reais da nanociência através de um recurso computacional acessível.

### Proposta de desenvolvimento de um Trabalho Didático:

#### 1. Contextualização

Na nanociência, o estudo de partículas em dimensões extremamente pequenas exige modelos que considerem superposição, interferência e descoerência quântica. Essas propriedades são diferentes do mundo clássico e podem ser introduzidas aos alunos através de analogias com passeios aleatórios quânticos (quantum random walks).

Na modelagem matemática, os random walks quânticos podem ser descritos como versões discretas de equações diferenciais estocásticas, permitindo visualizar distribuições de probabilidade não triviais. A interação desses estados produz padrões que se aproximam de estruturas caóticas.

Por fim, estes padrões serão convertidos em uma música aleatória e caótica.



#### 2. Metodologia:

Introduzir conceitos básicos de nanociência (movimento de partículas, transporte em nanoestruturas, exemplo do grafeno) e diferenciar o modelo clássico do quântico.

Modelagem computacional: Mostrar o código em Python/Qiskit que simula o random walk quântico, explicando passo a passo.
Código de programação Python

Usando linguagem de programação Python, vamos simular, comparar, modelar e converter os parâmetros em diversas estruturas.

### Parâmetros do Quantum Random Walks

```
import numpy as np
import matplotlib.pyplot as plt
from qiskit import QuantumCircuit, transpile
from qiskit_aer import AerSimulator
from PIL import Image


n_steps = 20          # número de passos do walk
shots_per_step = 200  # número de execuções por passo
qubits_per_axis = 2   # 2 → 4 posições por eixo (grid 4x4)
grid_size = 2**qubits_per_axis
```

### Simulando um Quantum Random Walks

```

# Matriz acumulada de probabilidades

prob_matrix = np.zeros((grid_size, grid_size))

# Função para simular um passo quântico
def quantum_random_walk_step(prob_matrix, shots):
   qc = QuantumCircuit(2 * qubits_per_axis)
   qc.h(range(2 * qubits_per_axis))   # cria superposição em todos os qubits
   qc.measure_all()

   simulator = AerSimulator()
   compiled_circuit = transpile(qc, simulator)
   result = simulator.run(compiled_circuit, shots=shots).result()
   counts = result.get_counts()

   # Atualiza a matriz de probabilidades

   for bitstring, count in counts.items():
       # Divide os qubits no meio: metade → eixo X, metade → eixo Y
       x_bits = bitstring[:qubits_per_axis]
       y_bits = bitstring[qubits_per_axis:]

       # Converte binário → inteiro
       x = int(x_bits, 2)
       y = int(y_bits, 2)

       prob_matrix[x, y] += count
   return prob_matrix

```
### Convertendo dados em imagem
```
for _ in range(n_steps):
   prob_matrix = quantum_random_walk_step(prob_matrix, shots_per_step)


# Normalização para 0-255
prob_matrix = prob_matrix / np.max(prob_matrix) * 255
prob_matrix = prob_matrix.astype(np.uint8)


# ----------------------------
# Salvar imagem 
# ----------------------------


img = Image.fromarray(prob_matrix)
img = img.resize((1080, 1080), Image.BICUBIC)  # interpolação fractal-like
img.save("quantum_random_walks.png")
```
Visualizando a imagem criada
```
plt.imshow(prob_matrix, cmap="inferno")  # pode trocar cmap para 'plasma', 'magma', etc.
plt.title("Quantum Random Walk")
plt.axis("off")
plt.show()
```

Visualização: Gerar a matriz de probabilidades e convertê-la em imagem fractalizada. Discussão: Relacionar os padrões visuais com fenômenos como difusão quântica em nanoescala, coerência e caos.


