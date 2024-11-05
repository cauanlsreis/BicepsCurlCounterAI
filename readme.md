# Biceps Rep Counter

Este projeto é uma aplicação em Python para contar repetições de exercícios (rosca bíceps) usando visão computacional e aprendizado de máquina. A interface gráfica (GUI) é construída com Tkinter e captura imagens ao vivo da câmera para identificar o estágio do exercício (braço estendido ou contraído), utilizando o classificador `LinearSVC` para fazer as previsões. 

## Estrutura do Projeto

O projeto é composto por três módulos principais:

1. **`camera.py`**:
   - Este módulo gerencia a captura de vídeo ao vivo usando OpenCV.
   - A classe `Camera` abre a câmera padrão e captura quadros, que podem ser processados em tempo real.

2. **`model.py`**:
   - Define a classe `Model`, que treina um modelo de aprendizado de máquina `LinearSVC` para classificar imagens em duas categorias: braço estendido (classe `1`) e contraído (classe `2`).
   - O método `train_model` lê imagens para as duas classes, transforma cada imagem em um vetor de pixels, e treina o modelo.
   - O método `predict` processa uma imagem de entrada ao vivo e retorna a classe prevista (`1` para estendido, `2` para contraído).

3. **`app.py`**:
   - Este módulo implementa a interface gráfica com Tkinter e organiza a lógica principal do contador de repetições.
   - A classe `App` controla a GUI, exibe a imagem da câmera, e interage com o modelo de aprendizado de máquina.
   - Os principais recursos incluem:
     - **Contagem de Repetições**: Detecta e conta repetições de exercício com base no estado estendido e contraído do braço.
     - **Treinamento do Modelo**: Permite salvar imagens para cada classe (`Estendido` e `Contraído`) e treinar o modelo `LinearSVC`.
     - **Previsão em Tempo Real**: Usa o modelo treinado para fazer previsões sobre o estado do exercício com base nas imagens ao vivo da câmera.

## Como Usar

1. **Executando o Projeto**:
   - Execute `app.py` para iniciar a interface gráfica.
   - Na GUI, você pode:
     - **Capturar imagens** para as classes estendido e contraído, usando os botões `Extended` e `Contracted`.
     - **Treinar o modelo** após capturar um conjunto suficiente de imagens para cada classe, clicando em `Train Model`.
     - **Ativar a contagem de repetições** ao alternar o botão `Toggle Counting`.

2. **Estrutura de Arquivos de Treinamento**:
   - Imagens salvas para cada classe são armazenadas nas pastas `1` (Estendido) e `2` (Contraído).
   - As imagens são convertidas para escala de cinza e redimensionadas para um tamanho fixo de 150x150 pixels para treinar o modelo.

## Observações

- O modelo utiliza `LinearSVC` para classificar cada imagem como braço estendido ou contraído.
- A contagem é incrementada cada vez que o sistema detecta uma transição completa do braço estendido para o contraído.
