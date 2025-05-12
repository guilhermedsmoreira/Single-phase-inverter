## Inversor Monofásico com Carga Resistiva (Ponte H)

Como objeto de estudo, iremos utilizar um **inversor com chaveamento em ponte completa**, conhecido como **Ponte H**, que irá alimentar uma carga resistiva.

Todo o circuito apresentado abaixo foi construído no **LTspice**, e os resultados foram exportados para cá, a fim de verificarmos os resultados obtidos com a teoria explicada.

Para a construção desse circuito, foi utilizado 4 transistores do tipo MOSFETs, uma fonte de tensão contínua com valor eficaz de 5V e um resistor de 10kohm. Vale ressaltar que cada MOSFET apresenta sua própria fonte de pulso para que possam ser controlados. Essa técnica, conhecida como PWM, será detalhada mais adiante.

![Circuito Ponte H](circuito.png)

---

### Análise da Carga Resistiva

Sendo nossa carga **puramente resistiva**, como se pode ver no circuito montado acima, em teoria a **tensão eficaz** (RMS) na carga deve ser igual ao valor da **tensão contínua de entrada** da fonte CC, porém com forma de onda **quadrada**, devido à comutação dos inversores. Assim:

> **Vef_carga = Vef_fonte**

Ao simular nosso circuito, podemos confirmar a teoria apresentada.

![Forma de Onda](onda_saida.png)

Conforme imagem acima, nossa fonte de tensão está entregando ao sistema 5Vcc. Consequentemente, em nossa carga temos uma tensão com o mesmo valor eficaz de 5V porém quadrada.

Podemos notar um pequeno ruído ou deformação em nossa onda na carga, mas não se preocupe! Trata-se apenas dos inversores trabalhando (explicar melhor essa parte).

---

### Cálculo dos Harmônicos

Considerando o tipo de onda visto em nossa carga, podemos obter os valores de **tensão de pico** e **tensão eficaz** dos harmônicos dessa onda quadrada da seguinte forma:

{Vn,pico = (4 * Vcc) / (n * π), para n = 1, 3, 5, 7, ...}
{Vn,eficaz = (4 * Vcc) / (raiz(2)*n * π), para n = 1, 3, 5, 7, ...}

---

### Tensão de Saída do Inversor

Uma vez que o valor eficaz da tensão na saída do inversor será o mesmo valor da tensão eficaz da fonte, conforme visto acima, como podemos variar o valor eficaz da tensão de saída do inversor nesse caso?

Para isso, podemos utilizar a técnica conhecida como **PWM de pulso único**, que baseia-se em variarmos a forma de onda mantendo a tensão contínua de entrada em um valor constante.

(((Pulso único -> significado: 1 único pulso por semiciclo

> A forma de onda irá variar conforme o nosso **ângulo de condução** (Alfa), que assume valores `0 < Alfa < π/2`.

O valor de Alfa irá depender do resultado esperado no seu circuito. Quanto maior Alfa, **maior será a largura do pulso**, ou seja, **maior será o tempo que o sinal permanecerá em nível alto (ON)**.

Parei aqui. Alfa é basicamente Ton da fonte no LT. Adicione imagens disso.

⚠️ **Mas cuidado:** quanto maior o valor de Alfa, **maior será o número de harmônicos** na saída!

---

### Valor Eficaz para a Nova Forma de Onda

Considerando a nova forma de onda que agora utiliza a técnica de PWM de pulso único, o valor eficaz da tensão de saída pode ser encontrado pela seguinte fórmula:

{Vef = Vcc * sqrt(1 - (2 * α / π))}

---

### Cálculo dos Harmônicos para a Nova Forma de Onda

Para os valores de **tensão de pico** e **tensão eficaz** dos harmônicos da nova forma de onda presente na saída do inversor, temos:

{Vn_pico = (4 * E) / (n * π) * cos(n * β)}

{Vn_ef = (4 * E) / (√2 * n * π) * cos(n * β)}

Onde:

- `E` é a tensão de entrada (fonte contínua),
- `n` é o número do harmônico (somente ímpares: 1, 3, 5, ...),
- `β` é o ângulo de condução.

> ℹ️ **Observação:** Dependendo do valor de `β`, **alguns harmônicos podem ser cancelados**.  
> Além disso, ao aproximarmos `β` de seu valor máximo (`π/2`), a **tensão eficaz tende a zero** e a **THD (Total Harmonic Distortion)** tende ao **infinito**.
