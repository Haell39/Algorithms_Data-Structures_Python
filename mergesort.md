### Código em Python (Mergesort)
Vamos ver isso funcionando com um código simples:
```python
def mergesort(lista):
    # Se a lista tem 1 ou 0 itens, já está "ordenada"
    if len(lista) <= 1:
        return lista
    
    # Divide no meio
    meio = len(lista) // 2
    esquerda = lista[:meio]  # Primeira metade
    direita = lista[meio:]   # Segunda metade
    
    # Divide mais (recursão)
    esquerda = mergesort(esquerda)
    direita = mergesort(direita)
    
    # Junta as partes ordenadas
    return juntar(esquerda, direita)

def juntar(esquerda, direita):
    resultado = []
    i = 0  # Índice da esquerda
    j = 0  # Índice da direita
    
    # Compara e junta em ordem
    while i < len(esquerda) and j < len(direita):
        if esquerda[i] <= direita[j]:
            resultado.append(esquerda[i])
            i += 1
        else:
            resultado.append(direita[j])
            j += 1
    
    # Adiciona o que sobrou
    resultado.extend(esquerda[i:])
    resultado.extend(direita[j:])
    return resultado

# Teste
lista = [5, 2, 8, 1]
print("Lista original:", lista)
lista_ordenada = mergesort(lista)
print("Lista ordenada:", lista_ordenada)
```

Saída:
```
Lista original: [5, 2, 8, 1]
Lista ordenada: [1, 2, 5, 8]
```

---

### Visualizando o Tempo
- Se a lista tem 4 itens:
  - Divide 2 vezes (log 4 ≈ 2).
  - Junta comparando 4 itens em cada etapa.
  - Total: algo como 4 × 2 = 8 "operações".

- Se a lista tem 8 itens:
  - Divide 3 vezes (log 8 = 3).
  - Junta comparando 8 itens em cada etapa.
  - Total: 8 × 3 = 24 "operações".

Compare com O(n²):
- 4 itens → 4 × 4 = 16 operações.
- 8 itens → 8 × 8 = 64 operações.

O(n log n) é bem mais eficiente que O(n²) quando a lista cresce!

---

### Analogia do Dia a Dia
Imagina que você tem uma pilha de 8 cartas pra ordenar:
- **O(n²)**: Compara cada carta com todas as outras (8 × 8 = 64 comparações).
- **O(n log n)**: Divide em grupos menores (4, 2, 1), ordena cada pedacinho, e junta (8 × 3 = 24 comparações).

É como organizar uma festa: dividir as tarefas em pedaços (log n) e depois ajustar tudo (n).