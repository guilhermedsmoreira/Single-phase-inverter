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

---

### Tensão de Saída do Inversor

Uma vez que o valor eficaz da tensão na saída do inversor será o mesmo valor da tensão eficaz da fonte, conforme vimos acima, como podemos variar o valor eficaz da tensão de saída do inversor nesse caso?

Para isso, podemos utilizar a técnica conhecida como **PWM de pulso único**, que baseia-se em variarmos a forma de onda mantendo a tensão contínua de entrada em um valor constante.

> A forma de onda irá variar conforme o nosso **ângulo de condução** (β), que assume valores `0 < β < π/2`.

O valor de β irá depender do resultado esperado no seu circuito. Quanto maior β, **maior será a largura do pulso**, ou seja, **maior será o tempo que o sinal permanecerá em nível alto (ON)**.

⚠️ **Mas cuidado:** quanto maior o valor de β, **maior será o número de harmônicos** na saída!

---

### Valor Eficaz para a Nova Forma de Onda

Considerando a nova forma de onda que agora utiliza a técnica de PWM de pulso único, o valor eficaz da tensão de saída pode ser encontrado pela seguinte fórmula:

```math
V_{ef} = V_{cc} \cdot \sqrt{\frac{1 - \frac{2\alpha}{\pi}}}

### Cálculo dos Harmônicos para a Nova Forma de Onda

Para os valores de **tensão de pico** e **tensão eficaz** dos harmônicos da nova forma de onda presente na saída do inversor, temos:

$$
V_{n,\ pico} = \frac{4E}{n\pi} \cdot \cos(n\beta)
$$

$$
V_{n,\ ef} = \frac{4E}{\sqrt{2} \cdot n\pi} \cdot \cos(n\beta)
$$

Onde:

- `E` é a tensão de entrada (fonte contínua),
- `n` é o número do harmônico (somente ímpares: 1, 3, 5, ...),
- `β` é o ângulo de condução.

> ℹ️ **Observação:** Dependendo do valor de `β`, **alguns harmônicos podem ser cancelados**.  
> Além disso, ao aproximarmos `β` de seu valor máximo (`π/2`), a **tensão eficaz tende a zero** e a **THD (Total Harmonic Distortion)** tende ao **infinito**.



