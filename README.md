# projeto-sistema-de-faturamento-mensal-
Esse sistema calcula o faturamento mensal da empresa fixa prime
  
  def lin():
   print('-'*30)


clientes_fixa = ('boltinox,indufix,liderinox, ASTM')
lin()
print('CLIENTES CADASTRADOS')
lin()
print(clientes_fixa)
lin()

parafusos = [
    {"id": 1, "tipo": "Sextavado", "medida": "M6x20", "preco": 0.35},
    {"id": 2, "tipo": "Allen", "medida": "M5x16", "preco": 0.45},
    {"id": 3, "tipo": "Philips", "medida": "4,2x25mm", "preco": 0.30},
    {"id": 4, "tipo": "Autoatarraxante", "medida": "4,8x25mm", "preco": 0.25},
]
#  Sistema de Análise de Faturamento 

import pandas as pd

def titulo(txt):
    print("-" * 50)
    print(txt.center(50))
    print("-" * 50)

# Dados fictícios de faturamento 
# Cada linha representa uma compra (empresa, mês, quantidade, valor total)
dados = [
    ["Boltinox", "Janeiro", 120, 4200.00],
    ["Boltinox", "Fevereiro", 90, 3150.00],
    ["Indufix", "Janeiro", 150, 5000.00],
    ["Indufix", "Fevereiro", 200, 7200.00],
    ["Liderinox", "Janeiro", 80, 2880.00],
    ["Liderinox", "Fevereiro", 130, 4680.00],
    ["ASTM", "Janeiro", 60, 2100.00],
    ["ASTM", "Fevereiro", 75, 2625.00],
]

# Criação do DataFrame
colunas = ["Empresa", "Mês", "Quantidade", "Valor (R$)"]
df = pd.DataFrame(dados, columns=colunas)

# === Exibir tabela completa ===
titulo("Tabela de Compras Mensais")
print(df)

# === Faturamento total por mês ===
titulo("Faturamento por Mês")
faturamento_mes = df.groupby("Mês")["Valor (R$)"].sum().reset_index()
print(faturamento_mes)

# === Faturamento total por empresa ===
titulo("Faturamento por Empresa")
faturamento_empresa = df.groupby("Empresa")["Valor (R$)"].sum().reset_index()
print(faturamento_empresa)

# === Faturamento geral ===
titulo("Faturamento Total")
total = df["Valor (R$)"].sum()
print(f"💰 Faturamento total no período: R$ {total:,.2f}")
