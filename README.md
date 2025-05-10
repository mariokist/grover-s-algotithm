# Simulação do Algoritmo de Grover

Este pequeno projeto simula o **Algoritmo de Grover**, utilizado em computação quântica para buscar um elemento marcado em um espaço não ordenado com complexidade `O(√N)`, onde `N = 2^n` e `n` é o número de qubits. A simulação é feita em Python usando álgebra linear com NumPy e visualização com Matplotlib.

---

## ✨ Fundamento Físico

O Algoritmo de Grover realiza uma **amplificação de amplitudes** para o estado desejado (marcado), utilizando:

1. **Operador Hadamard - Superposição inicial** com portas de Hadamard (`H⊗n`):  
   Transforma o estado $|0⟩$ em uma superposição uniforme:

$$
\lvert \psi \rangle = \frac{1}{\sqrt{N}} \sum_{x=0}^{N-1} \lvert x \rangle
$$



2. **Operador Oracle (O<sub>f</sub>)**:  
   Inverte a fase do estado marcado `|w⟩`:

$$
O_f |x⟩ = 
\begin{cases}
-|x⟩ & \text{se } x = w \\\\
|x⟩ & \text{caso contrário}
\end{cases}
$$


3. **Operador de Difusão (D)**:  
   Reflete o vetor de estado em relação à média das amplitudes, amplificando a amplitude de `|w⟩`.

---

## ⚙️ Estrutura Matemática do Código

- `N = 2^n`: Tamanho do espaço de busca.
- `|s⟩ = H⊗n |0⟩`: Estado inicial em superposição uniforme.
- `|w⟩`: Estado marcado aleatório.
- `|w⊥⟩`: Componente ortogonal a `|w⟩` no subespaço bidimensional da evolução.
- Operador de Grover:  
  $$
  G = D \cdot O_f
  $$

A cada iteração, o estado `|ψ⟩` é rotacionado no plano formado por `|w⟩` e `|w⊥⟩`, aproximando-se cada vez mais de `|w⟩`.

---

## 📈 Visualização

O gráfico gerado mostra:

- **Círculo unitário**: Representa todas as superposições de norma 1.
- **Vetores de estado**: (Representam como fica os vetores e suas probabilidades após a execução dos Operadores) 
  - Verde: Estado inicial, composto geralmente por um vetor com mesmo probabilidade em todos os estados 
  - Laranja: Após o oráculo (inversão de fase de `|w⟩`) 
  - Azul: Após o operador de difusão (reflexão sobre a média)
- **Trajetória**: Linha vermelha ligando os vetores ao longo das iterações.
- **Último estado**: Destacado com um ponto vermelho.

O gráfico ilustra geometricamente a convergência do estado quântico para `|w⟩` após `~π/4·√N` iterações.

---

## 🧠 Considerações

- O algoritmo é simulado de forma clássica, portanto a complexidade de memória cresce exponencialmente com `n`.
- Para `n > 20`, recomenda-se cautela com o uso de memória.
- O código pode ser estendido para incluir simulação de medições, ruído ou animação.

---

## 📌 Requisitos

- Python 3.x
- NumPy
- Matplotlib

Execute com:

```bash
jupyter Algoritimo de Grover.ipynb


