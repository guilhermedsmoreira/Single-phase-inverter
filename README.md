## Inversor Monofásico com Carga Resistiva (Ponte H)

Para introdução ao assunto, iremos utilizar como base de estudo um **inversor com chaveamento em ponte completa**, conhecido como **Ponte H**, que irá alimentar uma carga resistiva.

Todo o circuito apresentado abaixo foi construído no **LTspice**, e os resultados foram exportados para cá, a fim de verificarmos os resultados obtidos com a teoria explicada.

![Circuito Ponte H](circuito.png)

---

### Análise da Carga Resistiva

Uma vez que nossa carga é **puramente resistiva**, como se pode ver no circuito montado acima, a **tensão eficaz** (RMS) na carga será igual ao valor da **tensão contínua de entrada** da fonte CC, porém com forma de onda **quadrada**, devido à comutação dos inversores:

> **V<sub>ef_carga</sub> = V<sub>ef_fonte</sub>**

---

### Forma de Onda da Tensão de Entrada e Saída

![Forma de Onda](onda_saida.png)

---

### Cálculo dos Harmônicos

Para os valores de **tensão de pico** e **tensão eficaz** dos harmônicos da onda quadrada presente na saída do inversor, temos:

<!-- Inserir fórmula aqui -->
```math
V_n = \frac{4V_{cc}}{n\pi}, \quad n = 1, 3, 5, 7, \dots

