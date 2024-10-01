# Projeto VR de Laparoscopia - VR Care+

## VR Care+

A VrCare+ é uma plataforma inovadora de treinamento em cirurgia laparoscópica
que utiliza tecnologia de realidade virtual (VR) para proporcionar uma experiência de aprendizado imersiva, interativa e eficaz. Nosso objetivo é transformar o treinamento cirúrgico tradicional, tornando-o mais acessível, eficiente e envolvente para os
cirurgiões novatos.

O principal foco da VrCare+ é aprimorar a formação de cirurgiões através da
simulação realista de procedimentos laparoscópicos em um ambiente virtual. Ao
romper as barreiras físicas e logísticas associadas aos treinamentos presenciais, nossa plataforma pretende oferecer uma solução prática e flexível que permite aos futuros cirurgiões desenvolverem habilidades motoras críticas de forma contínua e acessível.

## Integrantes

- Kaiky Alvaro de Miranda RM:98118
- Lucas Rodrigues da Silva RM:98344
- Pedro Henrique Bicas Couto RM:99534
- Júlia Marques Mendes das Neves RM:98680


## Frustum Culling

Este projeto implementa um algoritmo de Frustum Culling em Python, que é uma técnica usada em gráficos 3D para determinar quais objetos estão visíveis dentro de um frustum (pirâmide de visualização). A implementação utiliza memoização para otimizar as verificações de interseção entre os objetos e o frustum.

## Estrutura do Código

### Classes

- **Plano**: Representa um plano no espaço 3D.
- **Frustum**: Representa um frustum que contém 6 planos.
- **Objeto3D**: Representa um objeto 3D com uma esfera delimitadora.

### Funções

- **verificar_interseccao(objeto, frustum)**: Verifica se um objeto está dentro ou intersectando o frustum.
- **memo_verificar_interseccao(...)**: Função otimizada usando memoização para verificar interseções.
- **reconstruir_frustum(frustum_planes_key)**: Reconstrói os planos do frustum a partir de uma chave.
- **frustum_culling(objetos, frustum_planes_key)**: Função principal para determinar quais objetos são visíveis.

## Instalação

Certifique-se de ter o Python instalado em seu ambiente. Você pode instalar as dependências necessárias usando o seguinte comando:

```
pip install numpy functool
```

## Exemplo de uso

```
# Criar um frustum com planos fixos
frustum_planes_key = "default"  # Exemplo de chave para o frustum
planos = [
    Plano((-1, 0, 0), 5),   # Plano direito (x = 5)
    Plano((1, 0, 0), 5),    # Plano esquerdo (x = -5)
    Plano((0, -1, 0), 5),   # Plano superior (y = 5)
    Plano((0, 1, 0), 5),    # Plano inferior (y = -5)
    Plano((0, 0, -1), 5),   # Plano próximo (z = 5)
    Plano((0, 0, 1), 5)     # Plano distante (z = -5)
]
frustum = Frustum(planos)

# Criar uma lista de objetos 3D
objetos = [
    Objeto3D(1, [2, 2, 2], 1),
    Objeto3D(2, [4.5, 0, 0], 0.6),
    Objeto3D(3, [5.5, 0, 0], 1),
    Objeto3D(4, [-4.5, -4.5, -4.5], 0.7),
    Objeto3D(5, [-6, 6, 6], 1.5),
]

# Aplicar frustum culling
objetos_visiveis = frustum_culling(objetos, frustum_planes_key)

# Exibir objetos visíveis
print("Objetos visíveis:")
for obj in objetos_visiveis:
    print(f"ID: {obj.id}, Posição: {obj.posicao}, Raio: {obj.raio}")

```


## Diagrama de Fluxo da Solução


```plaintext
+-----------------------------------------------------------+
|                Início do Projeto VR de Laparoscopia       |
+-----------------------------------------------------------+
                             |
                             v
+-----------------------------------------------------------+
|          Identificação do Desafio Educacional            |
|  - Necessidade de flexibilidade e acessibilidade nos      |
|    treinamentos médicos.                                   |
|  - Integração de cursos virtuais na formação.             |
+-----------------------------------------------------------+
                             |
                             v
+-----------------------------------------------------------+
|                  Definição de Objetivos                   |
|  - Proporcionar experiência educacional dinâmica e        |
|    interativa.                                            |
|  - Manter a qualidade do ensino e treinamento.            |
+-----------------------------------------------------------+
                             |
                             v
+-----------------------------------------------------------+
|                Desenvolvimento do Jogo VR                 |
|  - Criação de um ambiente imersivo para simulação de      |
|    laparoscopia.                                          |
|  - Implementação de algoritmos para otimização            |
|    (ex: Frustum Culling).      |
+-----------------------------------------------------------+
                             |
                             v
+-----------------------------------------------------------+
|         Promoção de Materiais de Estudo sobre             |
|         Coordenação Motora e Laparoscopia                 |
|  - Desenvolvimento de conteúdos educativos e guias        |
|    para ajudar os estudantes a aprimorar suas habilidades.|
+-----------------------------------------------------------+
                             |
                             v
+-----------------------------------------------------------+
|                   Avaliação de Resultados                 |
|  - Coleta de feedback dos estudantes.                      |
|  - Análise do impacto na formação e desempenho.           |
+-----------------------------------------------------------+
                             |
                             v
+-----------------------------------------------------------+
|                  Melhoria Contínua                        |
|  - Atualizações com base em feedback.                     |
|  - Implementação de novas tecnologias e metodologias.     |
+-----------------------------------------------------------+
                             |
                             v
+-----------------------------------------------------------+
|                         Fim do Projeto                     |
+-----------------------------------------------------------+

```

## Conclusão

O projeto **Frustum Culling** desenvolvido implementa de maneira eficaz o algoritmo de culling de frustum em Python, uma técnica fundamental em gráficos 3D para otimizar a renderização ao determinar quais objetos estão visíveis dentro da pirâmide de visualização (frustum). Através da utilização de memoização, conseguimos aprimorar significativamente a eficiência das verificações de interseção entre os objetos e o frustum, reduzindo o tempo de processamento em cenários com múltiplas chamadas repetidas.

## Principais Contribuições

- **Estrutura Modular**: A organização do código em classes bem definidas (`Plano`, `Frustum`, `Objeto3D`) e funções específicas facilita a manutenção e a escalabilidade do projeto.
- **Otimização com Memoização**: A aplicação do decorador `@lru_cache` para a função `memo_verificar_interseccao` demonstra um ganho de desempenho ao evitar cálculos redundantes, especialmente em cenas complexas com inúmeros objetos.
- **Flexibilidade na Reconstrução do Frustum**: A função `reconstruir_frustum` permite a reconstrução dinâmica dos planos do frustum a partir de uma chave, possibilitando a adaptação do algoritmo para diferentes configurações de visualização.

## Resultados Obtidos

Os exemplos de uso apresentados evidenciam a eficácia do algoritmo em diferentes cenários, identificando corretamente os objetos visíveis conforme suas posições e raios em relação ao frustum definido. A capacidade de detectar objetos parcialmente dentro ou tocando os planos do frustum demonstra a robustez da implementação.

### Output dos Exemplos:
- **Output 1**: Identificação de objetos completamente dentro ou intersectando o frustum.
- **Output 2 e 3**: Demonstração da precisão em cenários com objetos próximos às bordas do frustum, incluindo objetos parcialmente visíveis.

## Referências

- [Frustum Culling - PucRio](https://www.maxwell.vrac.puc-rio.br/31453/31453_4.PDF)
- [Functools — Funções de alta ordem e operações sobre funções](https://docs.python.org/3/library/functools.html)
