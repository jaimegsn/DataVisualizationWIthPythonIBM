# Sobre o Matplotlib e Sua Arquitetura:

Matplotlib é uma das mais utilizadas, se não a biblioteca de visualização de dados mais popular em Python e foi criado por John Hunter.<br>

A arquitetura de Matplotlib é composta de três camadas principais: 

- A camada back-end:
No back end temos 3 classes de interface abstata: a 1° é o FIGURE CANVAS, que define e abrange a área na qual a figura será desenhada, a 2° o RENDERER para desenhar na tela a figura, e por ultimo o EVENTO que tem como função lidar com as entradas do usuário, como teclas e mouses.

- A camada artista: 
Que é onde acontece o trabalho pesado onde geralmente é o paradigma de programação ideal para se escrever um servidor de aplicativos
web, um app de interface do usuario ou algum script<br>

Vamo usar a cama artista  para gerar um gráfico: <br>


```
from matplotlib.backends.backend_agg import FigureCanvas as FigureCanvas   # import FigureCanvas
import matplotlib.figure import Figure   # import Figure Artist

fig = Figure()
canvas = FigureCanvas(fig)

import numpy as np
x = np.random.randn(1000)

ax = fig.add_subplot(111)

ax.hist(x,100)
ax.set_title('Titulo Qualquer')
fig.savefig('histogram.png')
```



- A camada de script:
Que é a camada voltada para o dia a dia e tem uma interface de script mais leve para deixar simples as tarefas do dia a dia, e 
também para uma geração rápida e fácil de gráficos.

Vamo usar a cama Script  para gerar um gráfico: <br>

```
import matplotlib.pyplot as plt
import numpy as np

x = np.random.randn(1000)
plt.hist(x,100)
plt.title('Titulo Qualquer')
plt.savefig('histogram.png)
plt.show()
```
<br>

Nesse repositorio irei focar na camada de script




