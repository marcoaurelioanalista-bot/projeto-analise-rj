import matplotlib.pyplot as plt
import pandas as pd

# Dados consolidados do 1º Trimestre de 2025 (RJ)
# Fonte: Dados baseados no ISP-RJ
dados = {
    'Mês': ['Janeiro', 'Fevereiro', 'Março'],
    'Roubos': [2500, 2591, 1483],
    'Recuperados': [1700, 1800, 1541]
}

df = pd.DataFrame(dados)

# Configuração do gráfico
plt.figure(figsize=(10, 6))
bar_width = 0.35
index = range(len(df['Mês']))

# Criando as barras
bar1 = plt.bar(index, df['Roubos'], bar_width, label='Roubos de Veículos', color='#e74c3c')
bar2 = plt.bar([i + bar_width for i in index], df['Recuperados'], bar_width, label='Veículos Recuperados', color='#2ecc71')

# Customização
plt.xlabel('Meses de 2025')
plt.ylabel('Quantidade de Ocorrências')
plt.title('Criminalidade vs. Recuperação de Veículos no RJ - Q1 2025')
plt.xticks([i + bar_width / 2 for i in index], df['Mês'])
plt.legend()

# Adicionando os valores em cima das barras
for i, v in enumerate(df['Roubos']):
    plt.text(i - 0.05, v + 50, str(v), color='black', fontweight='bold')
for i, v in enumerate(df['Recuperados']):
    plt.text(i + bar_width - 0.05, v + 50, str(v), color='black', fontweight='bold')

plt.tight_layout()
plt.savefig('estatisticas_rj_2025.png')
plt.show()

