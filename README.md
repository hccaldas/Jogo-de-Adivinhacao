# Jogo de Adivinhação em Python

Este repositório contém um jogo de adivinhação simples escrito em Python. O objetivo do jogo é adivinhar um número secreto gerado aleatoriamente entre 1 e 100. O jogador pode escolher o nível de dificuldade, que determina o número de tentativas disponíveis.

## Funcionalidades

- Geração de um número secreto aleatório entre 1 e 100.
- Escolha do nível de dificuldade (Fácil, Médio, Difícil).
- Feedback ao jogador sobre se o chute foi maior ou menor que o número secreto.
- Sistema de pontuação baseado na proximidade do chute ao número secreto.

## Pré-requisitos

- Python 3.x

## Como jogar

1. Clone este repositório ou copie o código para o seu ambiente local.
2. Certifique-se de ter o Python 3.x instalado no seu sistema.
3. Execute o script.
4. Escolha o nível de dificuldade:
   - (1) Fácil: 20 tentativas
   - (2) Médio: 10 tentativas
   - (3) Difícil: 5 tentativas
5. Digite um número entre 1 e 100 quando solicitado.
6. O jogo fornecerá feedback se o chute foi maior ou menor que o número secreto.
7. O jogo termina quando o jogador adivinha o número secreto ou esgota o número de tentativas.

## Exemplo de Uso

```python
import random       # Importa a biblioteca random

numero_secreto = random.randint(1, 100)       # Gera um número aleatório entre 1 e 100
total_de_tentativas = 0       # Inicializa a variável total_de_tentativas
pontos = 1000       # Inicializa a variável pontos

print("Bem vindo ao jogo de adivinhação!")       # Imprime uma mensagem de boas vindas

print("Qual o nível de dificuldade?")       # Imprime uma mensagem
print("(1) Fácil (2) Médio (3) Difícil")       # Imprime uma mensagem
nivel = int(input("Defina o nível: "))       # Lê o nível de dificuldade

if nivel == 1:       # Se o nível for 1
    total_de_tentativas = 20       # total_de_tentativas recebe 20
elif nivel == 2:       # Se o nível for 2
    total_de_tentativas = 10       # total_de_tentativas recebe 10
else:       # Se não
    total_de_tentativas = 5       # total_de_tentativas recebe 5

for rodada in range(1, total_de_tentativas + 1):       # Para cada rodada de 1 até total_de_tentativas + 1

    print(f"Tentativa {rodada} de {total_de_tentativas}")       # Imprime a tentativa atual

    chute_str = input("Digite um número entre 1 e 100: ")       # Lê um número do usuário
    print(f"Você digitou: {chute_str}")       # Imprime o número digitado
    chute = int(chute_str)       # Converte o número digitado para inteiro

    if chute < 1 or chute > 100:       # Se o chute for menor que 1 ou maior que 100
        print("Você deve digitar um número entre 1 e 100!")       # Imprime uma mensagem
        continue       # Pula para a próxima iteração

    acertou = chute == numero_secreto       # Verifica se o chute é igual ao número secreto
    maior = chute > numero_secreto       # Verifica se o chute é maior que o número secreto
    menor = chute < numero_secreto       # Verifica se o chute é menor que o número secreto

    if acertou:       # Se acertou for verdadeiro
        print(f"Você acertou e fez {pontos} pontos!")       # Imprime uma mensagem
        break
    else:       # Se não
        if maior:
            print("Você errou! O seu chute foi maior que o número secreto.")
        elif menor:
            print("Você errou! O seu chute foi menor que o número secreto.")
        pontos_perdidos = abs(numero_secreto - chute)
        pontos = pontos - pontos_perdidos

print(f"O número secreto era {numero_secreto}. Você fez {pontos} pontos!")       # Imprime o número secreto e os pontos
print("Fim do jogo")       # Imprime uma mensagem de fim de jogo
