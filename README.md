# Redes Generativas Adversariais (GANs) para Geração de Dígitos MNIST

Este repositório contém uma implementação de uma Rede Generativa Adversarial (GAN) para gerar dígitos manuscritos semelhantes aos encontrados no dataset MNIST. As GANs são um tipo de modelo generativo que aprende a produzir novos dados com as mesmas estatísticas de distribuição que o conjunto de dados de treinamento.

## Visão Geral do Projeto

O projeto utiliza o PyTorch para construir e treinar uma GAN simples composta por duas redes neurais:

1.  **Gerador (Generator)**: Responsável por criar novas imagens de dígitos a partir de ruído aleatório.
2.  **Discriminador (Discriminator)**: Responsável por distinguir entre imagens de dígitos reais (do dataset MNIST) e imagens falsas (geradas pelo Gerador).

Os dois modelos são treinados simultaneamente em um "jogo" de soma zero, onde o gerador tenta "enganar" o discriminador e o discriminador tenta identificar as falsificações. Com o tempo, o gerador aprende a produzir imagens cada vez mais realistas, e o discriminador se torna melhor em detectá-las.

### Funcionamento das GANs

As GANs foram propostas por Ian Goodfellow em 2014 e operam em um framework de aprendizado de máquina onde dois modelos neurais competem:
* **Gerador**: Gera dados sintéticos (neste caso, imagens de dígitos) a partir de uma distribuição de entrada (ruído aleatório). O objetivo do Gerador é produzir amostras indistinguíveis dos dados reais para "enganar" o Discriminador.
* **Discriminador**: Classifica se uma amostra é real ou falsa, ou seja, se a imagem veio do conjunto de dados original ou se foi produzida pelo Gerador. O objetivo do Discriminador é identificar corretamente as amostras falsas.

Em um cenário ideal, o Gerador produz dados de alta qualidade e o Discriminador não consegue distinguir entre dados reais e sintéticos, resultando em uma taxa de acerto de 50%.

### Aplicações Comuns de GANs

* Geração de imagens realistas
* Super-resolução de imagens
* Tradução de estilos
* Preenchimento de dados faltantes

### Desafios no Treinamento de GANs

* **Modo Colapso (Mode Collapse)**: O Gerador pode produzir uma variedade limitada de saídas, focando em algumas amostras específicas que enganam o Discriminador.
* **Dificuldade de Treino**: Requer um balanceamento cuidadoso entre o treinamento do Gerador e do Discriminador.

## Estrutura do Repositório

* `gan.ipynb`: O notebook Jupyter que contém todo o código para implementar, treinar e avaliar a GAN.
* `requirements.txt`: Lista todas as dependências Python necessárias para executar o projeto.
* `gan_images/`: (Criado durante o treinamento) Diretório para salvar exemplos de imagens geradas em diferentes épocas.
* `models/`: (Criado durante o treinamento) Diretório para salvar os modelos treinados do Gerador e Discriminador.

## Como Executar o Projeto

Siga os passos abaixo para configurar e executar o projeto.

### 1. Clonar o Repositório

```bash

git clone https://github.com/anasofia0/gan.git
cd seu-repositorio
```

### 2. Configurar o Ambiente Python

Recomenda-se usar um ambiente virtual para gerenciar as dependências.

```bash
python -m venv venv
source venv/bin/activate  # No Windows, use `venv\Scripts\activate`
pip install -r requirements.txt
```

### 3. Executar o Notebook Jupyter

Inicie o Jupyter Notebook ou JupyterLab e abra o arquivo ```gan.ipynb```.

```bash
jupyter notebook gan.ipynb
```

## Dependências

As principais dependências do projeto estão listadas no arquivo ```requirements.txt```:

    torch==2.7.1+cu128 
    torchvision==0.22.1+cu128
    matplotlib==3.10.3
    numpy==2.1.2
    ipykernel==6.29.5

E outras dependências para ambiente Jupyter/CUDA.

## Contribuições

Contribuições são bem-vindas! Sinta-se à vontade para abrir issues ou pull requests.

## Licença

Este projeto está licenciado sob a licença MIT. Consulte o arquivo LICENSE para mais detalhes.

Nota: O tempo de treinamento pode variar dependendo da sua configuração de hardware (CPU vs. GPU). O notebook está configurado para usar GPU se disponível (```torch.cuda.is_available()```).