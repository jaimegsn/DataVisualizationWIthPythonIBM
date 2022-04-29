# Curso Data Visualization da IBM:

<h2>
Boas Práticas Iniciais :
</h2>
- Menos é Mais atrativo, efetivo e impactativo. (Em outras palavras, não poluir muito seu gráfico com muitas informações além de não inventar muito no design do gráfico e ser algo mais clean, resumindo ser objetivo)

- Gráficos de Pizzas são relevantes apenas nas circustãncias mais raras então é melhor evitar
  <br>

<p>
Sources:<br>
https://www.coursera.org/learn/python-for-data-visualization<br>
http://www.estruturas.ufpr.br/disciplinas/pos-graduacao/introducao-a-computacao-cientifica-com-python/introducao-python/3-2-figuras-subplotagens-eixos-e-marcadores/<br>
https://github.com/matplotlib/AnatomyOfMatplotlib
</p><br><br>

# Um Pouco do que aprendi sobre a Camada Artista na Internet

<p>Visto que o curso da IBM é muito focado na camada de Script, decidi pesquisar um pouco por fora sobre a camadad de Artista, pois nessa camada pode-se ter uma melhor customização do Gráfico</p><br>
<h2>
Figuras:
</h2>
<p>Figuras são as janelas onde acontecerá o desenho do nosso gráfico</p>

```python
fig = plt.figure(
    # Alguns Parâmetros na hora da criação da figura:
    num=1, # Número da Figura
    figsize=(10,5), # tamanho da figura em polegadas (largura, altura)
    dpi=300, # resolução em pontos por polegada
    facecolor=(1, 0, 0, .1), # cor do fundo
    edgecolor=(1, 0, 0, .1), # cor da borda no entorno do fundo
    frameon= True # Valor Padrão --- desenhar o quadro da figura ou não
    )
```

<br>

<h2>
AXES/SUBPLOT:
</h2>
<p>Toda a plotagem é feita em relação ao AXES, AXES é um objeto composto por title,axis,labels... e um objeto
AXES deve pertencer some a uma figura enquanto uma figura pode ter diversos AXES</p>

```python
fig = plt.figure() # Sem nenhum parâmetro, todos estão setados Default
ax = fig.add_subplot(111) # Outro jeito de criar grafico Poderia ser ->  ax = df.plot(kind='line')
ax.set(
    xlim=[0.5,4.5], # Quais serão os rotulos de marcações no eixo X
    ylim=[-2,8],   # Quais serão rotulos de marcações no eixo Y
    title=['An Example Axes'], # Configura o titulo do gráfico
    ylabel='Y-Axis',  # Configura o rotulo do eixo Y
    xlabel='X-Axis') # Configura o rotulo do eixo X

# OU

ax.set_xlim([0.5, 4.5])
ax.set_ylim([-2, 8])
ax.set_title('A Different Example Axes Title')
ax.set_ylabel('Y-Axis (changed)')
ax.set_xlabel('X-Axis (changed)')
plt.show()


plt.show()
```

<br>

<h2>
Basic Plot:
</h2>
<p>Métodos Básicos de Plotagem: Plot e Scatter, o Plot desenha pontos com linhas conectando eles enquanto o Scatter desenha pontos desconectados</p>

```python
fig = plt.figure()
ax= fig.add_subplot(111)

ax.plot([1,2,3,4], # Onde a marcação irá ficar no Eixo X
[10, 20, 25, 30],  # Onde a marcação irá ficar no Eixo Y
color='lightblue', # Cor da Linha
linewidht=3)  # Largura da Linha

ax.scatter([1.5, 3.8, 1.2, 2.5], # Onde a marcação irá ficar no Eixo X
[11, 25, 9, 26],  # Onde a marcação irá ficar no Eixo Y
c=[1, 2, 3, 5],  # Cores representada por números, para melhor leitura escolha numeros diferentes
marker='^')  # tipo der marcação = o(ciruclo) ^(Triângulo)
ax.set_xlim(0.5, 4.5)

#ax.bar
#ax.hist
#ax.line
#....
```

<br>

<h2>
Multiples Plots:
</h2>
<p>Muitas vezes queremos plotar vários gráficos dentro da mesma figura, como um exemplo comprar 2 gráficos e outros...
parapoder visualizar vários gráficos juntos adicionamos subplots</p>

```python
fig, axes = plt.subplots(nrows=2, ncols=2) # Criando em Grade 4 Gráficos (2 colunas de grafico com 2 linhas)
axes[0,0].set(title='Upper Left')
axes[0,1].set(title='Upper Right')
axes[1,0].set(title='Lower Left')
axes[1,1].set(title='Lower Right')

# Para iterar todos os Gráficos em Axes use .flat
for ax in axes.flat:
    # Removendo todos os Xticks e Yticks
    ax.set(xticks=[], yticks=[])

plt.show()
```

Ou

```python
fig = plt.figure() # Cria uma figura

ax0 = fig.add_subplot(1, 2, 1) # add subplot 1 (1 row, 2 columns, first plot)   OBS  (1,2,1)==(121)
ax1 = fig.add_subplot(1, 2, 2) # add subplot 2 (1 row, 2 columns, second plot). OBS  (1,2,1)==(121)

# Subplot 1: Box plot
df_CI.plot(kind='box', color='blue', vert=False, figsize=(20, 6), ax=ax0) # add to subplot 1
ax0.set_title('Box Plots of Immigrants from China and India (1980 - 2013)')
ax0.set_xlabel('Number of Immigrants')
ax0.set_ylabel('Countries')

# Subplot 2: Line plot
df_CI.plot(kind='line', figsize=(20, 6), ax=ax1) # add to subplot 2
ax1.set_title ('Line Plots of Immigrants from China and India (1980 - 2013)')
ax1.set_ylabel('Number of Immigrants')
ax1.set_xlabel('Years')

plt.show()
```


<br>

<h4>OBS: podemos adicionar apenas um gráfico usando o subplots</h4>

```python
# Em um código acima vimos isso:
fig = plt.figure()
ax = fig.add_subplot(111)

#Você pode reescrever assim:
fig, ax = plt.subplots()
# Visto que o subplots sem nenhum argumento cria apenas um gráfico
```

<br><br>
