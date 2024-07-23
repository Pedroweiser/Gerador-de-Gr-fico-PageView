# Gerador-de-Gr-fico-PageView
# Código que vai gerar um gráfico que representa o desempenho de um site em termos de acesso, que são os page views, com base nos dias do mês.

import matplotlib.pyplot as plt
import numpy as np

# Dados de page views
page_views = [12069, 22340, 31798, 39179, 44459, 44909, 45243, 180, 175464, 135174, 246110, 390857, 534345, 705025, 872349, 1023554, 1160990, 1240914, 1248906]
days = list(range(1, 20))

# Criar o gráfico de page views diários
plt.figure(figsize=(10, 6))
plt.plot(days, page_views, marker='o', linestyle='-', color='b', label='Page Views Diários')

# Adicionar título e rótulos
plt.title('Page Views Diários de um Cliente ao Longo do Mês')
plt.xlabel('Dias')
plt.ylabel('Page Views')
plt.grid(True)
plt.legend()

# Mostrar o gráfico
plt.show()

# Calcular a média móvel (janela de 7 dias, por exemplo)
window_size = 7
rolling_mean = np.convolve(page_views, np.ones(window_size)/window_size, mode='valid')

# Plotar a média móvel
plt.figure(figsize=(10, 6))
plt.plot(days, page_views, marker='o', linestyle='-', color='b', label='Page Views Diários')
plt.plot(days[window_size-1:], rolling_mean, color='r', label='Média Móvel (7 dias)')

# Adicionar título e rótulos
plt.title('Page Views Diários de um Cliente ao Longo do Mês')
plt.xlabel('Dias')
plt.ylabel('Page Views')
plt.legend()
plt.grid(True)

# Mostrar o gráfico
plt.show()

